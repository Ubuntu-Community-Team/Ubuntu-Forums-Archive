---
title: "running a Raspi with a WD elements with 1 TB and USB 2"
date: 2018-11-20
forum: General Help
---

### Post by dilbert_one on 2018-11-20
hello dear all  - good evening dear Ubuntu-experts, 


I’ve just purchased a Raspberry Pi 3 and i’ve installed an operating system onto the raspi so that i can run it.

**goal:** I want to have a little NAS or a Samba-Server

After this first step - the installing of an operating system onto the raspi - I’ve succesfully set it all up and i’ve managed to get the USB ports.
It seems to be working with a wireless wifi dongle. And that seems pretty fantastic. I am glad about this. So the next thing i did is to add a keyboard.i took a wireless keyboard. 

**so far so good:** The problem i have is that cannot see my external HDD which is plugged into a spare USB port. 
The HDD is a WD elements with 1 TB and USB 2. The good thing: it has its own power supply. Its got an NTFS file system and this works on my linux machine, my Windows machine and my Linux-Machine.

Well - i guess that i have to putty into the operating system and try to mount so that i have somewhat like so; /dev/sdb1

In linux “ntfs-3g” is used to see ntfs partitions - well perhaps this is missing?


is this correct? 

i hope that there is some one here in the great ubuntu-forum that has got some ideas for me. 

Is there anything else i should do!?.
love to hear from you
greetings

---

### Post by hartman8227 on 2018-11-20
If you'll post the results of the following commands

lsusb -t

and 

less [COLOR=#000000][FONT=Arial]/proc/bus/usb/devices


That will give us a better idea of where to start.[/FONT][/COLOR]

---

### Post by wildmanne39 on 2018-11-20
*Thread moved to **General Help for a more appropriate fit**.* for the moment, please let us know what linux OS you are running?

You can use SSH to access your PI 3, not sure about putty, I have never used it and was told not too but my PI 3 came with Arch preinstalled, I just needed to install and setup some apps.

---

### Post by nosmadar on 2018-11-21
Putty is a PITA.  Stick with ssh, much simpler and pretty much 'native' to Linux.
  I think Putty was created to allow Windows to do what Linux can already do.

---

