# 🏥🤖 Applied AI in Healthcare: Prompt Engineering + Evaluation Example

This project demonstrates how large language model (LLM) prompting techniques can be applied within a healthcare analytics context.

The goal is to simulate a structured clinical data extraction workflow and demonstrate evaluation methodology.

---

# 🎯 Objective

Extract structured cardiovascular risk factors from an unstructured clinical note using prompt engineering techniques, then evaluate model output quality using a scoring framework.

---

# 📄 Example Clinical Note (Simulated)

Patient is a 54-year-old male with a history of hypertension and type 2 diabetes.  
BMI is 31.2. Total cholesterol is 240 mg/dL.  
Patient reports smoking one pack per day for 20 years.  
No documented history of prior myocardial infarction.

---

# 🧠 Prompt Design

## Initial Prompt

"Summarize this patient's cardiovascular risk factors."

### Problem:
- Output is inconsistent  
- Missing structured format  
- Risk of hallucinated data  

---

## Refined Prompt (Structured Extraction)

"You are a healthcare data analyst. Extract cardiovascular risk factors from the clinical note below.

Return output in JSON format with the following fields:
- age
- hypertension_status
- diabetes_status
- cholesterol_level
- BMI
- smoking_history
- prior_cardiac_events

If information is not present, return 'Not documented'.  
Do not infer information not explicitly stated."

---


# 📊 Expected Structured Output

```json
{
  "age": 54,
  "hypertension_status": "Yes",
  "diabetes_status": "Type 2",
  "cholesterol_level": "240 mg/dL",
  "BMI": 31.2,
  "smoking_history": "1 pack/day for 20 years",
  "prior_cardiac_events": "None documented"
} ```

---
📈 Output Evaluation Framework

To simulate AI evaluation, responses are scored across:
| Metric               | Description                     |
| -------------------- | ------------------------------- |
| Accuracy             | Correct data extraction         |
| Completeness         | All required fields returned    |
| Hallucination Risk   | No fabricated values            |
| Format Compliance    | Valid JSON structure            |
| Clinical Consistency | No contradictory interpretation |

Each dimension is scored 1–5.

🐍 Example Python Evaluation Logic (Conceptual)
```def evaluate_output(predicted, expected):
    score = 0
    
    for key in expected:
        if predicted.get(key) == expected.get(key):
            score += 1
    
    completeness = len(predicted.keys()) == len(expected.keys())
    
    return {
        "matching_fields": score,
        "completeness": completeness
    }```

This demonstrates:

Structured validation

Deterministic comparison

Framework-ready scoring

🔎 Failure Mode Analysis

Common AI errors in healthcare extraction:

Inferring diagnoses not stated

Converting units incorrectly

Misinterpreting negations

Adding fabricated medical history

Mitigation strategies:

Explicit constraint language

Structured output enforcement

Instruction reinforcement

Validation scripts

🎓 AI + Healthcare Competencies Demonstrated

Prompt lifecycle refinement

Structured data extraction logic

LLM evaluation framework design

Healthcare domain constraint awareness

Python-based validation modeling

This project bridges applied AI methodology with real-world healthcare data structure and evaluation principles.

