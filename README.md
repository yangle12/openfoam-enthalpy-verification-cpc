# Multi-region enthalpy conduction: verification materials

Versioned research materials for **Conservation and temperature consistency of interface-only and full-flux corrections in multi-region enthalpy conduction**, by Le Yang, Yinchuan University of Science and Technology, China.

This repository contains source code, selected case inputs, processed numerical results, independent references and audit records. It supports a comparative implementation-verification study; it is not an official OpenFOAM fix or a claim of upstream endorsement. A journal acceptance or publication is not implied by this release.

## Start here

Download `Supplementary_Reproducibility.zip` from the fixed release and extract it into a new directory. The paths below refer to that extracted package. The release attachment contains the full code and data; the repository landing files record its documentation, licenses and manifest.

- `materials/extension_20261027/README.md`: portable native replay and extended 1D/2D checks.
- `materials/extension_20261027/PROTOCOL.md`: iteration criteria and the declared case matrix.
- `materials/extension_20261027/summary.json`: extension results, including failed attempts and reference-tolerance controls.
- `materials/previous_20261022/reproducibility/convergence/README.md`: converged secant comparison and four internal/interface-flux combinations.
- `materials/previous_20261022/data/`: processed earlier comparison results.
- `RELEASE_MANIFEST.sha256.json`: file hashes for the distributed materials.

The dated material directories retain the evidence snapshots used in the manuscript. Their old preparation-status notes may refer to NHT Part B, a private backup or pending deposition; those notes describe their creation history and are not the current journal or repository status. Historical source and inputs are not rewritten to remove that provenance. This top-level README governs the current release description.

## Tested portable replay

Use Linux with **OpenCFD OpenFOAM v2412**, development headers/libraries, `wmake`, Python 3, NumPy and SciPy. A Foundation release is not interchangeable by version number.

```bash
cd materials/extension_20261027
python3 scripts/replay.py prepare --package . --case pilot_2d_fourier --output /tmp/enthalpy-replay
source /path/to/OpenFOAM-v2412/etc/bashrc
bash /tmp/enthalpy-replay/build_run.sh
python3 scripts/replay.py audit --output /tmp/enthalpy-replay
```

The output directory must be new. The portable helper was independently compiled, run and audited in the recorded study; this release preserves the tested scientific source bytes. Original orchestration and document-generation scripts retain historical workstation paths and are not the portable entry point.

For the independent reference self-check:

```bash
python3 scripts/reference.py --check --out /tmp/enthalpy-reference-checks.json
```

## Scientific scope and attribution

The direct secant comparison is one-dimensional. The full-Fourier extension covers stationary orthogonal 1D/2D solids, constant density and isotropic constant conductivity, five synthetic heat-capacity laws and seven time steps. No liquid convection, general nonorthogonal mesh treatment, parallel verification, contact resistance, universal convergence or production-ready repair is claimed.

The interface diagnosis and secant-heat-capacity proposal are attributed to S. Takehara's OpenCFD issue #2740 (2023): https://gitlab.com/openfoam/core/openfoam/-/work_items/2740 . Established conservative enthalpy methods are credited in the manuscript. The work does not claim first discovery. Small same-grid reference differences measure implementation agreement, not continuum or experimental accuracy.

The 27 native extension attempts include 22 accepted and five failed original-flux controls. Failures and reference-tolerance exceptions remain in the materials. Both new native research executables use changed iteration controls; these are not all pristine official binaries.

## Included and retained evidence

The compact release contains the materials listed above. Large full-field histories, complete execution logs and binary archives are retained by the author and can be supplied upon reasonable request. Their identities and hashes are recorded in the materials; they are not claimed to be included in this compact repository. No DOI has been assigned. Cite the fixed release/tag, not a moving default branch.

Two third-party reproduction archives attached to issue #2740 are not redistributed because a separate redistribution license was not established. Their original retrieval record and checksums remain in `materials/previous_20261022/reproducibility/direct_comparison/prior_art/` and `OMITTED_THIRD_PARTY.json`. Obtain those attachments from the upstream issue. They are not required to replay this study's newly generated cases. The historical manifest describes the original private snapshot; the top-level release manifest describes the files actually distributed here.

## AI assistance

OpenAI Codex (GPT-6-based assistant, OpenAI) assisted with verification planning, code development and debugging, computational workflows, data processing, diagnostic interpretation, plotting code and manuscript drafting/revision. Plots and numerical claims derive from the archived computations. AI is not an author, and automated checks are not independent human peer review. Le Yang is responsible for the work.

## Licenses

Existing OpenFOAM copyright and GPL notices remain intact. Code contributed by Le Yang is distributed under GPL-3.0-or-later; author-produced numerical data and documentation are distributed under CC-BY-4.0. Third-party material retains its own notices and is not relicensed. See `LICENSE.md` and `LICENSES/` for scope and full license texts.
