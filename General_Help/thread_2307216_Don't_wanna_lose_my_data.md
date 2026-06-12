---
title: "Don't wanna lose my data"
date: 2015-12-22
forum: General Help
---

### Post by avago621 on 2015-12-22
I recently installed on a flash drive an Ubuntu 15.04 live CD persistent and love it is there any way I can install it to my hard drive with all my downloads settings apps and customizations intact

---

### Post by Vladlenin5000 on 2015-12-23
Hi and welcome.

You can use the same media to install. Then you can add the customizations. There isn't a simple way to keep what you already did in the live session (with persistence) and regardless of the difficulty it's absolutely NOT recommended.
If you need help with the installation process please ask and, of course, provide relevant details about the specs of the target machine and whether or not you intend to dual boot with another OS.

---

### Post by Bucky Ball on 2015-12-23
Welcome. Yes, there is a simple way. :) Well, a few ways, and easy enough but time consuming perhaps. If there is a problem because of the USB being a persistence install, sure someone will leap in soon enough ...

Having said that, a brief peek shows me [this]("http://ubuntuforums.org/showthread.php?t=2093823") and [this]("http://askubuntu.com/questions/380066/how-to-clone-ubuntu-installed-on-usb-stick-onto-pc-hdd"). Doesn't seem to be an issue. 

Clone the USB to another external device (or an internal drive that is not the one you are going to install Ubuntu to). Then clone it to the target partition on the internal hard drive. That's it. You will then need to mess about getting grub to boot the install, but that shouldn't be an issue. Boot Repair should take care of that. 

You can use [Clonezilla]("http://clonezilla.org/") or [fsarchiver]("http://www.fsarchiver.org/QuickStart#How_to_extract_filesystems_from_an_archive") (there are others). With Clonezilla you would clone the USB (source) to another drive partition (target) then the target partition become the source and you clone it back to the new target (the internal drive partition where you want Ubuntu). 

fsarchiver is slightly different. It makes an 'archive' which you then 'restore' to the internal hard drive. 

For Clonezilla, you make a Clonezilla USB and boot from that to do the work. With fsarchiver you can download [SystemRescueCD]("http://www.sysresccd.org/SystemRescueCd_Homepage"), create a USB, boot from that. It includes fsarchiver, testdisk, photorec, gparted and a bunch of useful things you want around anyhow (very useful). 

You can also install fsarchiver directly from the repositories and archive the system you are running! Some folk advise against this (so have a back up of you data, but have one regardless before doing anything), but I did it this way just recently and am typing to you from an identical copy of my Ubuntu on my hard drive which is now on my new SSD. :)

Clonezilla or fsarchiver will create an identical copy of your partition (or in the case of Clonezilla, a whole disk). fsarchiver can archive two partitions to one archive. And you can restore whichever you want. Just keep notes so you know what you've archived where! Important.

PS: You can also use dd to clone an identical copy of anything to anywhere in one hit, BUT ... approach with caution. It is unforgiving, takes no prisoners, and if you set the wrong target, there is no going back. It will obliterate anything on the partition prior to copying and gives no warning and no 'are you sure?' opt-outs. :) Very efficient, though, for the game.

---

