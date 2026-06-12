---
title: "External Hard Drive GRUB Error"
date: 2007-05-14
forum: General Help
---

### Post by magcius on 2007-05-14
Hello, I am a complete beginner at Ubuntu, so please bear with me.

I want this USB external hard drive, a WDC 250GB (branded Acomdata), to become my "portable office", as I switch between three or four computers very frequently. To be able to just plug this into a computer, modify some BIOS boot settings and start working, is very important to me.

I have installed Ubuntu 7.04 Feisty Fawn on an external hard drive using the Live CD. I followed pretty much all the in the installer, only at the last step (I believe it is when you are reviewing your install options), I clicked "Advanced..." and set the GRUB setting (I forget what it is now) to (hd2), my external hard drive.

My problem is that when I boot up the computer (ASUS motherboard), and when it boots from the USB external, I get a full screen of **"GRUB GRUB GRUB GRUB GRUB.."** I have looked around to see what the cause of this is, and the result is that this was an Auto-Detect issue. However, I believe that with an external hard drive, this is not the case.

My BIOS has two settings for a USB drive under the Removable Devices category:
[LIST]
[*]**USB-FDD**
[*]**USB-ZIP**
[/LIST]

I believe this is all I have done. If you want my menu.lst file or devices.map, just please ask.

---

### Post by m.musashi on 2007-05-14
How do you boot from the USB drive? Do you go into the bios and point to it? I've never messed with booting off USB so this may not be the same case; however, if you have one drive set as the boot drive, install ubuntu and put grub on a second drive and then use the bios to make the second drive the first drive you will probably get some errors. The reason is because the drive names changed from say hd2 to hd0 when you made it the boot drive but it's still looking for files on hd2.

While that may be the cause of your problem, I'm not sure of a solution. I think you will want to rename the external drive as hd0 and then each time you boot from it it will be hd0.

Post your menu.lst and device map and I'll see if I see anything obvious.

---

### Post by magcius on 2007-05-14
[QUOTE=m.musashi]Post your menu.lst and device map and I'll see if I see anything obvious.[/QUOTE]

[QUOTE=device.map]
(hd0)   /dev/hda   # My windows drive
(hd1)   /dev/hdb   # My external backup, internal
(hd2)   /dev/sda   # This is my external, the setup on this computer
[/QUOTE]

[QUOTE=menu.lst]
timeout         10

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=A4787B87787B56D0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=A4787B87787B56D0 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
[/QUOTE]

Sorry if I was not being clear, I set my boot order in the BIOS to load "USB-FDD" under "Removable Devices"

I want to be able to load this on any computer, plug it in and work.

The problem is, that, whenever I try to boot off the external, before the GUI bootloader comes up, something prints "GRUB GRUB GRUB GRUB" recursively, infinitely, and repetitively.

---

### Post by m.musashi on 2007-05-14
I'm thinking the problem is related to the grub loader not finding the stage 1 or stage 1.5 files. You might need to boot a live CD and set up grub again. However, I don't know what will happen if it's on a usb drive. Normally you setup grub on hd0 but I'd be willing to bet if you boot a live CD that the usb won't be hd0. There are some how-tos out there for setting up ubuntu on a usb drive. You might try and find one of those and see if it has any tips on setting up grub.

I have to bolt, but I'll be back in a bit. I'll look around and see what I can find.

EDIT: okay, I found [this thread](http://ubuntuforums.org/showthread.php?t=80811) that talks about installing on a usb drive. It's a bit old but I think it should give you the info you need. There is some info at the bottom related to reinstalling grub. However, since you want to be able to boot this drive from different computers you will probably want to install grub as though it were on hd0. That way, any computer you connect to and boot from the usb drive should work since it will always be hd0 in that scenerio (unless some hardware acts differently with usb as a boot drive).

One more thing to consider. If the various computers are quite different (i.e. different video cards, sound, networking) then this may not work well. I don't have any experience migrating an OS but I think it is going to be set up for the hardware it sees on install. It may recognize changes but if you have an nvidia card on one and an ati on another I think that will cause problems.

---

### Post by magcius on 2007-05-15
[QUOTE=m.musashi]**However, since you want to be able to boot this drive from different computers you will probably want to install grub as though it were on hd0. That way, any computer you connect to and boot from the usb drive should work since it will always be hd0 in that scenerio (unless some hardware acts differently with usb as a boot drive).**[/QUOTE]

I thought that I did install install my USB drive as hd0, as my menu.lst says so. Also, this looks like a BIOS setting, as there is nothing on the screen besides a repetitive:
[QUOTE=BOOT]
GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB....
[/QUOTE]

**If I don't reboot the computer, it will keep on printing that message over and over.**

---

### Post by magcius on 2007-05-15
I feel guilty, but I am going to bump this.

---

### Post by magcius on 2007-05-15
Maybe a bump will help?

---

### Post by m.musashi on 2007-05-15
In your first post you mentioned
> **magcius said:**
> I followed pretty much all the in the installer, only at the last step (I believe it is when you are reviewing your install options), I clicked "Advanced..." and set the GRUB setting (I forget what it is now) to (hd2), my external hard drive.
which suggests that originally your drive was hd2 when you installed grub. After installing and switching the usb drive to be the boot drive also changed it to hd0. In my experience, when grub is installed to a drive other than hd0 it usually causes problems when trying to boot that drive. It seems like grub is trying to start since you are getting a bunch of grub text, but it's not finding the files it needs to continue.

Try renaming the UUIDs to the actual name of the drive and partition where the boot files are located. Back up the menu.lst first so you can replace it if this doesn't work. It's just a hunch but maybe worth a try.

---

### Post by magcius on 2007-05-16
> **m.musashi said:**
> 
**Try renaming the UUIDs to the actual name of the drive and partition where the boot files are located. Back up the menu.lst first so you can replace it if this doesn't work. It's just a hunch but maybe worth a try.**

I am sorry, but I have only worked with Linux for so long. I would have *no clue* as to how to go about this... If you get a chance would you be able to tell me?

---

### Post by m.musashi on 2007-05-16
Sure. In your menu.lst you have a section that looks like this
```
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=[color=red]UUID=A4787B87787B56D0[/color] ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
The part I hilighted in red is the UUID bit.

If you change it to
```
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=[color=red]/dev/sda1[/color] ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
It will allow you to be specific about the location in language we understand. I have no idea how to understand a UUID. However, the UUID is supposed to be the preferred method since it stays the same even if you move a drive around (ie change where it's connected to the mobo not repartition it). But since it's not working this is a better way for us to make sure you are actually trying to boot the right partition.

BTW, the /sda1 part is a guess based on the info in your menu.lst. It could be wrong. The fact that it says root=(hd0,0) translates into /dev/sda1 (or hda1 depending on the type of drive) If the hd0,0 part is wrong then the other part will be wrong too.

Oh, you can back up the file by doing
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

---

