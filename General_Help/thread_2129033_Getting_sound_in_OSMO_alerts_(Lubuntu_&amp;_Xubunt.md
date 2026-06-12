---
title: "Getting sound in OSMO alerts (Lubuntu &amp; Xubuntu)"
date: 2013-03-25
forum: General Help
---

### Post by M_Mynaardt on 2013-03-25
Hi!

Up until today, I could never get sound for the task alerts in OSMO on my laptop (using Lubuntu) nor my Desktop (using Xubuntu).  I managed to stumble on the solution today.  I needed to install the package "sox".  Seems that OSMO calls a command line app ("play %s") to play its alert sound.  Only it seems that neither Lubuntu nor Xubuntu came with sox on it.  So, I installed sox, and now I have sound for my OSMO task alerts.  Cool!  :cool:

I didn't want to post this if it's old news.  But I couldn't find any other posts about sound not working in OSMO.  I hope this helps someone out there.

---

