---
title: "Volumes Showing Up On Desktop"
date: 2007-10-11
forum: General Help
---

### Post by JustinAllen on 2007-10-11
Ok, I've browsed the various threads throughout the forums and have gottem some great ideas and I want to clarify them before I do anything.  Ok, basically I've got no volumes showing up on my desktop and no cdrom.  Now I've gone into gconf-editor and to the appropriate place, check the volumes_visible and it doesn't make a difference.  I'm assuming this has something to do with my fstab, so i'm going to post it below.  Now another thing that bothers me is i see sample fstab and other people's fstabs on the forums and there's look fine, but with mine..for my drives it shows the UUID= piece and i wasn't sure if i could just remove that and replace it with /dev/hda1 or whatever and then add /media/hda1 so it shows on the desktop....just a thought...

Thanks for your time and help!!

Fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=299b51e4-3d97-4a35-80bf-ec19c1eb361e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=fc1a205e-606d-44ed-97fc-87163f663dec /home           ext3    defaults        0       2
# /dev/hda1
UUID=bfed482a-7711-45f4-bb4e-7bf2732cb4cc none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by eldragon on 2007-10-11
from what i see on your fstab, the only volume you should be seing is the cdrom, and that only happens when its mounted (aka, cdrom inserted)...is that not happening?

---

### Post by JustinAllen on 2007-10-11
Yes, that does happen..as does when i insert a USB drive, it does the same thing.  I want my HD's to show too and they don't.   What I was getting at I guess was if i edit the fstab for the UID=blahblahblah and add /media/hda1, etc would that then have them show up on the desktop?  Thanks for responding so fast too :D

---

### Post by JustinAllen on 2007-10-11
bumptiy bump....tried asking in IRC but it doesn't seem like anybody was free to help...quite busy in there..lol

---

