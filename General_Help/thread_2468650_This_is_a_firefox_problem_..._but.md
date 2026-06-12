---
title: "This is a firefox problem ... but"
date: 2021-11-06
forum: General Help
---

### Post by Langstracht on 2021-11-06
I'm quite sure that the remedy is with someone on this forum.

I have long used crontab to open web pages in firefox with "commands" like the following:

```
30 06 * * *          export DISPLAY=:0 && firefox https://www.ted.com/

```

This either started firefox and opened the web page.  Or, if firefox was already running, opened a new tab with the web page.

Not so anymore.  With firefox 94.0, if firefox is already running the command results in the so helpful

> Firefox is already running, but is not responding. To use Firefox, you must first close the existing Firefox process, restart your device, or use a different profile.

I've played around with a variety of command line options and gotten nowhere.

Does anyone have any idea how to overcome this?

TIA

---

### Post by HermanAB on 2021-11-07
It is a new “security” feature.  Use a different browser.

---

