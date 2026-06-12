---
title: "dual boot xp"
date: 2008-06-15
forum: General Help
---

### Post by Dai777 on 2008-06-15
Hi just wondering if you can throw some light on a small problem for me.
I tried to do a dual boot for ubuntu and xp pro but my computer can not find the hard drive when it comes to repartitioning xp.
here is what my current partition looks like:

[IMG]http://blufiles.storage.live.com/y1pSwMAbq-FtW9F1j9_3RdERP5Suc0Q82OhI5xKRrS93wcQM9eNoBveKe0TPKF6mkuVobkF9sO2S4Y[/IMG]
At the moment I'm using virtualbox with xp (ubuntu host) but i'd like to do a dualboot but for some reason my hard drive does not show up in xp partitioning setup

If I go to over write Ubuntu, XP can't find my hard drive when it comes to the re-partitioning bit, all three options are blank.

---

### Post by sailor2001 on 2008-06-15
I believe it is wisest to partition xp right in xp... Right click "mycomputer" and manage hard drive or something like that.

---

### Post by uidb4056 on 2008-06-15
As far as I know to have multi boot with XP and linux XP should be installed first. Currently your linux partition is using all of your disk, even if you shrink /dev/sda1 to have free space for create your XP partition when you install XP it will writes your MBR and you can't boot your linux whitout repairing it.

---

### Post by meierfra. on 2008-06-15
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

---

### Post by Dai777 on 2008-06-16
I did try to install xp first but as soon as I get  past the license and to re-partition the disk it say's it can't find any disk. You have three options and all are blank. It will find my external hard drive if it is plugged in but not my computer hard drive.

Can gparted partition my hard dive to ntfs so I try and install xp there?

---

### Post by uidb4056 on 2008-06-16
> **Dai777 said:**
> I did try to install xp first but as soon as I get  past the license and to re-partition the disk it say's it can't find any disk. You have three options and all are blank. It will find my external hard drive if it is plugged in but not my computer hard drive.

Can gparted partition my hard dive to ntfs so I try and install xp there?

Yest but you have to resize your /dev/sda1 to free up unpartitioned space for XP see the link posted by meierfra in previous message. You don't need to format from gparted the unpartitioned space it's better to format from XP install as you can see in the link.

---

