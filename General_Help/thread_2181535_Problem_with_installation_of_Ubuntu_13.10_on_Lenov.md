---
title: "Problem with installation of Ubuntu 13.10 on Lenovo T500"
date: 2013-10-18
forum: General Help
---

### Post by bostjanv on 2013-10-18
Hello,
I just installed Ubuntu 13.10 on a Lenovo 500 laptop, and have run into two problems:

(1) The toolbar at the left is not visible. When the appropriate positions are clicked the corresponding program starts; however, the icons are not visible.

(2) The laptop is placed on a port replicator, which is connected to monitor. The installation was performed with the monitor turned off since the laptop screen was being used. However, when the laptop cover was closed and the monitor turned on, the monitor display was garbled.

Any advice would be appreciated.
Regards,
bostjanv

---

### Post by pqwoerituytrueiwoq on 2013-10-18
have you tried installing additional driver, if any?
did it work on the live disk?

---

### Post by bostjanv on 2013-10-18
Thanks for the reply. Could you be more specific? Actually, since I had an unused computer I simply installed Ubuntu in the hope that it would work, so I did not test it with a live disk before installation. When you mention "additional drivers" where and how do I get them? Regards, bostjanv

---

### Post by pqwoerituytrueiwoq on 2013-10-18
search the dash for driver
it is also in software sources in the last tab

---

### Post by bostjanv on 2013-10-19
Thanks. I tried your advice, but it didn't work (after installing the Radeon driver I got a black screen with only mouse cursor showing on the laptop screen; after switching to the monitor, I was able to login; but the mouse cursor was invisible etc. etc.). After an internet search I discovered the site [http://www.linlap.com/lenovo_thinkpad_t500](http://www.linlap.com/lenovo_thinkpad_t500). I guess I'll have to expend some more effort on the basis of information found there. Regards, bostjanv

---

### Post by pqwoerituytrueiwoq on 2013-10-20
with that gpu you will be better off not using the proprietary driver
you should use the 3.12 kernel [https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)
you should remove that driver and use the default open-source one (the one in the 3.12 kernel is pretty good with old ati gpus)
if it still does not work i suggest a different desktop environment (gnome, cinnamon, xfce, lxde, or kde)

---

