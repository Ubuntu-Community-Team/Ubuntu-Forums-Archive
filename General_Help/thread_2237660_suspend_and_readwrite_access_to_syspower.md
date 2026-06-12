---
title: "suspend and read/write access to /sys/power/"
date: 2014-08-03
forum: General Help
---

### Post by Philip_Kiser on 2014-08-03
Dear Ubuntu Experts,

I have Ubuntu 12.04 installed on a Gateway ML6732 laptop. The system was running perfectly for several months. However, a few weeks ago the suspend function stopped working. After some experimentation it appears the underlying problem is that read/write permissions for the files in /sys/power are disabled for my normal user account. After allowing read/write access to these files the system suspends normally. However, if I reboot the system read/write access to the /sys/power/ files is lost and have to be manually changed again. Is there a way to maintain the read/write permissions for the files in question after rebooting?

Thanks for your help.

Philip

---

