---
title: "[SOLVED] Risk of putting ubuntu on external usb"
date: 2008-04-19
forum: General Help
---

### Post by amyst on 2008-04-19
I plan to follow this guide [HTML]http://ph.ubuntuforums.com/showthread.php?t=678146[/HTML] to install 8.04 on an external usb drive. After reading lots of posts, the risk seems to be having the grub being written to the mbr instead to the external drive. 

I'm using a dell laptop 1520 than runs 7.10, and I'm hoping to have 8.10 on the external usb. If during the installation something wrong occurs to the mbr, my laptop get a grub error and can't boot anything, **can a clean ubuntu install on my laptop restore mbr? ** I am guessing that grub is stored on the mbr - what does it mean if I break it? Would my laptop break permanently?

---

### Post by ibuclaw on 2008-04-19
From what I have read (quick brisk through)
It seems perfectly safe, and the loosing of the MBR is only minor, as it's easily fixable.

To quote the bottom in larger letters, as it's not always easy to read it:
```


1. Insert your Windows Vista Install DVD and boot from it.
2. After selecting your language options choose the &#8220;Repair your computer&#8221; option in the bottom left corner.
3. Select your Windows Vista Installation and continue
4. Open a new Command Prompt window
5. When command prompt is open, type the following commands
[CODE]
[B]Bootrec /fixboot
Bootrec /fixmbr[/B]

```
[/CODE]


And with Windows XP its just the same similiar steps as above, enter Recovery Console [(read here on how to access it)]("http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20access%20the%20Recovery%20Console:") and type a simple "FIXBOOT" and "Y"
To quote the linked site:
```

To repair a damaged Boot Sector at the command prompt type **FIXBOOT** and press Enter.
Then answer "**Y**" 

```

Regards
Iain

---

### Post by amyst on 2008-04-19
Thanks for the prompt reply, but the set of fixes isn't what I am looking for. I can do the same set of fixes as vista or xp with a ubuntu live CD or gparted. But all they modify is the internal hard drive. What I wish to know is if grub somehow modify the motherboard (I heard supergrub mentioned a few times, but I don't know how it works), how can I fix it if the modification goes wrong. 

Basically, I want to have two ubuntu's. One on my laptop's internal HDD, and the other on the external usb drive. My guess is that there's only one grub, on the mbr, that recognize the two ubuntu's when external HDD is connected.

I would greatly appreciate if someone who get this working can post their menu.lst. I think by looking at it I would have some idea what's with grub.

---

### Post by ibuclaw on 2008-04-19
Ah, okay.

I think there should be a Boot Record on both devices.

GRUB doesn't touch the Motherboard BIOS settings.
It only alters the part of the hard-drive where the Motherboard expects to read the boot data from.

ie:
If you have the BIOS set to the boot order as in the How-to you posted
> 
USB
CDROM
HARD DRIVE

Then the Motherboard will scan for a boot record on the USB ports, if one is there it will boot straight into the USB Disk.
If it can't find one, then it checks the CD-ROMs, then Hard Drive.

I think it's like using a LiveCD (except it's a USB Stick that you're booting off).

I repeat, the motherboard is safe.

Regards
Iain

---

### Post by amyst on 2008-04-19
Oh so I was confused! Thank you very much for this explanation :)

amyst ng

---

