---
title: "Ubuntu booting into busybox. Asks for manual fsck"
date: 2016-11-14
forum: General Help
---

### Post by ivaylo.tanev on 2016-11-14
Hi there my Ubuntu is booting into BusyBox with a message  *ERROR* uncleared pch fifo underrrun on pch transcoder A *ERROR* PCH transcoder A FIFO underrun 
  I read some other threads but the only thing that would prompt a response in the console is typing exit. which gives me  UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
It happened after a reboot so no new software was installed. I have booted a live 16.0 from a cd now.

  Some help would be useful  Thank you!

---

### Post by TheFu on 2016-11-14
Can't say the command you need to run without more data.  If you can get back into busybox (no using a live-boot flash/cd/dvd), the you can run **sudo touch /forcefsck** and reboot.  That will force an fsck on the / file system at the next reboot.

If that doesn't work, post the output from **sudo parted -l** so we can see which partitions/disks to fun the checks on. basically you need to run something like sudo fsck /dev/sda1 ;  But the file system cannot be mounted (in use) at the time.  Also, do not run this on non-Linux file systems. [https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting) explains, though I disagree with some of the suggestions.  There are always the manpages for more details too.

---

