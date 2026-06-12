---
title: "fstab"
date: 2007-05-23
forum: General Help
---

### Post by ronodle on 2007-05-23
Ubuntu-7.0.4 automatically mounts all of the partitions on my system at boot up.  I have four hard drives with partitions running seven different operating systems (or different versions thereof).  I don't want any other partition automatically mounted (except, of course, for swap) apart from the one containing Ubuntu-7.0.4.  Until this Linux version, simply editing /etc/fstab took care of this.  With this version, fstab seems to have no influence on what partitions actually get mounted at boot time.

Could someone please enlighten me, and explain how to deal with this?  Thanks, Ron

---

### Post by vtel57 on 2007-05-23
Ron,

Can you post a copy of your fstab? Just so we can look... :)

---

### Post by ronodle on 2007-05-23
What I tried was simply eliminating all the lines referring to anything other than proc, /, and swap.  Had no effect on automounted partitions.  Then I tried the one I use for Ubuntu-6.06 LTS which has no UUID references.  Also had no effect on the automounted partitions.

Here is the first attempt:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=69eb8776-b303-43c8-ac53-459e635e32c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb7
UUID=32ddb202-3237-45e3-abed-edd09f810a10 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

And here is the second:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

This was always a no-brainer.  Obviously I'm not keeping up.

Cheers,
Ron

---

### Post by vtel57 on 2007-05-23
Man! I am stumped. I know there's a simple way to do this. I had a similar problem in Mepis. I'm not familiar with how Feisty handles volume mounting at boot up, though. I use 6.06 still.

Search these forums, Ron, and see if you can find anything that might help you. I did a Google search, but didn't find any specific fixes for this. I'll keep my eye on this thread to see if you make any progress. I'd like to know for future reference how to fix this.

Luck! :)

---

### Post by ronodle on 2007-05-24
Thanks very much for taking a look.  Think I'll just chuck 7.04 and stick with 6.06 LTS.  I've managed to outwit it when it tries to think for me.  Guess i'm just not clever enough for 7.04.   I'm more of a Gentoo kind of guy anyway, but I like to try out the new stuff.

Thanks again,
Ron

---

### Post by vtel57 on 2007-05-24
Gentoo! ARRRRRRRRRRRGH! That distro SCARES me! ;)

Yeah, I stuck with 6.06 too. It worked fine. Why screw up a good thing. When the next LTS version comes out, I might upgrade. Till then, I'm happy. :)

Luck!

---

