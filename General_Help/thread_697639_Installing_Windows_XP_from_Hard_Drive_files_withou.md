---
title: "Installing Windows XP from Hard Drive files without CD"
date: 2008-02-15
forum: General Help
---

### Post by tim237 on 2008-02-15
Hi guys

I'm running Ubuntu 7.10 alone on my computer, no partitions no dual boot no nothing. It's all been going until recently I got given Civ 4 Complete and Libronix, neither of which run properly under WINE or Cedega (at least for me, other people seem to have got Civ 4 Complete running on WINE but I've followed their instructions to no avail). 

So I need somehow to get Windows going. I heard about virtual desktop software like VMWare, but then realised I need my Windows CD. Unfortunately that's lost. However I do have saved on my external hard drive my old Windows XP installation.

So here's my far fetched plan: is it possible to use the XP files I have on my external hard drive to get windows running any how so as to get those programmes running?

It's probably impossible, but worth an ask.

Thanks anyway
Tim

---

### Post by Het Irv on 2008-02-15
I have not researched it much, but I have heard that VMWare has a converter that will take an existing partion and make it a Virtual Machine.  That is all I know about it.  I will try to take a look at it later.

---

### Post by Herman on 2008-02-15
You can use files on your hard disk to make a Windows Live CD, and you can make your own Windows Install CD to re-install Windows with. 
There are conditions, but it is supposed to be legal if you stick to the rules, details are at 
[Bart's Preinstalled Environment (BartPE)  bootable live windows CD/DVD]("http://www.google.com.au/url?sa=t&ct=res&cd=2&url=http%3A%2F%2Fwww.nu2.nu%2Fpebuilder%2F&ei=Yti1R4mZOovSpgSt_binDQ&usg=AFQjCNH8QKJT4S2lCuG_68Ru1hJI51affA&sig2=fvtJ9M6i3GEw1fvNoUpThw")

Regards, Herman :)

---

### Post by BobLand on 2008-02-15
Something I do is attach the Windows drive to the computer then change the bios before you boot up.  In other words, XP is on my IDE drive, Ubuntu is on my SATA.  If I want to boot XP I restart and hit F2 to go to the bios.  I change the boot priority so the Windows drive boots first.  Likewise, change it back to boot Ubuntu.

It's a little longer version of dual-boot but I don't have to do deal with the mess when Windows crashes and messes up the boot area.  I did this to copy off archives from Windows to Ubuntu.  I have no intention of using Windows for anything other then the occasional game so I'd like it as far away as possible from Linux.

Another thing to try is google Acronis TrueImage.  They used to give a trial.  It's like Ghost but much safer and much faster.  You could transfer your Windows to anywhere.  If you have to buy it, it would still be cheaper then buying Windows new.

bobland

---

