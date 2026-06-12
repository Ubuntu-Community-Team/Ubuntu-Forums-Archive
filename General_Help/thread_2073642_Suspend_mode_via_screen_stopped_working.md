---
title: "Suspend mode via screen stopped working"
date: 2012-10-20
forum: General Help
---

### Post by squenson on 2012-10-20
Hi All,

I have just upgraded to Ubuntu 12.10 64-bit. The suspend mode via the screen icon representing a small switch doesn't work anymore. I can shutdown or restart though.

I have configured my computer to go to sleep when I close the lid of the laptop and this works.

I am not sure where to start my investigations...

Many thanks in advance for your help!

---

### Post by 2F4U on 2012-10-20
First of all, you should post your hardware specs, graphics card and if you are using open source or proprietary video drivers. Secondly, there is a file named /var/log/pm-suspend.log, which contains additional output created during the suspend process. Look into this file and see if you can find any error messages or problem reports.

---

### Post by squenson on 2012-10-20
I have an HP6830s with an ATI Mobility Radeon HD3430. I have 3GB or RAM and I run Gnome. I had problem with the video set-up and I managed to fix it with some advices from [this thread]("http://ubuntuforums.org/showpost.php?p=12304403&postcount=2") to get back to a proper resolution of 1,440 x 900.

I looked at the log file /var/log/pm-suspend.log and it doesn't contain error messages as far as I see.

I run the Systems Tools > Administration > System Testing program and the tests related to the suspend mode went very well: the machine suspended for a minute and started again by itself. I see the trace of this activity in the /var/log/pm-suspend.log file.

---

