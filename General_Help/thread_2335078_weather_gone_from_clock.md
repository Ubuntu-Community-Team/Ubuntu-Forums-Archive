---
title: "weather gone from clock"
date: 2016-08-25
forum: General Help
---

### Post by Timothy Taylor on 2016-08-25
At some time over the past week or so, the weather indicator has vanished from the calendar / clock in the panel.

World locations and times seem to work OK, but there's no weather information.

???

---

### Post by Thomas_Price on 2016-08-26
> **Timothy Taylor said:**
> At some time over the past week or so, the weather indicator has vanished from the calendar / clock in the panel.

World locations and times seem to work OK, but there's no weather information.

???

I've got the same issue, and also with the standalone applet.  I'm guessing the source API changed something

---

### Post by MartyBuntu on 2016-08-26
Same here. It's been down for a few days...I'm running Ubuntu Studio 64bit with the MATE desktop.

---

### Post by Timothy Taylor on 2016-08-30
Reassuring to know it's not a problem with my system.
Will this thread get flagged as a bug report?

*edit*
just filed this bug on lauchpad

---

### Post by ghostmyers on 2016-09-20
Same here, almost 2 months with this problem. :-?

---

### Post by #&amp;thj^% on 2016-09-20
Until this get fixed...You can use ''My-Weather-Indicator'' which can be installed.
Not the solution you wanted...but.

---

### Post by ian-weisser on 2016-09-20
Weather information providers come and go, regularly breaking weather apps that are often hardcoded to a single provider.
And, of course, provider APIs sometimes change without adequate warning.

It's not enough to simply file a bug.
Dig into the code, and find that provider and that API request.
Determine if it's a provider or API issue, or if it's really a problem with the code.
That is basic bug triage - user level stuff. Don't waste developer time on simple issues.

---

