---
title: "Grub Bootloader"
date: 2007-07-13
forum: General Help
---

### Post by johncudd on 2007-07-13
I have Ubuntu 7.04 installed on my computer on my secondary harddrive. Then I installed Windows XP on my primary harddrive. Windows of course (as I expected) overrided my grub.I figured I could just reenable grub with a live cd. But it seems as though my /boot is gone. I ran the "df" command and this is what printed out.

```
Filesystem           1K-blocks      Used Available Use% Mounted on
unionfs                 517792     40624    477168   8% /
varrun                  517792       100    517692   1% /var/run
varlock                 517792         0    517792   0% /var/lock
procbususb              517792       144    517648   1% /proc/bus/usb
udev                    517792       144    517648   1% /dev
devshm                  517792         0    517792   0% /dev/shm
lrm                     517792     14160    503632   3% /lib/modules/2.6.20-12-generic/volatile
tmpfs                   517792        12    517780   1% /tmp
/dev/hdb1             75798304  31007876  40940052  44% /media/disk
/dev/hda1             37889268   3767004  34122264  10% /media/disk-1
```

Ubuntu is installed on /dev/hdb1 and Windows is installed on /dev/hda1

I just need to get grub back up and running so I can run both Ubuntu and Windows. Thanks for the help.

---

### Post by Saxomophone on 2007-07-13
Did you follow the instructions at [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")?
or [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
The second one helped me more.

Also, if they're on seperate hdds will the boot loader even do anything? I'm not an expert on this, but you might need to go into the bios and choose which hdd to boot from. That could be part of the problem.

---

