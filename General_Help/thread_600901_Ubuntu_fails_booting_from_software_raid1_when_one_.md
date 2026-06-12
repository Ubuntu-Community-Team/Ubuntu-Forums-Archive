---
title: "Ubuntu fails booting from software raid1 when one disk is not available"
date: 2007-11-02
forum: General Help
---

### Post by dbendlin on 2007-11-02
Hello Guys,

I've recently installed the following OS's on my desktop computer
1.- Ubuntu 7.04 Alternate 
2.- Ubuntu 7.04 Server
3.- Ubuntu 7.10 Server
4.- Ubuntu 7.10 Alternate

I'm now running Ubuntu 7.10 Alternate, and its installed in 2 SATA Disk of 250 GB the followin way:

/dev/md0 is mounted on /boot
/dev/md1 is LVM Phisical Disk containing
/dev/lvmg0-root mounted on /root
/dev/lvmg0-swap as swap
/dev/lvmg0-datos mounted on /datos
/dev/lvmg0-backup mounted on /backup

/dev/md0 is a RAID1 array build with mdadm using /dev/sda1 and /dev/sdb1
/dev/md1 is a RAID1 array build with mdadm using /dev/sda2 and /dev/sdb2

When both SATA disk are connected, everything works just great, but when simulating a disk failure (i.e.by disconecting one of the disk /dev/sda or /dev/sdb), Ubuntu will fail to boot.

In the process of trying to solve this issue I've tried the following things:
1.- Install grub on both (/dev/sda and /dev/sdb) MBR's
2.- Compare UUID field from /etc/mdadm/mdadm.conf with /etc/fstab (They're diferent as mdadm reports one UUID and vol_id other.
3.- mount devices in fstab by its device name not the UUID

None, of this worked, I mean, if the 2 sata disk are online then everything's fiune, but when either one of them is missing system wont boot.

Grub loads stage 1, but when it passes that stage and actually tries to load the kernel it gets frozen.

I can only think of the following possible causes:
1.- md_mod is not been loaded by the generic kernel
2.- md_mod loaded by the generic kernel has a bug and fails to recognize the /dev/md0 raid1 device
3.- generic kernel is not compiled to support mdadm (well this isnt necesary if things get loaded via modules right?)

Finally, I've tried the same setup in another computer installing CentOS 5, on that OS I only had to install grub to both /dev/sda and /dev/sdb, after that I tried disconecting /dev/sda and booted the system succesfully only with /dev/sdb, after that I readded the /dev/sda, disk's got synced and array wentonline just fine.

After that I tried disconnecting /dev/sdb and everything went just OK.

Should this issue be filed as a bug? if so where?

Thanks in advance!

Kind Regards,

Diego Bendlin

---

### Post by dbendlin on 2007-11-03
Guys,

After reading my original post I realized that It wasn't clear enought that the situation described above was reproduced in 7.04 Desktop Alternate & Server and on 7.10 Desktop Alternate & Server.

Thanks in advance for any help you provide.

Regards,

Diego Bendlin

---

### Post by dbendlin on 2007-11-03
Guys,

I recompiled my ubuntu 7.10 Alternate kernel adding support for RAID and LVM into the kernel (not loading tham as modules), booted the system ok, but after that I disconnected one of the drives and the system wasn't able to boot :(

So, I've downloaded and installed openSUSE to give it a try, I setup a system like explained above, except for the LVM volume (openSUSE installer didn't allow me to create an LVM volume over a RAID device, wierd, maybe googling arround will help me get that done).

After installing everything over RAID1 using mdadm I disconnected the primary disk an the sistem still booted, after that I readded the disk and everything worked just great.

Can the problem had something to do with mdadm been incompatible with the generic  kernel?

At least im calm now, becouse I thoth it was me doing something silly and not been able to make mdadm work on mi ubuntu, but this seems to be a problem in ubuntu itself.

Hope some of the developers get to read this and try to solve the issue for further releases of ubuntu.

---

### Post by fjgaude on 2007-11-03
It would be correct for you to file a bug report. Thanks for your finding.

---

### Post by dbendlin on 2007-11-06
After searching throught the bugs database, I think this couple of bugs are the same:

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/120375]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/120375")
[https://bugs.launchpad.net/ubuntu/+bug/133663]("https://bugs.launchpad.net/ubuntu/+bug/133663")

Hope you guys get to fix this soon.

Thanks in advance,

Diego Bendlin

---

