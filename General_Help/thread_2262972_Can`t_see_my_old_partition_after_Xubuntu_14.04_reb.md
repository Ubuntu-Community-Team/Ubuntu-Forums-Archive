---
title: "Can`t see my old partition after Xubuntu 14.04 reboot (Grub error and new partition)"
date: 2015-01-28
forum: General Help
---

### Post by Anders_Makowicz on 2015-01-28
Yesterday i turn offed my computer as usually and today i woke up and runned it

Then i`ve get a grub message ```
/boot/grub/i386-pc/normal.mod not found]
```
So on my pendrive was Xubuntu installer but i didn`t found there option to install Grub  (in unetbootin) and i clicked to install second Xubuntu system to install Grub with it.
Afterwards when grub was installed it was showing only my new second system, when i logged i found that i`ve got my old system on ```
/media/kek/90f4d874-9e8d-44f1-92a1-1db889e0476a/home/canid/
``` (Canid is my old account and Kek is new).
I can`t change user to Canid so it seems like it`s visible as another partition on my file manager, but when i boot computer Grub is showing only Kek.

This is screenshot of GParted, Canid partition should be the /dev/sda1
[IMG]http://s24.postimg.org/9i5ie5eed/Screenshot_28_01_2015_19_08_53.png[/IMG]

How can i delete Kek (maybe change it to the boot patition) and go back to my old partition with all files?
I have important settings on system folders so i don`t want to move home folder to Kek but go back to old partition.

Many thanks for your effort

---

