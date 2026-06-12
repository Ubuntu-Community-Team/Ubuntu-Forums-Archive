---
title: "New 'puter coming......"
date: 2024-11-18
forum: General Help
---

### Post by Autodave on 2024-11-18
Santa coming early this year!  My Win11 machine should be here tomorrow.  Of course, I want to get Linux on it quickly while still keeping Win11.  For the past few machines, I have always just had Win and Linux of seperate drives.  But now my 2TB drive will be more than enough to house both OSes.  What do I need to turn off in the BIOS before installing Xubuntu?

Thanks in advance!

---

### Post by Rex Bouwense on 2024-11-18
The only thing we have had to turn off was fast boot.

---

### Post by yancek on 2024-11-18
If the computer comes with windows 11 installed, it will surely be an EFI install and you need to make sure you boot and install in EFI mode.  This may not be a problem as many computers manufactured since 2020 do not give the Legacy option but check before you install.

If you plan to access windows filesystems from Ubuntu, you should disable hibernation in windows.

---

### Post by Autodave on 2024-11-18
How do I make sure that I install in EFI mode?

---

### Post by oldfred on 2024-11-18
My Dell needed bitlocker turned off and I turned off fast startup.

But I ended up having charging issues & had to return to Dell. It came back & Ubuntu worked, but Windows did not. Had Windows repair/recovery flash drive, did not work. Downloaded full installer from Microsoft, did not work. The only thing that did work was to download the full Dell restore from Dell. That erased Ubuntu and made it just like the day I bought it. I gave up on dual boot.

I had created an external SSD with full Ubuntu. And now use that with my Dell. Fast enough thru USB-c port that I cannot tell difference with internal install & external drive.
 Rarely boot Windows, just to update it, except when traveling or in Tax season to run TurboTax. I really prefer my Desktop that is Kubuntu only or actually several versions of Kubuntu.

---

### Post by Autodave on 2024-11-18
This is a desktop: Ryzen 9 9900, 32G ram, RTX 4080 Super.  I am hoping that the newest kernel will be OK.  I like your idea about running Linux from an external SSD though....I may try that before I decide if I want to put it on the internal drive.  If the speed is good, I might just keep it like that.

---

### Post by tea for one on 2024-11-18
> **Autodave said:**
> How do I make sure that I install in EFI mode?
How you boot controls the mode of installation.
Boot in UEFI mode = Install in UEFI mode.
After you have booted into a live "Try Ubuntu" session, you can double check with this terminal command:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```

---

### Post by dragonfly41 on 2024-11-18
+1 > [COLOR=#000000]I like your idea about running Linux from an external SSD though....I may try that before I decide if I want to put it on the internal drive. If the speed is good, I might just keep it like that.[/COLOR]
[COLOR=#000000]I have run in that mode for years. I invested in StarTech powered dual docking bay (USB 3.0) and in there I have two plugin SDD's in caddies. One plugin caddy contains Ubuntu 22.04 and also a partition shared with Windows 10 (I have older Dell tower which does not take Win 11). The second plugin caddy SSD is for backups.[/COLOR]

---

### Post by 1fallen on 2024-11-18
> **Autodave said:**
>   I like your idea about running Linux from an external SSD though....I may try that before I decide if I want to put it on the internal drive.  If the speed is good, I might just keep it like that.

I as well have been doing this for years, with a Powered Dock station, I literally notice no difference in speed or stability.

I run 5 different OS's from that setup.

---

### Post by Autodave on 2024-11-18
So.....I can put my 24.04 installation USB in one port and boot to that and then have it install to an SSD that is in another port?  Is that correct?

---

### Post by 1fallen on 2024-11-18
> **Autodave said:**
> So.....I can put my 24.04 installation USB in one port and boot to that and then have it install to an SSD that is in another port?  Is that correct?

Yes that's right....But be sure you know the real destination drive. But you know that.

---

### Post by oldfred on 2024-11-18
If installer sees internal drive, it may install grub to internal drive's ESP. Which you may not want, if you ever want to use external drive with any other system. Often better to have boot files on external drive.

Old installer only only installed to first drive,  I use Kubuntu and its installer gives a choice on ESP.
But with Ubuntu supposedly the choice is there, but you may need ESP - efi system partition FAT32 on external drive first.
Once on external drive, it may depend on your UEFI how you boot. It may have an "ubuntu" entry or just a drive entry just like live installer. And often disconnecting an external drive has it lose UEFI Ubuntu entries & you have to use the drive entry. My Dell remembers entry, my desktop does not.

I prefer to use gparted to set up partitions in advance and use Manual install to choose partitions. If larger drive, I use smaller / (root) and do not normally allocate entire drive initially.

---

### Post by dragonfly41 on 2024-11-18
+1 > [COLOR=#000000]I prefer to use gparted to set up partitions in advance [/COLOR][COLOR=#000000].
I omitted that. When you first plugin your LiveUSB you create using mkusb or Rachel you first use "Try Ubuntu" not "Install". In Try Ubuntu mode install gparted (if not already installed) and then format and partition your target external SSD where you plan to install Ubuntu. Make sure that your first partition is FAT for loaders (mine is 500 MBS in size) and you set EFI boot flags.  Your next partition wil be EXT4 where Ubuntu is installed. You might choose to create other partition for data shared with Windows. So yes you will require two ports for this exercise. Or a port expander.

[/COLOR]

---

### Post by Autodave on 2024-11-18
Got an idea......I have a couple other machines sitting around.....none of them have hard drives at the moment.  I could use one of those to make the bootable SSD on.  Then, when turning the new machine on with the SSD attached, I could just use the boot manager to pick what to boot to.  That way I don't screw up the Windows installation on the new machine.  Plus, except for removing the nVidia driver, I can take the SSD to any other machine and boot it to Linux.  That should work.......

---

### Post by oldfred on 2024-11-18
I used my external SSD on my Dell with Intel 11th Gen, Desktop with Intel 6th Gen and even an old BIOS Intel duo-core2.
With old BIOS system, I had to add a BIOS boot stanza on its HDD to directly boot SSD as old system not UEFI. Others I could boot from ESP on SSD.

Not of my systems have proprietary drivers which would complicate booting. If external drive large enough, you could have different installs, configured differently but using same data partition(s). I do not share /home.

---

### Post by dragonfly41 on 2024-11-19
> [COLOR=#000000] If external drive large enough, you could have different installs, configured differently but using same data partition(s).[/COLOR][COLOR=#000000]
Good idea. I might use one of my two plugin caddies in StarTech docking bay to hold multiple installations. Indeed Cubic could be used to customise them. Edubuntu comes to mind for eLearning. One caddy is in use already .. for writing this in Ubuntu.

[/COLOR]

---

