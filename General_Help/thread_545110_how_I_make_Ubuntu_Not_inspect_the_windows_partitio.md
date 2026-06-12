---
title: "how I make Ubuntu Not inspect the windows partitions"
date: 2007-09-07
forum: General Help
---

### Post by teren9 on 2007-09-07
how I make Ubuntu Not inspect the windows partitions.
I do not want it to touch the xp partitions when booting, only the linux partitions.
It is taking aa lot of time and I don't want it.

---

### Post by zekica on 2007-09-07
You can open Terminal: Applications -> Accessories -> Terminal and type:

sudo cp /etc/fstab /etc/fstab.old [enter]
Then enter your password and then:
sudo gedit /etc/fstab

Now, find a line that looks like this:
# /dev/sda1
UUID=3007-17F2 /media/sda1 **vfat** defaults,utf8,umask=007,gid=46 0 [COLOR="Red"]1[/COLOR]

and change "1" at the end of the line to "0" (without quotes). Save this file and close both windows.

This should solve your problem.

---

