---
title: "To partition or not to Partition"
date: 2007-05-05
forum: General Help
---

### Post by rubix64 on 2007-05-05
I have a system that I just set up for ubuntu. The master drive for platforms and programs is 330GB and the slave is a 750GB. How do I go about adding a partition to the 330GB drive that Im running ubuntu on so that I can run windows on the extra partition.

is this even the best way to do this?

thanks in advance!

---

### Post by Buster222 on 2007-05-05
During the install process you get the opportunity to partition the disk. The menu lets you create partions of the size you want and then chose the file system and mount point for each partion.

---

### Post by rubix64 on 2007-05-05
Im sorry guys but im a little new to this. could someone give me  a semi detailed idea of how to run windows on a portion (size?) of my 330.

or....
 do I even need the os

can i use vmware for windows only software i.e. CS3, premiere pro etx...?

---

### Post by cptjaben on 2007-05-05
What you can do is run an Ubuntu live cd and use an application called Gnome partion Editor, found under the system menu I believe. Resize it to the size you wish for your windows partition. Next, boot the windows cd and install windows on that partition. Windows sometimes deletes GRUB boot loader so if you don't see the option to boot to Ubuntu when you start up your computer after your windows install, run the live cd and use it to reinstall GRUB. hope this helps, Also if your just going to be using a few programs i'd suggest making a small windows partition. Good luck.

---

### Post by rubix64 on 2007-05-05
O.K. so using the GNOME partition editor I attempted to resize the 330GB drive "sda" to just a little smaller leaving a 50GB partition for xp (too much for win? or too little?) anyways the error I got upon trying to apply my resize what that /dev/sda1 was mounted. I thought I had unmounted it by right clicking on it and selection unmount, at which point it opened 2 new folders, both directories in /home and removed the locked icon next to the drive 'sda1' I then tried to apply the resize but was given an error msg stating that /dev/sda1 was mounted...


any thoughts guys. Id appreciate anything as Im stumped

Thanks,
Rube

---

### Post by cptjaben on 2007-05-05
are you using gnome partition editor off of a live cd or just off of your Ubuntu install?

---

### Post by rubix64 on 2007-05-05
live cd...I couldnt find it inmy install system>Admin

---

### Post by woodgdo1 on 2007-05-05
There is a gparted live cd that works wonders for all sorts of Windows ntfs and linux partition resizing chores. You could give that a try...

---

### Post by mattG on 2007-05-06
> **rubix64 said:**
> live cd...I couldnt find it inmy install system>Admin

sudo apt-get install gparted

---

