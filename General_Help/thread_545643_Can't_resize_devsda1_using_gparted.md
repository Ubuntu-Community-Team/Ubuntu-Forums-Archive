---
title: "Can't resize /dev/sda1 using gparted"
date: 2007-09-07
forum: General Help
---

### Post by harrisupstate on 2007-09-07
When I attempt to resize my /dev/sda1 (it displays as "ext3") using gparted, I get an error that the drive is mounted.  I then right-click on the drive and "unmount", and that appears to work, but I keep getting the same error.

Any help would be appreciated!  Thanks.

---

### Post by Irihapeti on 2007-09-07
It sounds like you are using the GParted on the liveCD. I've had a similar experience and I just ignored the error (the second time) and everything seemed to work fine.

If you get the Gparted liveCD 
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=519163](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=519163)
it has a later version of Gparted than is on the Ubuntu CD. Also, it doesn't keep trying to mount the partitions that you're working on. I just used it a couple of hours ago to do some major rearranging of my drive.

HTH
Irihapeti

---

### Post by bronze on 2007-09-07
GParted running from Ubuntu can be difficult to handle - I suggest you download the GParted live CD, it won't mount any of the partitions and it's very easy to use.

Edit: 2 late

---

### Post by Irihapeti on 2007-09-07
Well, bronze, you could say: great minds think alike :-)

Irihapeti

---

### Post by harrisupstate on 2007-09-07
Yes, I was using the Ubuntu Live CD.  Now, are you saying that I should use the gparted live CD to boot the computer instead of the Ubuntu live CD?  If so, would that actually boot Ubuntu??  I don't really understand.........  thanks again.

---

### Post by merlinus on 2007-09-07
gparted live cd will not boot ubuntu, which is what you want in order to resize and/or move partitions easily.

You cannot do this with mounted partitions, and gparted live saves the hassle of having to unmount, mount, unmount, mount.

It is also a much newer version than on the ubuntu live cd, with more features and capabilities.

-merlin

---

### Post by harrisupstate on 2007-09-07
Okay, so...  if I use the gparted Live CD it will just load gparted,,,,  then I can do my thing with resizing...  then I guess I can just reboot as normal and be right back into regular Ubuntu?

My real goal is to install Windows with dual-boot.  I just have a need to use Windows, unfortunately....

Thanks again.

---

### Post by merlinus on 2007-09-07
Info here on dual booting in differing scenarios:

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

-merlin

---

