---
title: "Cant boot (after grub)"
date: 2008-05-25
forum: General Help
---

### Post by Boktai1000 on 2008-05-25
Hello, today I bought a 360 wireless receiver with hopes to use it to play some emulators and other games on Ubuntu, following the "official" guide here [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller). I ended up getting to this part
--------------------------------------
Compiling and installing the drivers

Assuming your current directory is your working directory ("xpad"), all you need to do is to execute the following commands:

make
sudo make install
sudo modprobe -r xpad
sudo depmod -a
sudo modprobe xpad
--------------------------------------
and when i typed sudo modprobe xpad i ended up getting an error or something that said "segmentation fault".  I thought mabe i should reboot and try this again.  Upon reboot grub booted into ubuntu, and once ubuntu starting loading, the loading bar only got to about 1/6 the way before it halted.  I would be thankful even if just got back into Ubuntu without a reformat, im currently on the live cd posting this so if anyone can help at all that would be great.

Edit:  Got it working, read posts below.  If anyone encounters the same error try removing any other controllers, in my case it was my guitar hero 2 x-plorer.  Just follow the guide at [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller) with controllers/guitars unplugged and it should work.  Mabe someone should also update the wiki page informing users to have current controllers/guitars unplugged before proceeding (excluding the 360 controller which your installing).  Also, i tryed booting with both the 360 receiver and Guitar Hero X-Plorer and it wouldnt let me boot, so i shutdown, unplugged guitar and i was back in.  Im pretty sure u can just plug it back in though once in Ubuntu though.

---

### Post by Boktai1000 on 2008-05-25
ive also tried recovery mode and it wont load either, even if i just somehow remove this or something i dont care id rather be back in ubuntu than wait for help on the livecd :[

---

### Post by omababy on 2008-05-25
I couldn't say why your module is producing segmentation faults, but it probably is getting loaded at boot. Edit the grub ('e' key in grub screen) and remove the 'splash' kernel boot parameter, it will remove the progress bar splash screen at boot so you can see whats going on abit better. Maybe too add 'rw init=/bin/bash' see if you can get a prompt and remove the module.

---

### Post by Boktai1000 on 2008-05-25
I was talking on IRC and i change "ro" to "rw" and added init=/bin/bash, and then go to /etc/init.d and see if theres a script or something named xpad and change it to unused_xpad.  I did end up getting to some sort of terminal promt but i was confused as what to do next, and only managed to get into /etc but i didnt no how to edit the file or change it.

---

### Post by omababy on 2008-05-25
try:

modprob -r xpad

or see if its got an entry in /etc/modules and remove it.

---

### Post by Boktai1000 on 2008-05-25
my modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
uinput

for modprob -r xpad i would just type that in at the terminal that i boot to?

---

### Post by omababy on 2008-05-25
Yer, see if that helps. If not try just removing the splash kernel parameter on a normal boot and note what it does or says to get a better idea.

---

### Post by Boktai1000 on 2008-05-25
i had trouble using the rw init=/bin/bash but i got the slash removed, and it ended with loading my nvidia driver... which dosnt make sense.  I wish there was a way i could copy paste it on here, but before the nvidia driver a few lines up it said something about modprobe erroring.

---

### Post by Boktai1000 on 2008-05-25
Many formats later, I found the source of the problem.  It was my Guitar Hero X-Plorer, the Guitar that comes with Guitar Hero II.  I do not know why, but when I tried to install the Xbox 360 Wireless controller following the steps from the wiki with it unplugged, I got no Segmentation Fault error and I can now reboot just fine.  I hope this information will prove useful if anyone ever comes across the same problem I had.

---

