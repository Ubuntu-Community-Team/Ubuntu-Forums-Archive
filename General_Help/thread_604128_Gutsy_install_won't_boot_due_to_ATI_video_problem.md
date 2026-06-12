---
title: "Gutsy install won't boot due to ATI video problem"
date: 2007-11-05
forum: General Help
---

### Post by Ziggy72 on 2007-11-05
If somebody can help I really, really would like a solution to this problem...

I have an AMD Athlon 64 X2 Dual Core Processor and an ATI  Radeon X1300/X1550 Series display adapter and I'm trying to dual boot Vista and Gutsy. Installation ol Gutsy using the Alternate CD proceeds normally and there are no problems with Grub, but when the system tries to boot into Gutsy, it fails and hangs very quickly with the message "Cannot detect this video mode". One person has suggested that I modify /boot/grub/menu.lst to delete splash. I've tried that, but it has made no difference. Whatever I do I just can't get into Gutsy. If I could, I could then install the right ATI drivers, but I can't even get to first base.

Please, please I need some really good help from geeky people on this. Suggestions gratefully accepted. Thanks

---

### Post by lamadredelsapo on 2007-11-07
I have a similar problem, but the difference is that Gutsy won't even boot from the live CD

---

### Post by TuxTwig on 2007-11-07
Boot into the Live CD/DVD, and then go to your xorg.conf file. Post the results here. It should be under /etc/X11/xorg.conf

Gutsy still has multiple bugs and this might be due to an unknown bug, try downloading the 6.06 LTS Live CD and trying from that if the Gutsy CD won't boot.

---

### Post by Ziggy72 on 2007-11-07
Gutsy won't boot into the live CD - the installation hangs...:(  so I've no way of getting at the xorg.conf file.

---

### Post by chadjohnson on 2007-11-11
Maybe you could use SystemRescueCD. Boot into that, mount the drive, and change the file.

If, for example, your drive is /dev/sda1,

mkdir /mnt/sda1
mount -t auto /dev/sda1 /mnt/sda1
nano /mnt/sda1/boot/grub/menu.lst

make changes, save, reboot (type reboot to reboot).

---

### Post by imbjr on 2007-11-11
Have a look here:

[http://ubuntuforums.org/showthread.php?t=580327](http://ubuntuforums.org/showthread.php?t=580327)

---

