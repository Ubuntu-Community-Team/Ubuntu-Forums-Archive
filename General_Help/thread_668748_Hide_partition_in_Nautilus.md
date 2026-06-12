---
title: "Hide partition in Nautilus?"
date: 2008-01-15
forum: General Help
---

### Post by zhimsel on 2008-01-15
Is there any way of hiding a particular partition from showing up in Nautilus unless its mounted? I have 2 partitions (one empty and one with stuff on it, but unmounted most of the time) and they show up in the "Places" bar and the "Computer" section in Nautilus as "11.4GB Volume", etc. Can I hide these?

---

### Post by zhimsel on 2008-01-23
Anybody have any ideas/solutions?

---

### Post by louieb on 2008-01-23
Just a wild as guess but it might work.
Open up Nautilus > bookmarks > edit bookmarks.

---

### Post by zhimsel on 2008-01-23
> **louieb said:**
> Just a wild as guess but it might work.
Open up Nautilus > bookmarks > edit bookmarks.

Naw, it's not in the bookmark section. It's system-recognized hardware. It shows up as a disk in "Computer". It's in the section above bookmarks.

---

### Post by zhimsel on 2008-01-27
I figured out how to get rid of the floppy drive and the blank partition from Nautilus. I realized that there was an entry for the floppy in my fstab (I'm not sure why, as I don't even have a floppy on this PC), as well as one for that blank partition. I commented them both out and restarted. Gone from nautilus.

Anyone know how I can stop the second partition (which is *not* empty, and is not automatically mounted, so you are forced to mount from the command line as root) from showing up in nautilus? Or at least change the name from "4.8 GB Volume" to /path/to/volume?

---

### Post by Skerit on 2008-04-06
I'm wondering about this as well,

I have a small, 8 MiB partition (needed for booting into windows) which won't go away!

---

### Post by dornik on 2008-04-27
heres the solution guys. :)

credit for this solution (and it works great!) goes to user zero-9376 in this post 

[http://ubuntuforums.org/showthread.php?t=567003](http://ubuntuforums.org/showthread.php?t=567003). 

heres what he suggested:-

[COLOR="Red"]ok when the ubuntu system boots up it starts a bunch or programs/services which are associated with different runlevels, the scripts that start those services are in the folders /etc/rcX.d/ where X is a number. In ubuntu the default runlevel is 2 so the scripts in the /etc/rc2.d/ folder are the ones that get are executed when ubuntu starts and shuts down.

if you have a look in there, there are K(number)servicename and S(number)servicename. the k and s are scripts that are called during shutdown and startup respectively, the number is used to determine the order in which the scripts are started.

in linux everything is represented by files, your partitions are probably /dev/hdaX or /dev/hdbX (mine are sd instead of hd because they are sata drives). if you dont want the system to be able to see or mount the partition all you have to do is delete the file that corresponds to the partition so if one of your fat32 partitions is /dev/hdb1 you want to delete that file. you want to do this before gnome starts up so you put the

rm /dev/sdb1

in one of the /etc/rc2.d/S____ files with a low number, as i said i used S10 that way the device will be deleted before the system can see it and it wont be accessible.

if you change your mind you can just remove the line from the file and reboot and it should work again. again im no expert but it worked for me


EDIT:
So step by step,
if the partition you want to hide is hdb1

open terminal
sudo gedit /etc/rc2.d/S10xserver-xorg-input-wacom
change
Code:

#!/bin/bash

. /lib/lsb/init-functions

to
Code:

#!/bin/bash
rm /dev/hdb1
. /lib/lsb/init-functions

save the file and close the editor and terminal
reboot your system[/COLOR]

---

