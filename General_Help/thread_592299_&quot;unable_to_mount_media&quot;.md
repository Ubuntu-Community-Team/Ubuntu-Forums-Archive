---
title: "&quot;unable to mount media&quot;"
date: 2007-10-26
forum: General Help
---

### Post by Kymus on 2007-10-26
Every time I try to look at the contents of a CD or DVD, I'll get that error. What puzzles me, is that it was working fine just a few days ago :confused:

**EDIT:** I re-enabled the ATI restricted drivers and now it seems like magically the CD's and DVD's are mounting and being read. I suppose now everything is fine as far as this particular issue goes, but I am really confused as to why the heck it happened. Here's the story on [my struggle with the ATI drivers]("http://ubuntuforums.org/showthread.php?t=590303").

**Edit edit:** After ejecting the disk that was in there, I put a different one in. Regardless, the drive still gave the name of the previous disk. I tried to log out, and log back in and that didn't solve anything. I found that reseting the computer is what ended up changing the media. So it seems that without a reset, it will not read any swapped media. I burnt a DVD and so far it seems that it was burnt perfectly fine (still haven't fully tested all the data yet), however. It seems that a number of settings are all funky. My previously mentioned (as yet unsolved) ATI Driver issue (which I think has to do with xserver-xgl), this drive mount issue, and then also there seems to be a discrepancy when logging in; X and GNOME are having mismatched versions of my keyboard and I'm prompted to select either or (regardless of choice, it still seems to act perfectly normal). **Is there a chance that all this is connected?**

**tiny edit:** For what it's worth - and maybe this is normal due to the problem - a disk will not eject by me pushing the eject button on the drive. It will only eject if I right click either the CD or Drive icon and select eject. Then it's fine. The media disappears and then it won't read anything until I reset again (*rawr*)

---

### Post by Kymus on 2007-10-28
I was hoping that this was one of the threads that would of gotten fished out yesterday (unanswered posts day), but apparently I'm not that lucky :P. Ah well.

I really prefer patience over bumping, but unfortunately threads get buried in 5 minutes (literally) and once they're buried, well.. yea. 

Sorry I gotta bump

---

### Post by Kymus on 2007-10-29
bump

---

### Post by shmatt on 2007-11-11
I have this same problem. One day I rebooted my computer and it hasn't recognized a cd or dvd since.

Just for fun I'll post my fstab:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9e3dbb2a-d166-47e3-b211-c83307769440 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5542241f-b05b-4239-8e3b-adda30febd3f none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by jdwinfodesign on 2007-11-22
Same problem. 

Bump.

---

### Post by Kymus on 2007-12-05
bump

---

