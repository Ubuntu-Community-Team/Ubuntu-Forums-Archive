---
title: "Need to reconfig Grub to read menu.lst from correct drive - how?"
date: 2007-09-07
forum: General Help
---

### Post by einstein on 2007-09-07
Greetings!

My Compaq Presario V2000 came with WinXP Home installed.  I installed Feisty on the main drive as well  so had a dual boot with all working well.  I then installed Feisty on a USB HD with Grub installed to the main HD.  Everything works fine EXCEPT that Grub reads menu.lst (and whatever else) from the USB drive, which means that I cannot boot the computer unless the USB drive is attached.

Question:  How do I reconfigure Grub to read menu.lst from Feisty on the main hard drive?  I am a little on the newbie side and have gotten myself into a few hair raising predicaments previously so I am not up to experimenting on this one.

The USB installation apparently overwrote the Grub stuff in the main drive MBR so reinstalling the main drive Feisty should corrects things .... except that I really do not want to reinstall.

Thanks in advance.

Dennis

---

### Post by yabbadabbadont on 2007-09-07
Please post the contents of your /etc/fstab from the main hard drive (not the USB).

---

### Post by einstein on 2007-09-07
fstab from the main HD installation, as requested. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=b529a43c-27c0-4a33-a333-45384244f202 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6481edea-2f10-4c16-b521-913df37d910e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by yabbadabbadont on 2007-09-07
> **einstein said:**
> fstab from the main HD installation, as requested. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=b529a43c-27c0-4a33-a333-45384244f202 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6481edea-2f10-4c16-b521-913df37d910e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

OK, here we go.  Open a terminal window.  Run "sudo grub".  This will drop you into a grub interactive shell.  Now issue the following commands: ```
root (hd0,1)
setup (hd0)
quit

```
That should reinstall grub to the MBR of the main drive and tell it to look for its config file on /dev/hda2.  (hd0,1) is grub speek for the second partition on the first drive.  (grub counts from zero)

---

### Post by einstein on 2007-09-07
Perfect!  Much thanks, yabbadabbadont!

 - Dennis

---

