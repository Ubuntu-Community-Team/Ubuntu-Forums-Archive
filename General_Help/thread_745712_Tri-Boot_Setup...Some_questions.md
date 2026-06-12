---
title: "Tri-Boot Setup...Some questions"
date: 2008-04-04
forum: General Help
---

### Post by parm289 on 2008-04-04
I've searched around here and the internet and haven't found answers for my specific setup, so here we go:

My current setup is:

One hard drive with two partitions - a 150gb Ubuntu partition and a 85gb XP partition.  I use GRUB as my bootloader (I know it sounds obvious, but I accidentally overwrote XP with ubuntu, and installing XP over Ubuntu is not fun).

What I want to do, depending on compatibility with my hardware setup (I will probably try this out in VMWare first to make sure), is tri-boot Leopard, Ubuntu, and XP.  Seems like the ultimate setup to me....drools....

Anyway, many of the guides on the web suggest starting with XP, then installing OSX and finally Ubuntu.  They recommend this to ensure GRUB maintains its status as the bootloader.  However, I don't see a problem installing OSX as the last OS because it is fairly simple to re-instate GRUB after (if) it has been erased.

I need some "Hackintosh"/Tri-booting experts to answer some questions:

1.  Does Leopard install a bootloader or will GRUB still be in place after the install?

2.  Will I be able to simply create a new partition and install OSX on it, or does it require a separate or empty hard drive?

3.  Will this affect my existing installations?

4.  If you're a Hackintosh/OSx86 person, let me know because I have some more questions about that which I couldn't garner the answers for online...

I know this isn't really the place to ask about OSX, however I trust the ubuntu community and some of my questions have to do with GRUB, etc.  Hopefully I provided enough information - if not, just ask for whatever you need to know.

P.S. If you want a list of my hardware, I'll see what I can do.

P.P.S.  I'm running on a PC - a custom built that is made for XP.

---

### Post by tamoneya on 2008-04-04
I have never done anything with hackintosh but i know a fair amount about multi-booting so i will answer as best i can.  First of all i agree with the xp, OSX, ubuntu install order

1. Leopard will install some sort of boot loader (it may be GRUB but im not sure) but since ubuntu is installed last it will over write the OSX bootloader.

2.  OSX will be fine on its own partition and does not require a separate drive

3.  The installations will not be affected.  OSX will only change your bootloader.

If for some reason the OSX messes your bootloader beyond repair you can always just pop in your ubuntu livecd and reinstall GRUB with that.  This is what i ended up doing since i install ubuntu and then xp.

---

### Post by parm289 on 2008-04-04
Thanks for your reply.

I suspect that OSX would install a new bootloader, but I'm not worried since I used the livecd to reinstall GRUB before.

I'm glad I can use a partition - my main concern is any special formatting, etc that is required.  I will look on the osx86 site for this info.

I also installed ubuntu then xp, so I imagine installing osx will not be much different from that process.  Thanks for your help.

---

