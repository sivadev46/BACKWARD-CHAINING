# BACKWARD CHAINING

## Experiment 2(d): Implementation of Backward Chaining

### Aim

To implement backward chaining using Python.

### Scenario

A medical expert system is designed to diagnose diseases based on patient symptoms. The system uses backward chaining to infer whether a patient has a specific disease by checking rules and known facts.

### Procedure

1. Define the knowledge base with rules (causal relationships).

   * Flu occurs if both cough and fever exist.
   * Fever occurs if sore throat exists.
2. Define known facts: {sore_throat, cough}.
3. Define the backward chaining function:

   * Check if the goal is in known facts. If so, return True.
   * Check if rules exist for the goal in the knowledge base.
   * For each rule, verify all conditions recursively using backward chaining.
   * If all conditions can be proven, return True.
   * Otherwise, return False.
4. Query whether the patient has flu.
5. Execute the backward chaining function and display the result.

### Python Program

```python
# Knowledge Base (Rules in IF-THEN format)

knowledge_base = {
    "flu": [["cough", "fever"]],
    "fever": [["sore_throat"]],
}

# Known facts

facts = {"sore_throat", "cough"}

# Backward chaining function

def backward_chaining(goal):

    if goal in facts:
        return True

    if goal in knowledge_base:
        for conditions in knowledge_base[goal]:

            if all(backward_chaining(cond) for cond in conditions):
                return True

    return False

# Query: Does the patient have flu?

query = "flu"

if backward_chaining(query):
    print(f"The patient is diagnosed with {query}.")
else:
    print(f"The patient does NOT have {query}.")
```

### Output

```text
The patient is diagnosed with flu.
```

### Result

Thus, the Backward Chaining algorithm was successfully implemented using Python to determine whether the patient has flu based on the given symptoms and knowledge base.
