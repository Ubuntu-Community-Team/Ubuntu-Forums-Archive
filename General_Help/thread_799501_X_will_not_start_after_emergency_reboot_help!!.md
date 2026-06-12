---
title: "X will not start after emergency reboot help!!"
date: 2008-05-19
forum: General Help
---

### Post by bergqvistjl on 2008-05-19
Hi, i am fairly new to linux. Last night my system froze on the desktop (mythbuntu 8.04 with standard gnome desktop installed via mythbuntu control centre) so i rebooted via the reset button. When it booted up, i got a message saying that the X server didnt start and something about a GDI (ill try and get proper message on here soon) it then presented me with a command line login prompt which i was able to log into, unfortunally i didnt know any commands that could help me. Any ideas? perhaps how to schedule a disk check + repair? Otherwise im going to reformat it tonight. its a bit annoying, ud think  an os like ubuntu wud be able to handle an unexpected reboot.

---

### Post by sdennie on 2008-05-19
Have you ever rebooted the machine before?  Did you recently install nvidia video drivers after downloading them from the nvidia website?

---

### Post by bergqvistjl on 2008-05-19
yh ive rebooted it fine before. ive been using it for about a week without a hitch. what i was trying to do was disable compiz (which ive done before a few days ago) cos it makes my games and videos flicker. i prob should have waited for the hang to resolve itself oh well. and i was using the proprietry ati drivers with no problem at all. i presume summat on the hdds got corrupted when i rebooted it while it was still doing stuff.

---

### Post by russo.mic on 2008-05-19
> **bergqvistjl said:**
> yh ive rebooted it fine before. ive been using it for about a week without a hitch. what i was trying to do was disable compiz (which ive done before a few days ago) cos it makes my games and videos flicker. i prob should have waited for the hang to resolve itself oh well. and i was using the proprietry ati drivers with no problem at all. i presume summat on the hdds got corrupted when i rebooted it while it was still doing stuff.

Just had something like this happen to me.  I don't think you can do this to previous versions of ubuntu installer, but you CAN reinstall ubuntu to the partition or drive without formating.  This means you could reinstall without losing anything in /home if you didn't make it a seprate partition.  

before that, grab a knoppix disk, or ubuntu installer disk, or whatever and run a fsck on the disk in question, and cross your fingers.  make sure before you run the command you don't mount the drive.  it would be something like fsck /dev/sda1, or /dev/hda1, or whatever depending on what your drive and partition are called.  a  sudo fdisk -l will help you figure that out.

Russo

---

### Post by bergqvistjl on 2008-05-19
ok ill try  fdisk (cos my mythbuntu is heavily customised and ive got the gnome desktop over the top of it i think ill do a full format. can fdisk fix corrupt sectors and stuff, like window's checkdisk. and what if it hangs again so i have to do a reboot. i dont want to re-install ubuntu everytime lol!

---

### Post by bergqvistjl on 2008-05-19
Thanks russo for the fsck tip its fixed!!!!!!

---

