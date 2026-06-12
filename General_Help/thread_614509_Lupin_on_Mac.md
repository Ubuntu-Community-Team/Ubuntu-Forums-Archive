---
title: "Lupin on Mac"
date: 2007-11-16
forum: General Help
---

### Post by lqqkout4elfy on 2007-11-16
How do I get Lupin working on the Mac?

Further, I tried installing Wubi inside a Boot Camped Windows install, and it wouldn't boot to Ubuntu... sigh...

What can I do?? I would like to help if there IS a Mubi branch!

---

### Post by ago on 2007-11-19
Mubi branch has not been started yet, if you are willing to take care of that you are most welcome.
Lupin is now merged within the ISO.
It is possible to make it work on mac and I can give more detailed instructions.

---

### Post by lqqkout4elfy on 2007-11-24
I'm totally willing to test this out! Can you give me more detailed instructions?

---

### Post by ago on 2007-11-24
easiest way:

1) Install wubi 7.10 on windows, do not reboot windows
2) Copy the ubuntu folder onto the mac (the /ubuntu/diska/xyz.disk files are very large but completely empty so you can skip them and regenerate them on the mac using dd or equivalent)
3) Change the mac bootloader so that it boots off /ubuntu/install/boot/kernel|initrd using boot arguments as in /ubuntu/install/boot/grub/menu.lst
4) after installation have the bootloader point to /ubuntu/disks/boot using boot arguments as in /ubuntu/disks/boot/grub/menu.lst

A mac installer frontend would have to generate the same ubuntu folder structure as in point 1/2, and change the mac bootloader as in 3/4. Ideally the mac bootloader should chainload to grub. In windows, for instance, ntldr is used to launch grub4dos. Not sure if that is possible.

---

### Post by lqqkout4elfy on 2007-11-25
The default Mac boot loader only boots from separate partitions. So far #3 or #4, it seems like I will have to either do:

1. rEFIt
2. Grub 2 
3. elilo

This doesn't seem like it's very simple. But it also sounds like a nice little challenge to not mess with the partitions!!

---

### Post by ago on 2007-11-25
You can use any bootloader capable of loading the linux kernel, normally the main requirement is that the bootloader has to work within the filesystem used. There is no need to replace the existing bootloader if this is capable to chainloading to a second bootloader.

---

### Post by lqqkout4elfy on 2007-11-27
I have NO clue how to do chainloading with the Mac... any ideas??

---

### Post by ago on 2007-11-27
Chainloading means letting the mac bootloader start a different bootloader, it's like a pass-through. I know little about the mac myself, but most modern bootloaders can do it.

---

### Post by lqqkout4elfy on 2007-11-29
Oi the mac bootloader must not be very modern then!! I think to make this more flexible, I'll try out the grub2 bootloader. The process is simply:

```
bless -folder /etc/efi -file /etc/efi/grub2.efi
```

The trick is that you'll need to compile grub2 on a box other than Mac because Apple doesn't know how to package GCC.

---

### Post by step21 on 2009-01-22
O.k., I came across this myself so looked into it a little bit.
1. The problem is not so much that the mac bootloader is not "not modern" it's just limited (on purpose I assume).
This is for example why it's as good as impossible to boot non os x operating systems from an external drive. Also, due to the nature of the mac's efi firmware linux and windows (and everything else apart from mac os x) is provided with an emulated bios. This is the recommended and best way to run these systems, although there have been efi-thingys on some vista dvds and somebody hacked elilo to be more functional, (because elilo prob. runs, but has no access to video hardware acceleration otherwise) but this hack is very outdated from what I know, and only worked for mac minis. All of the above efi things do not currently work.
Also, afaik there is no way that the mac boot loader chain-loads another (non efi?) bootloader as long as its not on a seperate partition iirc, and I'm not sure about coexisting ... even refit plugs itself in after the normal firmware.
So one would have to use either refit, (but I'm not sure how that would work exactly, played around with the efi shell a bit, but I couldn't access anything I mounted somehow, and not sure about loopback support) or grub2, but i don't know the present status of this. In theory, all of what this needs could probably be done in efi, by the original firmware, but it is not. So if anyone with insight into wubi/grub/refit reads this ... maybe check my text for misunderstandings and reply.

---

### Post by step21 on 2009-01-22
O.k., on first glance grub2 seems like a viable option, [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook) however it seems that it would still require refit cause on [http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI) it says that using grub2 directly instead of refit is only tested on a mac mini. Even if I would get it running ( but I have only one machine atm and would like to keep it bootable ) it would not ensure that it runs on all intel macs.
That said, I don't mind running refit, but I'm not sure how the average mac user will feel about it Also maybe refit can be silenced/suppressed (creating the illusion of directly switching to grub2 ) but I'm not sure. Would this be a good idea?

---

### Post by step21 on 2009-01-24
O.k., I found a x86_64 grub2 efi version somewhere on the forums, cause so far I have not yet succeeded in compiling it on mac os x and like I saif no linux box to do this on atm.
I am able to select it (grub) in refit and after flashing something (the menu maybe?) for a very short period it returns me to the grub command line. There all commands basically work, but after some period the command line seems to freeze, so I couldn't get the long kernel line for wubi to enter before it froze, but changing the root device and ls -l etc. worked.
So, any ideas, why the menu doesn't show and it freezes?

---

### Post by lqqkout4elfy on 2009-05-27
Wow, I didn't think anyone else is on this case. Can you outline the steps to get this working?

I really would be interested in this! I have a few macs to test this out with... (an iMac and a Macbook Pro) 

I also happen to have a Time Capsule, so I don't mind blow away the computer for this!

---

### Post by step21 on 2009-05-27
@lqqkout4elfy what do you mean by "get this working"? if you mean wubi on os x (or mubi) it is not working currently, and I don't know from where you got the impression it is. This is mainly due to the fact that even if you say, copy the wubi files, linux doesn't have stable write support for hfs+ with journaling, which means it only could maybe work if users turned of journaling, which I think is not good. There also were some other issues ... if you have more than one mac, as seems to be the case, messing with partitions shouldn't be a problem for you. ^^

---

