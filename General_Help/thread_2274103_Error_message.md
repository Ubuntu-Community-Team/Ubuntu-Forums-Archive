---
title: "Error message"
date: 2015-04-17
forum: General Help
---

### Post by RobGoss on 2015-04-17
Hello for the past few days I have been getting this error message each time I boot my machine sometimes too or three time this message will popup in a windows I then have to close it

**Following error message below**

System program problem detected
do you want to report the problem now

I have to close the error message to continue my work.

Thanks for any help on this matter

---

### Post by Dennis N on 2015-04-17
It is a message from apport, an automatic error reporting system. You can submit a report and help developers debug the system.

---

### Post by RobGoss on 2015-04-17
> **Dennis N said:**
> It is a message from apport, an automatic error reporting system. You can submit a report and help developers debug the system.

Yes I reported it a few times already thanks so much

---

### Post by Holger_Gehrke on 2015-04-18
The crash-report sits in /var/crash and is named for the full path to the program causing the crash with all slashes replaced with underscores. It will get cleaned away automatically after a day or two. You can at least tell what is crashing by having a look there.

---

### Post by RobGoss on 2015-04-18
I founds out what was causing the error message it's this app- Notification Daemon, the problem is I can't remove it with out removing a few other applications my system uses. Any suggestions? Thanks so much

---

