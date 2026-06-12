---
title: "dual boot"
date: 2008-01-05
forum: General Help
---

### Post by ladybluballs on 2008-01-05
hi after a bad winxp crash that ruined my win hard drive,I tried to quickly learn linux but could not do things with linux that I needed to do  with windows utilities.I replaced the hard drive and installed winxp I have ubuntu on another hard drive not connected to computer at this time,I have many things loaded I dont want to lose and want to learn linux over time now to my question what do I need to do to get my already installed ubuntu disk to dual boot with my winxp install without reinstalling the unbuntu from scratch  thanks

---

### Post by ladybluballs on 2008-01-07
well I guess I have not ask my question correctly as I have not got any response,I have spent all day doing research and attempting to get my ubuntu hard drive to dual boot but for some reason my winxp drive wont boot with the ubuntu plugged in, I have it set as slave but the master wont even boot windows with slave hd connected

---

### Post by p_quarles on 2008-01-07
You'll need to install the GRUB bootloader on the HDD you want to boot from (probably the first disk -- the one with XP). This can be done using the Ubuntu live CD:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Bllasae on 2008-01-07
Well, didn't you say that your Windows XP hard drive crashed? Did you install Windows XP on it again after the crash?

---

### Post by ladybluballs on 2008-01-07
> **Bllasae said:**
> Well, didn't you say that your Windows XP hard drive crashed? Did you install Windows XP on it again after the crash?

no I could not clean it up so I replaced it new and installed xp back on new hdd,xp is working perfect by itself

---

### Post by ladybluballs on 2008-01-07
> **p_quarles said:**
> You'll need to install the GRUB bootloader on the HDD you want to boot from (probably the first disk -- the one with XP). This can be done using the Ubuntu live CD:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

thank you  will try this tomorrow

---

### Post by logos34 on 2008-01-07
> **ladybluballs said:**
> thank you  will try this tomorrow

Don't forget to add a windows entry to /boot/grub/menu.lst so you can boot XP.  Or does it already have one?

---

### Post by p_quarles on 2008-01-07
> **logos34 said:**
> Don't forget to add a windows entry to /boot/grub/menu.lst so you can boot XP.  Or does it already have one?
Reinstalling GRUB should -- unless something goes horribly wrong -- take care of that automatically.

---

### Post by ladybluballs on 2008-01-08
> **p_quarles said:**
> You'll need to install the GRUB bootloader on the HDD you want to boot from (probably the first disk -- the one with XP). This can be done using the Ubuntu live CD:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I did not get the grub boot to reinstall,the live cd will only boot all the way up with the ububtu drive unhooked and when I try to set up the grub loader I get error file or directory not found,when I try to boot live cd with cables hooked to ubuntu hard drive it tries to boot and stops with message [can't access tty: job control turned off. also its may not be  related but a big flash flew out the back of my computer,I discovered it had blown the power supply I had a extra one on hand and back up to try more suggestions on the boot problem

---

### Post by ladybluballs on 2008-01-09
> **ladybluballs said:**
> I did not get the grub boot to reinstall,the live cd will only boot all the way up with the ububtu drive unhooked and when I try to set up the grub loader I get error file or directory not found,when I try to boot live cd with cables hooked to ubuntu hard drive it tries to boot and stops with message [can't access tty: job control turned off. also its may not be  related but a big flash flew out the back of my computer,I discovered it had blown the power supply I had a extra one on hand and back up to try more suggestions on the boot problem

ok it looks like I did not ask the proper question again so I will try a different way to get ububtu back up,are there a way to I can hook the ubuntu drive up by itself and completely clean up the drive and then hook the drive back to winxp drive and do a reinstall of ubuntu on the drive I just cleaned,I think I can do a clean reinstall ok.

---

### Post by ladybluballs on 2008-01-09
ok this seems like it should be a simple problem, I have winxp on master hdd and its working fine,I can unhook cables and put the ide cables on the ubuntu hdd after setting jumpers to master and the ubuntu boots up and works fine,when I set the jumpers back to slave on the ubuntu hdd and hook ide cables back on master hdd that has winxp it will not boot it says os not found I have to dissconect the ubuntu slave and shut down power to computer and when I power back up I have windows back

---

### Post by p_quarles on 2008-01-09
Well, the situation with the second hard drive doesn't seem simple to me. Without being able to see it, I'd have a hard time figuring out whether this is a hardware issue or a bootloader issue. 

Anyway, this isn't going to work unless you're able to install GRUB with both drives connected. The fact that the installed OSes, as well as the Ubuntu live CD, all fail when both drives are connected is odd to say the least. I could suggest trying the Super GRUB Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Also, I found a bunch of information about different ways of dual-booting two hdds here:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by ladybluballs on 2008-01-09
> **p_quarles said:**
> Well, the situation with the second hard drive doesn't seem simple to me. Without being able to see it, I'd have a hard time figuring out whether this is a hardware issue or a bootloader issue. 

Anyway, this isn't going to work unless you're able to install GRUB with both drives connected. The fact that the installed OSes, as well as the Ubuntu live CD, all fail when both drives are connected is odd to say the least. I could suggest trying the Super GRUB Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Also, I found a bunch of information about different ways of dual-booting two hdds here:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

thanks I also have suse 10.2 that I wanted to try,if I install suse on the same hdd with windows would that not give me the grub boot and reconnect the ubuntu hdd would I have all 3 os bootable

---

### Post by p_quarles on 2008-01-09
Honestly, I don't think there's much to be gained by dual-booting (err, tripe booting) Linuxes. It's likely to cause more headaches, and isn't the easiest way to test out different distros. You may want to look into Virtualbox or VMWare, both of which will allow you to install further operating systems inside of a virtual machine. 

You'll need a decent amount of memory (~1 gig) to be able to do this effectively, but it's very cool. I use it to run Windows (rather than dual-booting) and test out different distros of Linux and BSD.

---

### Post by ladybluballs on 2008-01-09
> **p_quarles said:**
> Honestly, I don't think there's much to be gained by dual-booting (err, tripe booting) Linuxes. It's likely to cause more headaches, and isn't the easiest way to test out different distros. You may want to look into Virtualbox or VMWare, both of which will allow you to install further operating systems inside of a virtual machine. 

You'll need a decent amount of memory (~1 gig) to be able to do this effectively, but it's very cool. I use it to run Windows (rather than dual-booting) and test out different distros of Linux and BSD.

I may look into that I have 1gig ram,now back to the dual hdds I looked in bios and both hdd calls themselfs hdd0 master/hdd0slave I thing my problem may be here,could it be both are trying to be master maybe I dont have the jumpers set right?

---

### Post by p_quarles on 2008-01-09
> **ladybluballs said:**
> I may look into that I have 1gig ram,now back to the dual hdds I looked in bios and both hdd calls themselfs hdd0 master/hdd0slave I thing my problem may be here,could it be both are trying to be master maybe I dont have the jumpers set right?
Cable connections was my thought. Unfortunately, I don't know of any Bash commands that would help with that. ;)

---

