# Synthetic customer profile (FinSight AI) - v2 with fraud labels
One customer, one current account, one debit card. Fully synthetic; no real person or bank data.
- Salaried employee at fictional "Nexora Solutions", living in Ariana, Tunis area; currency TND.
- Salary 3,200 TND/month (3,480 from Apr 2025), paid ~25th-28th; year-end bonuses Dec 2024/2025, performance bonus Jul 2025.
- Rent 720 TND (760 from 2025), utilities (Ooredoo, Tunisie Telecom, STEG bimonthly, SONEDE quarterly), subscriptions, health + car insurance.
- Adaptive savings standing order after payday; savings top-ups when the balance would run low.
- Seasonality: Ramadan-era groceries (Mar), Eid/summer cash and dining, Black Friday online spikes, December festive spend, gradual inflation.
- Trips: Hammamet (Jul 2024), Istanbul (Sep 2024), Djerba (Aug 2025), short Sousse trips. These are legitimate.
- Usual devices: DEV_A1 (phone, ~82% of online activity) and DEV_B2 (laptop). Usual country: TN.
- Planted anomalies (legitimate but unusual): 49 rows labelled in anomaly_ground_truth.csv.
- Planted fraud: 43 rows in 15 cases (2.5% of rows; real-world rates are far lower, raised here so models have enough positives). Labelled by is_fraud / fraud_type in both files and detailed in fraud_ground_truth.csv.
  Fraud types: account_takeover (6), atm_cash_out (6), authorized_push_payment_scam (2), card_testing (16), impossible_travel (6), night_high_value_online (3), recurring_unauthorized_subscription (4). Total fraudulent debits 6,697.674 TND. For every case except authorized_push_payment_scam the bank credits the amount back 10-21 days later (merchant 'Bank Dispute Reimbursement', is_fraud False, 14 rows); these are legitimate rows that post-date the fraud, so do not use them as detection features (leakage). The scam is not reimbursed.
  Suggested split: train on 2024, test on 2025 (fraud cases exist in both years).
- Totals: 1749 transactions (2024-01-01 to 2025-12-31), credits 114,765.224 TND, debits 115,118.884 TND, closing balance 3,286.590 TND, minimum balance 156.169 TND.
- Raw file: 1767 lines including 18 duplicates and 12 malformed rows; issues logged in data_quality_issues.csv.
