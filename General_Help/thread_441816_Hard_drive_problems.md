---
title: "Hard drive problems"
date: 2007-05-12
forum: General Help
---

### Post by tbasherizer on 2007-05-12
Last night, I was trying to install a copy of mac os x in vmware, and was trying to make a physical disk partition with gparted to install mac os x on in vmware (confusing?). I was fooling around in gparted, when I stumbled upon a certain tool, I forget the name now, but can find it out when asked. I then restarted my copmuter to boot into Ubuntu, when some terminal stuff came up, and at the bottom, it said something along the lines of 

" (number of sectors) out of (number of sectors) hda2
Not automatically fixing this."

That's really vague, but if asked, I can provide a more detailed description, as I can't restart my computer at the moment. I can't boot ubuntu, and am stuck in n00bdows at the moment. Please help!

---

### Post by tgalati4 on 2007-05-13
I've had this happen to be on a Dell Inspiron Laptop.  I think what is happening is as follows:

You have a machine with a BIOS that supports suspend to disk.

During certain events (this is what I am not sure about) the BIOS attempts to write the suspend file to disk.  But of course with our linux meddling, this disk does not exist, nor will it ever exist.

Somehow the BIOS writes a flag to the Master Boot Record (MBR)--saying "hey dummy, boot off the suspend disk"

Linux checks the MBR by making a snapshot (I think) and if there are errors it will post the comparison.

It will warn you of the error, but not restore the MBR from backup unless you do an fsck on the disk and anwser yes to restore MBR.

Because Grub is installed on the MBR, it gets hosed by the BIOS suspend attempt.

You can repair it in one of several ways.  Try booting the Live CD, mounting your harddrive in the terminal, and sudo grub-update.  This should find kernels on your disk and write the appropriate, bootable MBR.

If you have a grub boot floppy (and you will after this event), boot into grub and manually type in the boot sequence.  Use tab completion to simplify the typing:

> root (hd0,0)
Hey I found something to boot from.
>kernel /boot/kernel (tab)
>initrd /boot/initrd (tab)
>boot

This MBR nonsense usually happens when you are screwing around.  And from the description of what you were doing in your post--I would say that qualifies.

---

### Post by tbasherizer on 2007-05-13
Thanks, I'll give it a try.

---

### Post by tbasherizer on 2007-05-13
Could you be a bit more specific as to what to do in grub?

---

### Post by tgalati4 on 2007-05-13
When you boot, the first thing that comes up is Grub.  The Grand Unified Boot Loader.

You should see a menu of different operating systems to load:  Ubuntu, Windows, Freespire, SLED, etc.

If you hit the "c" key it takes to you command line.  You are now in a Grub terminal.

Type in the following:

> root (hd0,0)
I have found a FAT32 Partition that is just peachy.
>root (hd0,1)
I have found a Linux Partition that is just peachy.

(Yours may not say peachy.)

To boot linux you need four things from grub:

A root device
>root (hd0,0)
A kernel
>kernel /boot/kernel (tab key)  or  kernel /vmlinuz-(tab key)
An initial ram disk
>initrd /boot/initrd (tab key) or /initrd(tab key)
The boot command
>boot

If your system does not come up in grub, then you can create a grub floppy (there are tutorials on the forums to do that--search grub floppy).  This will boot to grub and give you a grub command line.

It's similar to lighting a match in the dark.  It's tough to do when you can't see, but once you can see, it's obvious where the light switch is.

---

### Post by tbasherizer on 2007-05-15
Nevermind. I figured out the root of the problem. I had set vmware to boot from physical disc, and there were some problems with that. So I uninstalled it in the command line, and all is good. But thanks anyway.

---

