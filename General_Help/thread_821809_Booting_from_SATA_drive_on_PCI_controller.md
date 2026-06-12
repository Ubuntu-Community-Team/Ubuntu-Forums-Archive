---
title: "Booting from SATA drive on PCI controller"
date: 2008-06-07
forum: General Help
---

### Post by garethsimpsonuk on 2008-06-07
Hello ppl I really hope someone can help me!

I've been sat in the server forum all day while trying to sort this out and i'm not getting much help cos it's dead so here goes...

Basically I bought a SATA pci card for my PATA based mobo. I can install fine to the drive on the pci card but can't boot from it.

I have an option to reaarrange boot priority in bios and i've put 'add in card' first, still no joy.

Basically I think I need to flash my bios but don't know what mobo it is or what program to use to flash.

I come across this which seems to be a workaround.
[I]
That's the bad news. The good news is that once the linux kernel loads, it kisses those bios limitations goodbye. From that point on, all hardware detection is controlled by the kernel. The kernel that's loaded at boot time resides in /boot. Accordingly, you should be able to install mandriva by creating a small /boot partition on your IDE drive, 200MB should be more than enough, and install everything else on your sata drive. You would also need to direct the installation routine to install the bootloader to the IDE drive. Then at boot time, your bios would see the bootloader on the ide drive and load it and the bootloader would see the kernel in /boot and load, after which the rest of your installation would be seen on the sata drive.[/I]

I just don't know how to modify the grub settings to point to the SATA drive. Can someone guide me?

I'd prefer to have it boot straight from the sata and it's strange that it doesn't as it's detected in the post boot screen.

So if anyone think they can help or knows who can please please let me know!
Thanks guys

edit: [original post]("http://ubuntuforums.org/showthread.php?t=821423")

---

### Post by logos34 on 2008-06-07
boot from the live cd, post the output/contents of **sudo fdisk -l** and **/boot/grub/menu.lst** (to access the latter you'll need to mount root partition)

Sounds like you've tried just about everything.  You came closest to booting the first time around--grub apparently was written to the ide disk MBR, but it can't seem to access menu.lst on the sata drive--either because it's pointing to the wrong partition or something about the pci card is preventing it.

---

### Post by garethsimpsonuk on 2008-06-08
yea thanx logos it was driving me mad last night! i don't know why but know when I boot up, during post I see

Verifying DMI Pool Data....
Boot from CD:..
|B`e-$|B`e-$_ 

I've tried to copy it exactly but there's some strange symbols that aren't on the keboard. Such as the first vertical dash ( which is again repeated before the B )has a kinda small line coming out of the left in the middle so it's a bit like this -| but they connect and he horizontal line is much shorter. The underscore isn't really an underscore more like a cursor as it's blinking and the accent is directly over the e.

Anyway whatever it is it's hard to search for the problem when I can't even copy the display so I'm stumped. I reset the bios and it's still there, and disabled anything and eveything in different combnations and still no luck. I even disconnected the CD drive altogether. ( I think I recieved a boot disk error that time )
Why is it trying to boot from CD and what is that strange set of characters. It's like it's waiting for something due to the blinking cursor but never gets anywhere.

Anyway anyone got any ideas for a very very annoyed ( with myself ) ubuntu user?

Thanks

oh and thanx 4 ur post logos, I expect you've gone now though

---

### Post by garethsimpsonuk on 2008-06-08
bump

---

### Post by garethsimpsonuk on 2008-06-08
bump

---

