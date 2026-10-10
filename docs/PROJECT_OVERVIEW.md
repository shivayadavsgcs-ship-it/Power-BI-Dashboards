# Project Overview and Audit Notes

## Repository purpose

This repository is a portfolio of Microsoft Power BI dashboard projects. The primary artifacts are Power BI Desktop `.pbix` files, with a root `README.md` describing selected dashboards. This is an analytics/reporting portfolio, not a conventional software application.

## Confirmed project inventory

The following artifacts were identified from the README and commit file metadata:

| Dashboard / artifact | File | Current documentation status |
|---|---|---|
| IPL 2025 Data Analytics | `2025 IPL DATA Dashboard.pbix` | Described in the README |
| Swiggy Food Delivery Performance | `Swiggy Report.pbix` | Described in the README |
| Food Item Dashboard | `𝐅𝐨𝐨𝐝 𝐈𝐭𝐞𝐦 𝐃𝐚𝐬𝐡𝐛𝐨𝐚𝐫𝐝.pbix` | Needs its own README section; filename uses Unicode bold characters |
| BSS Loan Report | `BSS Loan Report.pbix` | Needs its own README section; privacy review is a priority |
| Portfolio documentation | `README.md` | Documents two dashboards in a single long page |

This inventory is based on the available README and selected commit metadata; it is not a binary-level inspection of every Power BI file.

## Documented dashboards

### IPL 2025 Data Analytics

The README describes bowling efficiency, wickets, dot balls, boundaries, scoring contribution, dismissal types, team comparisons, venue mapping, and date/team slicers. Reported headline values include 26K+ runs conceded, 2.74K overs, 873 wickets, and 5K dot balls. These are README-reported figures and have not been independently recalculated from the model.

### Swiggy Food Delivery Performance

The README describes revenue, order count, average rating, average order value, delivery-speed analysis, food-category performance, payment-method mix, and delivery-location mapping around Hyderabad/Secunderabad. Reported headline values are ₹26.64K revenue, 26 orders, 3.88/5 average rating, and ₹1,025 AOV. These figures have not been independently recalculated from the model.

### Food Item Dashboard

A PBIX artifact is present in commit metadata, but the current README does not describe its purpose, data source, key metrics, or interaction model. Add a concise section after verifying the report directly.

### BSS Loan Report

A PBIX artifact is present. The associated commit description says the dashboard concerns loans issued through two local charities and includes member names, loan amounts, interest, payments, and outstanding balances. These fields may be sensitive personal/financial data. Review the report and any embedded or separately stored source data for authorization, consent, data minimization, and public-sharing suitability before promoting or continuing to publish it. Prefer anonymized or synthetic sample data for a public portfolio. Do not assume permission to use data for analysis also implies permission to publish identifiable records.

## Architecture and technology

- Primary authoring/runtime tool: Microsoft Power BI Desktop.
- Primary deliverables: binary `.pbix` report files.
- Documented analytics techniques: DAX measures, aggregations/ratios, KPI cards, charts, maps, treemaps, and slicers.
- Conventional source-code build/test configuration was not identified in the available review. Power BI reports require validation inside Power BI Desktop; their correctness cannot be inferred from filenames or README descriptions alone.
- No issue or pull-request activity was returned by the connected GitHub searches at the time of this review.

## Risks and quality gaps

1. **Privacy and publication risk — high priority:** Review the BSS loan report for identifiable names and sensitive financial details before making the repository public or sharing screenshots/data extracts.
2. **Documentation coverage:** Four PBIX artifacts are identifiable, but the README documents only two. Add a section for every report with purpose, data provenance, KPI definitions, filters, and screenshots where safe.
3. **Metric definitions and reconciliation:** Define each KPI precisely (including denominator, time window, currency, blanks, and duplicate handling). Check that totals and averages reconcile with the underlying model. In particular, document the AOV definition and ensure cricket measures distinguish innings/overs/balls correctly.
4. **Reproducibility:** For each report, document the data source, refresh steps, required credentials/gateways (without secrets), expected schema, and any manual preparation.
5. **Binary review limits:** GitHub commit metadata identifies PBIX filenames but does not expose their internal model, DAX, relationships, Power Query transformations, or visual accessibility. A full semantic/model audit requires opening the reports in Power BI Desktop or exporting supported model metadata.
6. **Filename consistency:** The Food Item Dashboard filename contains Unicode mathematical bold letters. Consider a simple ASCII filename for easier linking and cross-platform scripting, but rename only after checking for existing links and coordinating the change.
7. **Portfolio usability:** The root README combines two projects in one document. Add a dashboard index and consistent sections for all reports; include sanitized preview images and direct links where practical.
8. **Validation and accessibility:** Check slicer interactions, filter context, blank/zero behavior, date tables, map privacy implications, contrast, alt text, and keyboard/screen-reader usability.

## Recommended order of work

### P0 — Protect sensitive data
- Open the BSS Loan Report and review all report pages, source tables, and any drill-through/tooltips for names, account identifiers, loan balances, or other personal information.
- Confirm authorization for public distribution. If uncertain, replace identifiable data with anonymized or synthetic data before publication.

### P1 — Make the portfolio complete
- Add Food Item and BSS Loan Report descriptions to the README only after validating their contents and safe-to-share status.
- Create a consistent project index with a one-sentence purpose, key questions, headline metrics, data source/date, and link to each PBIX.
- Replace broad claims such as “end-to-end” with specific, verifiable descriptions of data preparation, modeling, and analysis.

### P2 — Validate analytical correctness
- Record KPI definitions and DAX measures for every report.
- Reconcile headline values against source data and document filters/date scope.
- Test slicer combinations, totals, missing data, and outlier behavior in Power BI Desktop.

### P3 — Improve maintainability and presentation
- Add sanitized screenshots, a data dictionary, refresh instructions, and a short methodology section.
- Use consistent, ASCII-friendly filenames for future additions.
- Keep source datasets and secrets out of the repository unless there is a clear, safe reason to publish them.

## Review boundaries

This review inspected the root README and selected commit metadata, plus repository issue/PR searches. The GitHub code-search integration did not return file-search results for the attempted binary-extension queries, and PBIX binary internals were not parsed. Therefore, this document separates confirmed repository metadata from README-reported metrics and audit recommendations. No dashboard measure has been independently tested.

## Working conventions for future changes

- Prefer small, reviewable changes on a feature/documentation branch rather than editing `main` directly.
- Never delete or replace PBIX files, source datasets, or repository settings without explicit approval.
- Before changing a report or its data, describe the intended outcome and validate it in Power BI Desktop.
- Do not commit credentials, personal financial data, or raw customer/member records.
- Update this document whenever the project inventory, data sources, measures, or publication status changes.
