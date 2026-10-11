# AI Voice Agent Assignment — Brief Test Results

**Platform:** Retell AI Conversation Flow Agent  
**Review basis:** The nine supplied call transcripts. Results below reflect transcript evidence only; they do not independently verify audio quality, stored variable values, or canvas transitions.

## Summary

| Status | Count |
|---|---:|
| PASS | 6 |
| PARTIAL | 3 |
| FAIL | 0 |
| **Total transcripts reviewed** | **9** |

## Scenario Results

### Test 1 — Perfect Eligible Customer
**Status: PASS**  
The customer provided the required eligibility information: residential property, joint ownership, original documents available, ₹65 lakh desired loan, self-employed, bank income, ₹75 lakh market value, and a 5-year tenure. The agent gave the preliminary eligibility result and senior-expert follow-up message.

### Test 2 — Agricultural Property
**Status: PASS**  
When the customer identified the property as agricultural, the agent immediately explained that the offer could not proceed and ended the call without continuing eligibility questions.

### Test 3 — Cash Income
**Status: PASS**  
The customer identified as self-employed and said income was received in cash. The agent immediately disqualified the customer and ended the call without asking further eligibility questions.

### Test 4 — Missing Original Documents
**Status: PARTIAL**  
The transcript indicates that only photocopies were available and the agent correctly disqualified the application. However, the transcript renders the respondent’s name as “Sandy” rather than the intended customer name, Sanjay. Because transcription may not accurately reflect the recorded audio or speaker wording, this is not treated as a confirmed identity-verification failure based on the transcript alone. Review the recording to confirm whether the respondent’s identity was properly verified before the offer was disclosed.

### Test 5 — Busy Customer / Callback
**Status: PARTIAL**  
A different person said Sanjay was busy. The agent did not disclose the loan offer and ended politely, which protected confidentiality. However, it asked the person to have Sanjay call back rather than capturing a preferred callback time or confirming a configured callback procedure.

### Test 6 — Out-of-Order Answers
**Status: PASS**  
The customer volunteered residential property, joint ownership, and an estimated market value together. The agent asked about original documents next rather than repeating ownership or market value. It then collected the remaining information and gave the preliminary eligibility handoff.

### Test 7 — Existing Loan
**Status: PASS**  
When the customer said they already had a loan against the property, the agent delivered the transfer-specialist message and ended the call without continuing the standard LAP assessment.

### Test 8 — EMI-Related / Existing-Loan Enquiry
**Status: PARTIAL**  
The agent routed the customer's existing-loan enquiry to the specialist message and ended the call. However, the transcript says the customer wanted to “release my existing loan”; it does not explicitly test a request to reduce an EMI. Run a separate test using a statement such as “I want to reduce my existing EMI.”

### Test 9 — Adversarial Property Correction
**Status: PASS**  
The customer first said the property was residential, then corrected the answer to agricultural. The agent followed the latest clear answer and immediately disqualified the customer.

## Issues to Fix

1. **Identity verification — verify against audio:** Test 4’s transcript may indicate a name mismatch, but the recording must be reviewed before concluding that verification failed. Confirm that the agent does not disclose the offer or proceed with qualification until the intended customer’s identity is established.
2. **Busy-customer callback:** Capture the preferred callback time when speaking with the intended customer, and only claim a callback is scheduled if the scheduling mechanism confirms it. For a third party, follow the configured unavailable-contact procedure.
3. **EMI reduction coverage:** Add a distinct test where the customer explicitly asks to reduce an existing EMI.
4. **Conversation repetition:** Review the duplicated new-LAP versus existing-loan question in the transcripts and improve clarification/transition handling where appropriate.

## Scenarios Not Yet Evidenced by These Transcripts

The supplied transcripts do not demonstrate both outcomes of the ₹75 lakh alternative (acceptance and refusal), or tenure boundary tests for below 3 years and above 15 years. Test these separately before marking the full assignment complete.

- **Loan amount above ₹75 lakh — accepts ₹75 lakh:** Expected to update `loan_amount` to `7500000` and resume qualification.
- **Loan amount above ₹75 lakh — refuses:** Expected immediate disqualification and call end.
- **Tenure = 2 years:** Expected immediate disqualification.
- **Tenure = 20 years:** Expected immediate disqualification.
- **Tenure = 3 and 15 years:** Expected to pass the tenure criterion.

## Conclusion

The transcripts show that the agent handles the main eligible, agricultural-property, cash-income, existing-loan, and out-of-order-answer scenarios. Test 4 requires audio review because the transcript alone does not conclusively establish an identity-verification failure. Callback handling and explicit EMI-reduction testing also need improvement. Do not report the assignment as fully validated until the outstanding scenarios above have been run and their actual outcomes recorded.
