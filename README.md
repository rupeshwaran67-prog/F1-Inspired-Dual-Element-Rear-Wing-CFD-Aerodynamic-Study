# F1-Inspired-Dual-Element-Rear-Wing-CFD-Aerodynamic-Study
CFD analysis of a Williams-inspired (mid-2000s, pre-DRS era) dual-element Formula 1 rear wing with endplates, modelled at full 1:1 scale in ANSYS Fluent to evaluate downforce and drag characteristics under high-speed circuit conditions.

## Overview

This project investigates the aerodynamic performance of a high-downforce F1 rear wing configuration using steady-state RANS CFD. The geometry — a dual-element wing with endplates — was built and meshed for external flow analysis around a full vehicle-relevant domain, with a ground-effect boundary condition included to capture realistic on-track flow behaviour.

## Methodology

- **Geometry & Domain**: Dual-element rear wing with endplates, modelled at 1:1 scale in ANSYS DesignModeler. Computational domain sized at approximately 3000 mm streamwise to allow full wake development downstream of the wing.
- **Boundary Conditions**: Velocity inlet, pressure outlet, moving/stationary ground plane (`ground`, `twall`), and no-slip wall conditions (`wall`, `wall-solid`) to represent realistic track-level aerodynamics.
- **Mesh**: Triangulated surface mesh generated in ANSYS Meshing (CFD-focused physics preference, Fluent solver). Global element size was constrained by the ANSYS Student license cell-count limit (512,000 cells), which set an effective floor on mesh resolution across the full external domain.
- **Solver**: ANSYS Fluent, 3D, double precision, parallel (4 processes). Pseudo-transient solution with SST k-omega turbulence modelling.
- **Convergence**: Residuals (continuity, x/y/z-velocity, k, omega) converged to between 1e-03 and 1e-06 within approximately 300 iterations.

## Results

- **Pressure Field**: Contour plots show a strong low-pressure region forming beneath and around the wing elements, consistent with downforce generation, alongside a high-pressure region upstream and above the wing.
- **Streamlines & Wake Structure**: Velocity streamlines reveal flow acceleration over the suction side of both wing elements and vortex structures shedding from the endplates into the wake — typical of a high-downforce, pre-DRS-era wing configuration.
- **Flow Behaviour**: The combination of pressure contours and streamline data was used to qualitatively assess downforce/drag trade-offs and identify drag-producing wake structures behind the wing.

## Tools Used

ANSYS Fluent (CFD solver), ANSYS CFD-Post (post-processing and visualisation), ANSYS DesignModeler / Meshing (geometry and mesh generation)

## Validation Context

This study has not been independently validated against new wind tunnel testing or proprietary track data. To sanity-check the qualitative behaviour observed, results were compared against trends reported in published CFD and wind-tunnel studies of similar dual-element rear wing configurations:

- Mohammed et al. (2017), *Study on Airflow Characteristics of Rear Wing of F1 Car* — CFD study of a dual-element rear wing module reporting pressure distributions, lift/drag coefficients, and the effect of element gap (DRS open/closed) on flow behaviour.
- Soso & Wilson, *CFD Analysis of Dual Element Rear Wing of an F1 Car* — k-ε turbulence model study of front/rear wing aerodynamics, reporting the influence of ground effect and angle of attack on lift and drag coefficients, including identification of stall onset.
- F1technical.net rear wing CFD analysis — reports endplate vortex production and downwash effects between wing elements, and biplane interference effects between closely spaced elements.
- MSc thesis comparing wind-tunnel and Star-CCM+ CFD results for front/rear formula car wings, finding downforce predictions within approximately 10% of wind-tunnel measurement, but drag predictions showing greater than 10% error — a useful indicator of which CFD outputs are more reliable for this class of geometry.

The low-pressure region observed beneath the wing elements and the vortex/wake structures shed from the endplates in this study are qualitatively consistent with the flow phenomena reported in the sources above. Absolute pressure and force values from this study are not directly comparable to these references, as geometry, scale, Reynolds number, and domain setup all differ — the comparison is intended to sanity-check flow behaviour, not to claim quantitative agreement.

## Limitations & Honest Notes

- This is a steady-state RANS study run on an ANSYS Student license, which caps the mesh at 512,000 cells. This sets a hard floor on achievable mesh resolution across the full external domain, particularly in regions like the wing leading/trailing edges and wake where finer resolution would normally be used. Local face/edge sizing was not used to concentrate resolution in these regions within the available cell budget — a logical next step on a full license, or even within the student cap, would be targeted local refinement rather than a uniform global size.
- y+ near the wing surface was not formally checked or reported, so boundary layer resolution is not verified.
- The study has not been validated against wind tunnel or track data; absolute pressure and force values should be treated as indicative rather than definitive.
- The geometry is a representative dual-element wing inspired by mid-2000s F1 aerodynamics, not a reverse-engineered or CAD-accurate replica of any specific team's part.

## Images

All images are stored in the `images/` folder of this repository.

### Setup

**Geometry & Domain**
![Geometry and domain setup](images/01_geometry_domain_setup.png)

**Mesh — Full Domain View**
![Mesh full domain](images/02_mesh_full_domain.png)

**Mesh — Element Sizing**
![Mesh element sizing](images/03_mesh_element_sizing.png)

**Boundary Conditions — Inlet Setup**
![Boundary conditions inlet](images/04_boundary_conditions_inlet.png)

**Boundary Conditions — Domain View**
![Boundary conditions domain](images/05_boundary_conditions_domain.png)

### Solution

**Residual Convergence**
![Residual convergence](images/06_residuals_convergence.png)

### Post-Processing

**Pressure Contour — View 1**
![Pressure contour view 1](images/07_pressure_contour_view1.png)

**Pressure Contour — View 2**
![Pressure contour view 2](images/08_pressure_contour_view2.png)

**Velocity Streamlines — View 1**
![Velocity streamlines view 1](images/09_velocity_streamlines_view1.png)

**Velocity Streamlines — View 2**
![Velocity streamlines view 2](images/10_velocity_streamlines_view2.png)

**Velocity Streamlines — View 3**
![Velocity streamlines view 3](images/11_velocity_streamlines_view3.png)

---
*Part of an ongoing portfolio of FEA/CFD and CAD projects — see other repositories for Formula Student structural analysis, EV powertrain simulation, and crashworthiness studies.*
