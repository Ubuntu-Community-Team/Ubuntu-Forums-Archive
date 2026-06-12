---
title: "html tables print with reversed fore-/background colors"
date: 2015-01-18
forum: General Help
---

### Post by rtimai on 2015-01-18
**HP DJ1000 prints web pages with fore/background colors reversed**
I haven't been able to locate any other user posts describing this symptom which probably first appeared several weeks ago. I only recently realized that it involved HTML pages with tabular data.

1- Pages with columnar data print with solid background color (or black.) Seems to be triggered by HTML pages displaying information in columns. Other HTML pages of straight text content print normally. Local applications (e.g. spreadsheets print normally.)

2- Print Preview always displays normally.

3- Occurs when printing from both Chromium (webkit) and Firefox (Mozilla) browsers (when testing each browser the other one is closed.)

4- I have examined in detail all the options in both web browsers and the printer driver, as well as Accessibility features (Universal Access in Ubuntu Linux) in the operating system (see below.) No Accessibility Features enabled, e.g., reverse color, high contrast, zoom, etc. A High-Contrast extension for Chromium has been uninstalled.

5- I have "deleted" the printer, turned off the printer, restarted, turned the printer back on, and reinstalled the driver twice. Test Print (as well as printing from any other local application) yields normal results. Symptoms only occur when printing columnar information in pages from either mozilla- or webkit-based web browsers.

6- On a typical problem page I alternately selected Print To File (PDF.) When viewed, the PDF displayed normally, but still printed with a solid background, and text/foreground colors reversed.

Because the symptoms occur independently of which web browser I'm printing from, and no Accessibility Features are enabled in either the browsers or the operating system, it seems to me that this may be a printer driver issue, and it may involve how it handles tables in HTML document printing. BUT columnar-formatted web pages printed to PDF display normally when viewed, yet ALSO print with fore/background colors reversed -- sorry, I am not providing an sample because it contains confidential information.

OS: Ubuntu 14.10
Hardware: HP Pavilion dv6-3012he 
Printer: HP Deskjet 1000
Printer Driver Description: HP-Deskjet-1000-J110-series
Chromium Version 39.0.2171.65 Ubuntu 14.10 (64-bit)
Firefox Version 35.0 Mozilla Firefox for Ubuntu - canonical 1.0

---

