---
title: "Mount encrypted, LVM volumes without &quot;special device... does not exist&quot; error"
date: 2015-06-08
forum: General Help
---

### Post by markling on 2015-06-08
My attempt at rescue of encrypted disk was stalled by the following error, which occured when I tried to mount my encrypted LVM volumes:

mount: special device /dev/hd... does not exist

This error occured while following the excellent instructions given by jerome1232 in this SOLVED thread here: [http://ubuntuforums.org/showthread.php?t=940904](http://ubuntuforums.org/showthread.php?t=940904)

This seems to be a common problem.

Forums widely report that the solution is to use the following command to make the logical volumes active:

sudo vgchange -a y Ubuntu 

But there are unsolved requests for help where this command is used and the VGs are activated and yet the same error occurs: "mount: special device... does not exist".

The problem is the mount command, e.g. to mount the logical volume called "home" to the mount point at "/media/home":

sudo mount /dev/Ubuntu/home /media/home

It seems to satisfy some people. But, for some unexplained reason, it may not work as given.

I find the command would only work if it was written thus:

sudo mount /dev/mapper/Ubuntu-home /media/home

But then I was using crunchbang linux. I hope nevertheless that this is an appropriate place to post this clartification, and that if other lost souls pass this way they might use the help.

The clarification was given here: [http://forums.fedoraforum.org/archive/index.php/t-183575.html](http://forums.fedoraforum.org/archive/index.php/t-183575.html)

---

