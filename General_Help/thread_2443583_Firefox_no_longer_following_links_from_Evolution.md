---
title: "Firefox no longer following links from Evolution"
date: 2020-05-17
forum: General Help
---

### Post by jfholla on 2020-05-17
I've encountered a strange problem on my wife's desktop machine. She uses the email client Evolution to manage her e-mail and Firefox is the default web browser on her machine. 

A week ago Firefox kept crashing upon opening and per-instructions I found on the web I removed and re-installed it again. That fixed the crashing problem. However when one clicks on an embedded link in an e-mail in Evolution, Firefox opens, but does not go the linked site. 

I checked the Firefox preferences and it is set as the default browser.

Any thoughts to a solution?

---

### Post by TheFu on 2020-05-17
I&#8217;d guess you can than the snap packages and constraints.
Check whether evolution is a snap package:
**snap list**

Lacking that, check the xdg-open action for the system.

---

### Post by speartip on 2020-05-18
It could be that the crash has caused your Firefox profile to become corrupted. It might be a good idea to start with a clean profile by either deleting the .mozilla folder in your home folder or renaming it so that you can rename it back again if it proves to not be the issue.

---

### Post by TheFu on 2020-05-18
> **speartip said:**
> It could be that the crash has caused your Firefox profile to become corrupted. It might be a good idea to start with a clean profile by either deleting the .mozilla folder in your home folder or renaming it so that you can rename it back again if it proves to not be the issue.

Along those lines ... check the system log files for any errors/warnings. Those are in /var/log/.
The disk could be failing.  Use either gnome-disks or smartctl
The file system could be corrupt.  Use fsck.

I'd just move the ~/.mozilla directory to a different name, do the testing, see if that helps. If not, put it back.
Also, try a new account. See if that works.  If it does, then it is likely some mix of configuration files in your userid that broke.  Creating a new userid for a test is pretty quick, very low risk.  If it doesn't work in the new userid too, then it isn't specific to any user. It is a system issue.

---

### Post by jfholla on 2020-05-19
ThAnks for all the suggestions. As it turned out it appears to be a corrupted profile file. I created a new one and

---

### Post by jfholla on 2020-05-19
Opps!! I cut myself off.  Creating a new profile fixed the problem.

---

### Post by TheFu on 2020-05-19
> **jfholla said:**
> Opps!! I cut myself off.  Creating a new profile fixed the problem.

Please use the "Thread Tools" button just above the first post to make it "SOLVED".  Help the community out.

---

