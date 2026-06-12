---
title: "Can I install an Acronis image to a drive that is using AHCI?"
date: 2014-11-05
forum: General Help
---

### Post by J Tinsby on 2014-11-05
I recently got an SSD and changed my BIOS to AHCI and installed Win 7. I want to put my Ubuntu on that drive as well, but the Acronis image of Ubuntu, wasn't made with AHCI enabled. Can I still install to ext4 partitions on my SSD or must I start over with everything and install Linux to the SSD from scratch? If that's the case I may just put Mint on the SSD instead.

Thanks to all in advance,

J T

---

### Post by rbmorse on 2014-11-05
AHCI is a controller protocol and won't have any effect on the Acronis Image.  

Where you're going to have problems doesn't have any relation to AHCI/IDE -- it will be getting the restored Ubuntu partition to boot the system. You'll want to have the Boot Repair Disk: 

[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

available to do the required GRUB fixups after you use Acronis to restore the Ubuntu partition image to the new target drive.

---

### Post by J Tinsby on 2014-11-06
> **rbmorse said:**
> AHCI is a controller protocol and won't have any effect on the Acronis Image.  

Where you're going to have problems doesn't have any relation to AHCI/IDE -- it will be getting the restored Ubuntu partition to boot the system. You'll want to have the Boot Repair Disk: 

[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

available to do the required GRUB fixups after you use Acronis to restore the Ubuntu partition image to the new target drive.

Hi rbmorse,

Thanks for the reply. Yes I realize it's not going to boot, I already have the Boot Repair Disc but don't really want to use it. My Ubuntu system was made with Grub on the / partition not on the MBR. If I use the repair disk it will mess with the MBR of Win 7 and be in control of both 7 and Ubuntu. That's what puzzles me about the whole thing, Ubuntu was put on the 3rd of three partitions, XP, 7, & Ubuntu. I know that the boot information for 7 was put on XP so if XP is gone I would have to repair 7. But if I just put an Ubuntu image onto my new SSD that contains Grub, I get a "Grub rescue" message and it won't go any further. I know this because I tried it with a spare mechanical HD. I can see the files are there in the / partition, including Grub folder. But I don't know enough about Linux to repair it without using that disc. I don't want Grub in charge of booting 7 and Ubuntu. I guess I'll have to start fresh with everything related to Ubuntu or as I opined I may install Mint instead. 

If you have any solutions please advise me, I am new to Linux and don't have the experience a lot of you guys in here do. But I think it could be fixed if there was a way to re-install Grub to the image, even though it's there already.

Thank you,

J T

---

### Post by rbmorse on 2014-11-06
So...you're trying to set up a machine to triple-boot, and use a/the Windows' boot loader to manage the boot selection. 

The thing is that GRUB2 was designed expressly with this kind of thing in mind whereas the Windows Boot Loader (BCD) assumes that Windows...and only one flavor of Windows at that...is the only O/S on the machine. 

I suppose that it is possible to do what you want...it's beyond my ken, but doubtlessly someone else here can help. 

You'll need something like EasyBCD (Google for it) and while I've made that work with two operating systems on a machine I never quite got it right when trying to manage three. Not saying it can't be done, I just was never able to do it. The fault, no doubt, being mine. 

Good luck.

---

### Post by J Tinsby on 2014-11-06
well "yes" and "no" :D

I have an SSD with Win 7 with AHCI enabled, tho' I desperately wanted to just throw an Acronis image on there... I was advised by the sevenforum to do complete re-install so I did, and am still doing it. I also allowed the installer to make the System Reserved partition, just in case.

The old HD was where I had my triple boot system with XPired, 7, & Ubuntu and EasyBCD. EasyBCD was installed in XP to boot 7 and I simply pointed it to the partition where Ubuntu is located.
An image was made that contains all 3 OS's plus the MBR. I have successfully restored a backup of XP and 7 to an older drive, but I can't get Ubuntu to boot, as I say I get the Grub Rescue message with a flashing cursor. I don't know how to respond to that message IE:is it asking me to re-install Grub or can't it find it? I see a Grub folder that seems to contain the Grub files, but again I am NO expert with Linux, still learning and always will be but I DO like the OS!

Note that I currently have only Win 7 on my SSD and there is no instance of Ubuntu or Mint on it anywhere. I'd like to find a way to put my image of Ubuntu on that drive onto 2 ext4 partitions that I would make prior to installing the image. But I'm not sure it's going to work, but very sure that it won't boot right away. Again, trying to avoid that Boot Rescue Disc because I know what it does, yes it will make Ubuntu boot but it puts Grub everywhere and I don't want/like that.

Thanks for your response and honesty :D EasyBCD has always worked well for me, maybe since it needs to be installed in Win 7 to allow the Grub bootloader to work, as it did in XP.

Imho it's too bad there isn't a disc that would just allow Grub to be repaired without having it take over the whole system.

J T

---

### Post by kurt18947 on 2014-11-06
> **rbmorse said:**
> So...you're trying to set up a machine to triple-boot, and use a/the Windows' boot loader to manage the boot selection. 

**The thing is that GRUB2 was designed expressly with this kind of thing in mind whereas the Windows Boot Loader (BCD) assumes that Windows...and only one flavor of Windows at that...is the only O/S on the machine. **

I suppose that it is possible to do what you want...it's beyond my ken, but doubtlessly someone else here can help. 

You'll need something like EasyBCD (Google for it) and while I've made that work with two operating systems on a machine I never quite got it right when trying to manage three. Not saying it can't be done, I just was never able to do it. The fault, no doubt, being mine. 

Good luck.

Precisely.  I have a 3rd party utility what works very well for booting multiple O.S. independent of each other - or not as I choose.  The problem is that it only works on MBR/'conventional' system BIOS, it doesn't do U.E.F.I. so I was forced to use GRUB for a new system with a 'hybrid' BIOS. I don't see where GRUB is causing a problem.  I did have one situation where I thought GRUB broke - it wouldn't boot Windows 7 - but I suspect that was due to upgrading the motherboard BIOS from ver. 1.xxxx to ver. 2.xxx from the manufacturer.  Reinstalling Win 7 fixed the problem.  It may have been that the BIOS upgrade broke the Windows boot code, not GRUB because Ubuntu continued to boot normally.  Since that hiccup, booting has worked as expected using GRUB with both O.S.s for a few months now.  The 3rd party software I use on machines with non-U.E.F.I. BIOSes is bootitbm  from Terabyteunlimited. It gets around the 4 primary partition limit as well as booting multiple OSs.

If you have a choice in the matter, install Windows first then any *nix O.S.s.  I also used grub-customizer to make GRUB look and work more like I wanted.  I initially had problems with grub-customizer -- it didn't do anything.  I figured out that after I made the desired changes I had to write the changes to the disk.  Once I figured that out, I was able to make GRUB work as I wanted.

---

