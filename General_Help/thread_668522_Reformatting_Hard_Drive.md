---
title: "Reformatting Hard Drive"
date: 2008-01-15
forum: General Help
---

### Post by sundaymars on 2008-01-15
Hello...wow..I have not been here in a while...so I will introduce myself. My name is Timmy Gibson. I have a computer with a hard drive that is currently partitioned with Ubuntu on one partition, Windows 2000 on another, and a third partition is blank. I want to reformat it to where I have Ubuntu on one partition, and another linux distribution (i have not figured out which one) on another). I was wondering what do I need to do?

Also in a second question, which linux distribution should be the second one?

thank you all.

~timmy

---

### Post by JawsThemeSwimming428 on 2008-01-15
I am not sure about the partitioning but as far as another distro to use I would pick Mepis 7.0. I have been distro-hopping (somewhat) for awhile now and I love Mepis. I used Ubuntu for about two years (I still plan on having an install just to test with) and I liked it but it seemed to become unstable after awhile. I installed Mepis at the end of November and have not looked back. It is the closest Linux distro I have tried to everything just working. I would definitely check it out. It uses KDE by default and I was never a big fan of KDE but the way Mepis puts it together is amazing. What are you going to be using the distro for?

---

### Post by bodhi.zazen on 2008-01-15
Well, you should have no problems. You can share a swap partition between distros, so you need a  root or / partition for the new distro.

The limitation you may haev is you can only have 4 primary partitions. Beyond that you need an extended partition with subdivisions called logical partitions.

See this link for details : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Beyond that you should be good to go. Most distros will automatically configure Grub to recognize previous installations.

---

### Post by navd on 2008-01-15
Alright so.. First I will say try Gentoo Out. It is a little difficult but will get you prepared for the linux world. Second. You need to use a partition manager like gparted. Burn it to a cd and boot into it.

You want to delete all of your partitions except the one ubuntu is on. Now you can also try the command fixmbr in gparted(not sure if it has it) but the windows cd sure does in repair mode.

Last, boot into whatever new distro you want and set it to install in the unallocated space or whatever empty partition you made. If you need specifics just Holla.:)

---

### Post by sundaymars on 2008-01-15
> **JawsThemeSwimming428 said:**
> What are you going to be using the distro for?

I mainly want to try out other distributions. I love Ubuntu and that is why I want to keep it in one partition. I started using Ubuntu last year and I want to learn more about Linux. I find it to be a fascinating alternative to Windows.

Also I recently tried updating my version of Ubuntu and some kind of error came up, so I will just start all over. Also it will be exciting to be able to learn how to reformat a disk drive and partition it.

I am a web designer and unlike most people, I choose to hand code the XHTML and CSS. So it is only natural that I want to learn about the makeup of the computer hardware itself.

---

