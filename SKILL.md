---
name: exam-grader
description: Grade essay-based exams that reference case studies. Use when grading student submissions against a rubric with point allocations and marking bands. Evaluates demonstrated understanding, awards partial credit, and provides brief feedback per question.
---

# Exam Grader

A skill for grading essay-based examinations where students respond to questions about a case study. Grades against a rubric, awards partial credit for demonstrated understanding, and provides concise feedback.

## When to Use This Skill

**Trigger conditions:**
- User mentions grading exams, marking submissions, or evaluating student work
- User provides a case study, rubric, and student submission
- User wants consistent, rubric-aligned marking with brief feedback

## Required Inputs

Before grading, ensure all four inputs are available:

| Input | Description | Format |
|-------|-------------|--------|
| **Case Study** | The scenario students analysed | Document or text |
| **Questions** | The exam questions posed | List with point allocations |
| **Rubric** | Marking criteria with bands and descriptors | Table or structured text |
| **Student Submission** | The answers to be graded | Document or text |

If any input is missing, ask for it before proceeding.

## Grading Workflow

### Step 1: Parse the Rubric

Extract from the rubric:
- **Point allocations** per question (e.g., Q1: 25 marks)
- **Marking bands** with descriptors (e.g., "Excellent: 21-25", "Good: 16-20", etc.)
- **Key criteria** that must be addressed for each band

Create an internal reference structure:

```
Question 1 (25 marks)
├── Excellent (21-25): [criteria]
├── Good (16-20): [criteria]
├── Satisfactory (11-15): [criteria]
├── Weak (6-10): [criteria]
└── Poor (0-5): [criteria]
```

### Step 2: Identify Case Facts

Before evaluating answers, extract key facts from the case study:
- Central problem or scenario
- Relevant data, figures, or context
- Stakeholders and their positions
- Constraints or conditions mentioned

This ensures answers are evaluated against *this specific case*, not generic knowledge.

### Step 3: Grade Each Question

For each question, evaluate the student's answer by:

1. **Check case application**
   - Does the answer reference specific facts from the case?
   - Are concepts applied to the case context (not just stated abstractly)?
   - Are case details used accurately?

2. **Check rubric criteria**
   - Which band descriptors does the answer satisfy?
   - What criteria are met, partially met, or missing?

3. **Assess demonstrated understanding**
   - Even if the final conclusion is imperfect, does the student show they understand the underlying concepts?
   - Is there evidence of analytical thinking?
   - Award partial credit where understanding is evident

4. **Assign a mark**
   - Place the answer in the appropriate band
   - Position within the band based on strength of evidence
   - Document the rationale briefly

### Step 4: Write Feedback

For each question, write **brief feedback** (2-4 sentences) that:
- Acknowledges what was done well
- Identifies the main gap or improvement area
- Is specific to this answer (not generic advice)

**Feedback tone:**
- Constructive, not punitive
- Direct and clear
- References case or rubric where relevant

**Example feedback:**
> "Good identification of the key risk factors from the case. The analysis would benefit from quantifying the potential impact using the figures provided in Exhibit 2. Consider how the stakeholder constraints limit the available mitigation options."

### Step 5: Compile Results

Output the grading in this format:

---

## Grading Summary

**Student:** [Name/ID if provided]  
**Total:** [X] / [Total Available Marks]

### Question 1: [Question Title] — [X] / [Y] marks

**Band:** [e.g., Good]

**Feedback:** [2-4 sentences]

---

*(Repeat for each question)*

---

### Overall Comments

[1-2 sentences on general strengths and areas for development across the submission]

---

## Partial Credit Guidelines

Award partial credit when the student demonstrates understanding even if execution is flawed:

| Situation | Credit Approach |
|-----------|-----------------|
| Correct concept, wrong application to case | Award for conceptual understanding, note application gap |
| Incomplete analysis but correct direction | Award proportionally to depth achieved |
| Minor errors in otherwise sound reasoning | Small deduction, acknowledge the reasoning |
| Generic answer without case reference | Cap at lower band regardless of conceptual accuracy |
| Misreads case facts but analyses logically | Partial credit for method, note the misreading |

**Principle:** If you can see they understand the concept, give credit for that understanding, then note what's missing.

## Consistency Checks

After grading all questions:

1. **Internal consistency** — Would similar quality answers in different questions receive similar band placements?
2. **Rubric alignment** — Does each mark awarded map clearly to rubric criteria?
3. **Case dependency** — Have answers that ignore the case been appropriately capped?

If inconsistencies are found, adjust and note the adjustment.

## Edge Cases

**Student references material outside the case:**
- If relevant and adds value: acknowledge but don't require it
- If it substitutes for case analysis: note the gap

**Answer is very short:**
- Grade what's there; brevity isn't penalised if content is strong
- If too thin to demonstrate understanding, mark accordingly

**Answer misunderstands the question:**
- Grade against what was asked
- In feedback, clarify the misunderstanding

**Rubric criteria conflict:**
- Use professional judgement
- Note the tension in your rationale

## Output Files

When grading is complete, offer to export:

1. **Summary table** — Question-by-question marks in a simple table
2. **Full feedback document** — Complete grading with all feedback
3. **Marks only** — Just the numbers for upload to a grading system

## Tips for Effective Grading

- Read the full answer before starting to mark
- Don't let early impressions anchor the grade—reassess against rubric
- Use the case as the anchor: "Did they use *this* case?"
- Keep feedback actionable: what should they do differently next time?
- When in doubt between bands, consider demonstrated understanding

## Batch Grading

If grading multiple submissions:

1. Grade all submissions for Q1 before moving to Q2 (improves consistency)
2. After every 3-5 submissions, spot-check for drift
3. Keep a brief note of common errors to mention in general feedback
4. Flag any submissions that need second review

---

## Quick Reference

**Inputs needed:** Case study, questions, rubric, student submission

**Process:** Parse rubric → Extract case facts → Grade each question (case + rubric + understanding) → Brief feedback → Compile

**Output:** Mark per question + band + 2-4 sentence feedback + total

**Partial credit:** Yes, for demonstrated understanding even if execution is imperfect

**Feedback style:** Brief, specific, constructive
