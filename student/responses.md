# Week 07 Controls Lab — Responses

Answers and recorded model results from `submission.json`. This document does not recompute or independently validate the results.

## Submission status

- Schema: week07.submission/v1

- Record ID: eb657096-660f-4429-90ca-630277912623

- Record revision: 144

- Model hash: fnv1a-adee3cf8

- Readiness: Marked incomplete or not ready; missing: prediction, verification, claim, reflection, aiUse, execution

## Supplied setup (instructor supplied)

### question — instructor supplied
Calculate required control moment, elevator moment, and the change with airspeed. Explain whether the nominal response meets +0.12 rad/s².

### system — instructor supplied
Illustrative planar pitch model. Aircraft geometry, integration, force conversion and constraints are supplied.

### representation — instructor supplied
Body axes forward/right/down. Positive pitch moment nose-up. Positive Fz downward. Positive elevator trailing edge down. Reference/CG X=0 m; tail X=-3 m.

### inputs — instructor supplied
Iy=5000 kg·m²; target=+0.12 rad/s²; competing=-750 N-m; density=1.225 kg/m³; V=40 m/s; S=16 m²; chord=1.5 m; Cmδ=-0.8/rad; elevator=-5°. Inputs are illustrative, not calibrated.

## Student responses

### physics
**Prompt:** Explain why a downward force aft of the CG gives a positive nose-up moment.

**Student response:**
```
Using M = r × F: the tail sits aft of the CG (negative x), and the elevator force points downward (positive Fz). That cross product gives a positive moment noseup, per the stated convention.
```

### assumptions
**Prompt:** Explain one supplied assumption and what could invalidate it: planar motion, fixed reference, local linear effectiveness, no trim or damping.

**Student response:**
```
Planar motion assumes the aircraft only pitches in a single vertical plane, with no roll, yaw, or sideslip coupling. This would be invalidated by any asymmetric input or disturbance — such as a gust, aileron deflection, or engine-out condition — that introduces motion or forces outside that plane.
```

### model
**Prompt:** Write your demand, dynamic-pressure, coefficient and moment equations. Identify which quantities are supplied and which are unknown.

**Student response:**
```
Demand The target angular acceleration is 0.12 rad/s². Using Newton's second law for rotation, the required net moment is Iy × α = 5000 × 0.12 = 600 N·m. Dynamic pressure q∞ = ½ρV² = ½ × 1.225 × 40² = 980 Pa
Coefficient increment Convert −5° to radians: −5 × π/180 = −0.0873 rad
ΔCm = Cmδ × δe = (−0.8) × (−0.0873) = 0.0698
Elevator moment: M_elevator = ΔCm × q∞ × S × c = 0.0698 × 980 × 16 × 1.5 = 1642 N·m
Net moment (elevator plus the competing moment):
ΣMy = 1642 + (−750) = 892 N·m
```

### prediction
**Prompt:** Before running your own implementation, predict the sign of its elevator moment and the effect of halving airspeed. Explain the competing moment.

**Student response:**
_Missing — no response supplied._

### verification
**Prompt:** Show one independent hand calculation with units. Compare it with your model, and explain a sign, unit, or limiting-case check.

**Student response:**
_Missing — no response supplied._

### claim
**Prompt:** What do your computed results support at the stated condition? Include a limitation.

**Student response:**
_Missing — no response supplied._

### reflection
**Prompt:** What additional evidence or missing physics would you investigate next?

**Student response:**
_Missing — no response supplied._

### AI use
**Prompt:** Identify the AI tool and how you used it, what you changed, and how you independently checked the result. State “No AI used” if applicable.

**Student response:**
_Missing — no response supplied._

## Equations and model source

The recorded model JSON/expression source follows exactly as supplied. It is not interpreted or recomputed here.

```
{
  "schemaVersion": "week07.student-model/v1",
  "id": "week07-student-model",
  "version": "1.0.0",
  "slots": [
    {
      "id": "controls.demand",
      "expressions": [
        {
          "name": "requiredMoment",
          "expression": "",
          "unit": "N*m"
        }
      ]
    },
    {
      "id": "controls.effectiveness",
      "expressions": [
        {
          "name": "dynamicPressure",
          "expression": "",
          "unit": "Pa"
        },
        {
          "name": "deltaCm",
          "expression": "",
          "unit": "1"
        },
        {
          "name": "deltaMoment",
          "expression": "",
          "unit": "N*m"
        }
      ]
    }
  ]
}
```

## Recorded verification status

No verification record was supplied.

## Recorded model runs

_Missing — no model runs supplied._

## Submission instructions

Use Save to GitHub in the app to save both files, commit, and push. Submit your fork URL and the saved commit SHA. Manual fallback: save this file beside `student/submission.json`, run `npm run student:prepare` and `npm run student:validate`, then commit and push student/.
