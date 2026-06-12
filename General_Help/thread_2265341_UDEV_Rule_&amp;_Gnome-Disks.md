---
title: "UDEV Rule &amp; Gnome-Disks"
date: 2015-02-14
forum: General Help
---

### Post by Resuutunubu on 2015-02-14
Hello Forum,

As it appears Gnome-Disks might over-ride UDEV rules. But I like to put this out for discussuion.

Here is what happened:

System 12.04 with several HDDs. One is the main system HDD.
It is used as a file and print server but running on a regular 12.04 system with LXDE desktop.

I've defined UDEV rules to put the HDDs on standby to save power.
Example: 
```
SUBSYSTEMS=="scsi", KERNEL=="sd?1", ATTRS{model}=="WDC WD604BC-78DE", RUN+="/sbin/hdparm -S 60
/dev/disk/by-uuid/120f0de3-1e7a-42cf-43ec-9abfeab6b5cb"
```

This used to work until I opened gnome-disks.
After that, no standby mode anymore.
But the main HDD apparently tries to do it but switches on again immediately.

Hence my conclusion that gnome-disks somehow kicks out UDEV rules.

I have no idea hot to restore this.
I tried: adding the UDEV attribute ```
**OWNER="root"**
```, restarting udev, restarting the whole machine, turned the sleep mode in gnome-disks off and on.
Nothing would help.

Has anyone experienced this before?
Is there any log file that would show what is keeping the HDD awake after using gnome-disks?

Any help would be much appreciated.

Regards,
Stephan

---

