---
title: "booting problems with laptop"
date: 2014-05-09
forum: General Help
---

### Post by facedepet23 on 2014-05-09
Hi! I have a problem installing ubuntu and i hope someone can help.

I had no problem with linux installations so far but i have a problem with one in particular a toshiba satellite laptop with an amd64 with vista (my mom's computer).
The problem is when i tried to make a usb boot loader with lili, i installed the boot not on the usb stick but on the vista bootloader. Naturally vista doesn't boot anymore but the ubuntu installation instead, but everything crashes and i wasn't able to install ubuntu and now i get stuck on a screen upon boot indicating a kernel panic. I made another usb boot loader with ubuntu 12.04 lts 64, it boot succesfully but i get stuck in the ubuntu loading screen (even after a night it's still there). I tried to use a windows xp cd to format the hdd but i get a blue screen of death upon installation (firts time i see that). 

Now i wonder what i should do i may have messed up my mom's laptop i can't install any os. Is there a way to format everything without any os (doesn't seems to have any way to do it on the bios). Should i try to get my hands on a vista repair cd? I will try to make an usb with ubuntu 14.04 instead and see what happens. Someone have any suggestions?

---

### Post by dragonfly41 on 2014-05-09
Boot-repair should help you out of this hole ..

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by facedepet23 on 2014-05-09
Thanks i think it will work i'll try tonight. Do you think i can use the ubuntu startup disk creator and put it on an usb stick?

---

### Post by facedepet23 on 2014-05-10
Well no luck. I made a bootable usb with this utillity, on startup, if i choose the boot repair option it just stalls like if i try to install ubuntu. Then, I took the option 64bit session. Lots of words and commands start to appear then it freeze. But the last thing i read before it stalls: asking for cache data failed. I Know the cache is related to virtual memory and ram so could it be that there's a problem with the hdd or a ram stick??

---

### Post by oldfred on 2014-05-11
An XP disk will not fix a Vista install and may make it worse. XP uses the ntldr where Vista & later use bootmgr. That is in the PBR or partition boot sector and usually is set with chkdsk.

You need to either get a Vista or newer Windows repair CD or flash drive to boot to fix Windows or get a Linux live disk to boot to add Boot-Repair so we can really suggest the best solution.

What video card/chip? Some systems need nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

