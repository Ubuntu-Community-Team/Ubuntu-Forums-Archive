---
title: "minimal bash-like on GRUB ubuntu 11.04"
date: 2012-12-27
forum: General Help
---

### Post by caiorrs on 2012-12-27
hey guys, I'm new here, and I have a problem.

some time ago my grub crashed, so I tried to fix it using the regular solution, restore the grub from sda1 using a live cd.

but then i accepted to dont fix it and I ran the win 7 cd to fix the MBR and use the windows, BUT NOW I want to fix it again.

I tried again to use the regular solve but it didnt work. When I started my pc I saw this error:

GNU GRUB version 2.00-7ubuntu11

Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions.

grub>_

and then I need to write some command...

I have searched in a lot of sites and the people said that they gave it up and formatted their disks, I want to fix it, so, if someone knows how to do it I apreciate

thanks for helping =D

I have the ubuntu 12.10 in my pen drive (live-usb)

---

### Post by dino99 on 2012-12-27
if your ubuntu is installed on hd, then from a livecd/liveusb you can easily reinstall it by running:

sudo grub-install /dev/sda
sudo update-grub

but if your ubuntu & grub are on the stick, then you need to know its id:

sudo blkid

then do the commands above but with /dev/sd? where ? is the good letter for your stick (given by the blkid command)

note: you also can install grub on sda, even if ubuntu is on the stick (or install on both, but then one is the master and other the slave, meaning that only the master can update the grub menu)

---

### Post by caiorrs on 2012-12-27
with stick you mean the liveusb? and yes, it is installed on my notebook's HD.
one more question, i have 2 partitions with the ubuntu one is the sda1 with 40Gb to ubuntu(ext4) and a sda2 with 40gb for documents (ext4) and a 4gb for swap memory. how can I know which one (sda1 or sda2) I have installed my ubuntu and in which of them I install the grub?

thanks

---

### Post by caiorrs on 2012-12-27
Im using the live usb now

terminal

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

error... know how to fix?

thanks and sorry about lots of posts =S

---

### Post by catalin.vasilescu on 2012-12-27
df -P /file/goes/here | tail -1 | cut -d' ' -f 1
or df -h 
or fdisk -l

---

### Post by catalin.vasilescu on 2012-12-27
@* Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.*  Follow the manual over [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") .

---

### Post by caiorrs on 2012-12-27
hey man, thanks, you helped me to fix it, it worked

really thank you

how do I change the name of the topic to solved?

ttttttthhhhhhhaaaaaaaaaaaaaannnnnnnnnkkkkkssssss

=D

---

