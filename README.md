# Student Portal Risk Dashboard

**Live demo:** https://yatinannam.github.io/srmp-risk-dashboard/

An interactive dashboard for the case study *Information Security Risk Assessment and Audit of a College Student Portal*, prepared for Security Risk Management Principles (21CSC308T) at SRM Institute of Science and Technology.

**Author:** Yatin Annam · RA2411030010101 · Section X1

> **Hypothetical case study.** All risks, scores and actions are illustrative examples for a generic college portal. No real SRM system was accessed, tested or assessed.

## The case study

A college student portal holds student profiles, marks, attendance, login credentials, fee details, backups and audit logs. A single weakness could lead to unauthorized access, exposed personal data, changed academic records or downtime.

The study walks through the four syllabus units:

1. **Introduction to risk:** assets, threats, vulnerabilities, impact, risk and the CIA triad.
2. **Data collection and planning:** scope, sponsor, assessment team, evidence collection and asset inventory.
3. **Data analysis:** threat and vulnerability pairs, scored with a 5 × 5 likelihood × impact matrix.
4. **Information security audit:** audit lifecycle, evidence types, control types and follow-up.

### Sample risk register

| ID | Scenario | Likelihood × Impact | Rating | Target residual |
|---|---|---|---|---|
| R1 | Phished administrator credentials | 4 × 4 = 16 | Critical | 2 × 4 = 8 (Medium) |
| R2 | Unauthorized access to another student's marks | 3 × 5 = 15 | High | 1 × 5 = 5 (Medium) |
| R3 | Unpatched portal component exploited | 3 × 4 = 12 | High | 1 × 4 = 4 (Low) |
| R4 | Production account accesses backups | 2 × 5 = 10 | High | 1 × 3 = 3 (Low) |
| R5 | Insufficient logging to investigate misuse | 3 × 3 = 9 | Medium | 2 × 3 = 6 (Medium) |

Score bands: Low 1–4, Medium 5–9, High 10–15, Critical 16–25.

## Using the dashboard

- **Play demo:** walks through the audit follow-up automatically. Actions move to Verified one by one, risks drop to their residual scores on the heat map, and the exposure trend falls. Click again to stop.
- **Heat map:** switch between **Inherent** (before treatment) and **Residual** (after verified treatment). Click a cell to filter the register. In the inherent view, drag a risk chip to another cell to re-score it.
- **KPI tiles and legend:** click Critical or High (or a legend chip) to filter the register by rating.
- **Risk exposure trend:** total inherent vs residual score over the session. Hover for the change behind each point.
- **Risk register:** change likelihood or impact and every score, rating and count updates live. Pick a treatment option (Mitigate, Transfer, Avoid, Accept, after ISO/IEC 27005). Search, edit or remove risks; removing a risk also removes its linked actions.
- **Add risk:** set inherent likelihood and impact, a treatment option, a target residual score and an optional first remediation action.
- **Remediation tracker:** add or remove actions, filter by status and move actions through Not started, In progress, Done and Verified. A risk counts as treated, and its residual score applies, only when all its linked actions are verified. Hover a register row to highlight its actions.
- **Audit phase bar:** step through the five audit phases.
- **Activity log:** every change is timestamped as an audit trail.
- **Undo:** the Undo button or Ctrl+Z reverts the last change.
- **Export CSV / Print report:** download the register or print the whole dashboard.
- **Theme:** cycle Auto, Light and Dark.
- **Reset demo data:** click twice to restore the original sample data (this can also be undone).

Changes are saved in the browser and stay in sync across open tabs, so a presenter tab and a projector tab show the same state.

Keyboard: `/` jumps to search, `Esc` closes a form or clears filters, `Ctrl+Z` undoes.

To run it locally, open `index.html` in a browser, or run `python -m http.server 8000` in this folder and visit http://localhost:8000/.

## Tools for this scenario

| Tool | Use in this case study | Related risk |
|---|---|---|
| **Nmap** | Discover hosts, open ports and services to build the asset inventory | Scoping |
| **Wireshark** | Inspect traffic to confirm logins and marks travel encrypted | Confidentiality |
| **OWASP ZAP** | Test the web app, e.g. whether one student can view another's marks | R2 |
| **OpenVAS (Greenbone)** | Scan for missing patches and known vulnerabilities | R3 |
| **Wazuh** | Centralize logs and alert on administrator activity | R5 |

> **Use these tools only on systems you own or have written permission to test**, such as a personal lab or an intentionally vulnerable app like OWASP Juice Shop. Never scan a real college portal without authorization.

## References

1. NIST SP 800-30 Rev. 1, *Guide for Conducting Risk Assessments* (2012). https://csrc.nist.gov/pubs/sp/800/30/r1/final
2. ISO/IEC 27001:2022, *Information security management systems*. https://www.iso.org/standard/27001.html
3. ISO/IEC 27005:2022, *Information security risk management*. https://www.iso.org/standard/80585.html
4. NIST SP 800-53 Rev. 5, *Security and Privacy Controls* (2020). https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final
5. OWASP Top 10:2025. https://owasp.org/www-project-top-ten/
