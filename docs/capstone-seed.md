# Capstone seed: Bank Statement Credit Analyst

> An AI analyst that reads company bank statements and flags risk signals for credit underwriters, with each finding linked to the transactions behind it.

## 1. What does it do?

It reads company bank statement PDFs, categorises each transaction, and flags risk signals for a credit underwriter, with each finding tied to the transactions behind it.

## 2. Who is it for?

A business credit analyst or underwriter reviewing an SME loan or overdraft application. They currently read months of statements by hand, categorising transactions and looking for red flags before they can write the credit memo.

## 3. What is the single most important question or task it must handle well first?

**"Does this business show stable, genuine trading income over the last three months?"**

This becomes the Session 1 `/ask` domain. Only a credit-risk capstone would ask it. It needs transaction categorisation (so trading revenue is separated from loans, transfers and owner injections) and structured, cited reasoning.

## 4. What would make you proud to demo on Demo Day?

Within three minutes, I upload a company's PDF statements and see:

- a categorised transaction table;
- a short underwriting summary covering revenue trend, debt repayments, overdraft use and bounced payments;
- every flag linked to the exact transactions behind it, so the underwriter can verify the finding rather than trust the model.

## Scope guardrails

- Two data sources: synthetic statements (two or three bank-style layouts) and a set of real business bank statements.
- Business-style accounts only, not consumer credit.
- One account, one currency, one fixed three-month window per review. No multi-account consolidation or currency conversion.
- Read-only analysis. The tool never makes or recommends a lending decision; it surfaces evidence for the underwriter, who decides.
- Every flag must cite the transactions behind it, or, for absence findings (e.g. "no trading receipts in month 3"), the period and categories checked. Unsupported findings are not shown.
- One demo path: upload PDFs, then categorised table, then cited summary. No user accounts, dashboards or export features.

## How it maps to the sessions

| Session | What it adds |
|---|---|
| 1. Reasoning | `/ask` on the trading-income question, with structured, categorised output |
| 2. RAG | Lending policy and category definitions |
| 3. Agents | Tools for totals, trends and anomaly checks |
| 4. TRACE evals | Accuracy against synthetic ground truth |
| 5. Memory | A client's earlier reviews |
