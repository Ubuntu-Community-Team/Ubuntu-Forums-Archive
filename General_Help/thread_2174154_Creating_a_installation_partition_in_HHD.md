---
title: "Creating a installation partition in HHD"
date: 2013-09-13
forum: General Help
---

### Post by chrsbrss2 on 2013-09-13
I'll start off by saying I'm a big time newbie, as such I've made several mistakes.

My big question is in two parts -

1.  Is it possible to make a pre-install DVD of Ubuntu with certain applications and software already installed (VLC, Opera web browser, Games, Movies, etc) preloaded onto a DVD.

2.  Is it possible to take said DVD and put it into a partition simalar to how Microsoft now has it's installation in the HHD - Access the partition on the HHD and re-install the OS so it's like a fresh install.

I've used the command line several times, but on a few occasions I've caused the OS to crash and not been able to save it so I just end up re-installing the OS.  I'm not bothered by doing it (Well, okay maybe a little, it is after all how you learn) but it would be nice to not need to go to the software center and re-install all the items that I have.  So...  if it is possible, how would I go about doing it?

---

### Post by Mephisto Pheles on 2013-09-13
1. is possible but very cumbersome to do. It won't save you any time and cause you a lot more headaches than just doing a normal install and using software center or using apt-get to install the programs you need/want.

2. you'd need a working running disk image for that, meaning it would have to be installed first, so that's somthing else than just an "extended" install DVD. (unless I misunderstood you)

---

### Post by mastablasta on 2013-09-13
1. yes, use system imager (or remastersys for older editions) to do it.:[http://system-imaging.blogspot.com/](http://system-imaging.blogspot.com/)

2. it would be much easier to simply create a backup image of the system you can use clonezila or redobackup for that. then if you mess somethign up you just restore the image. best done with external hard disk, different hard disk (inside mashcine) or USB stick. 

and yes, you could install redobackup or simialr to that partition, leave enough space for the system image and then boot from that partition to restore the image. this would mean that you would need grub to stay good. in general though it's just easier to simply just use a live USB external disk or something like that. that way grub will work in case of its corruption on your maschine.

---

### Post by chrsbrss2 on 2013-09-19
Thanks, your probably right about the USB or DVD instead.  Thanks for the responses and the directions.

Chris

---

### Post by sudodus on 2013-09-19
If you want to install (or copy) your already tweaked system to a whole drive, you can use the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") to make a tarball of your system and then expand a system from the tarball to the other drive. If you have more complicated setups (dual boot etc) you can do it manually with the same method, to make and use tarball(s), and afterwards install the bootloader.

This method is an alternative to remasterys.

---

