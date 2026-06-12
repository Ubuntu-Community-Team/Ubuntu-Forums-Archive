---
title: "[SOLVED] Booting Ubuntu Server from USB doesn't work"
date: 2018-09-02
forum: General Help
---

### Post by theshroom on 2018-09-02
I'm having an issue trying to install Ubuntu Server 18.04 on my old (12 years old) desktop. I keep getting a message saying it can't find a default or UI directive: 
```
No DEFAULT or UI configuration directive found!
```
After several attempts of trying to fix it for about 2 hours I decided to try booting it on my Macbook Air instead, which worked.
So, what could be causing the problems on my desktop? I checked the minimum requirements for the CLI/Server version of Ubuntu, which required: 

[LIST]
[*]300 MHz x86 processor 
[*]256 MiB of system memory (RAM) 
[*]1.5 GB of disk space 
[*]Graphics card and monitor capable of 640x480 
[/LIST]

The hardware on my desktop is this: 
[LIST]
[*]CPU: AMD/ATI Athlon x2 4400+ 2.2GHz (Dual core) 
[*]GPU: Radeon X1650 Series (500MB VRAM) 
[*]RAM: 2GB 
[*]HDD: 500GB 
[*]USB STICK: 32GB 
[/LIST]
So, it should run fine right? Or is the components on the desktop simply too old, even if it technically matches the minimum requirements?
Since it works on the Macbook it doesn't feel like I'm doing something wrong either? But maybe I am?

---

### Post by TheFu on 2018-09-02
Could be lots of things.

A 12 yr old system will use BIOS/Legacy to boot, not EFI like a Mac.  So if you are asked any questions about EFI, UEFI, or BIOS booting, always choose the last, BIOS.

Not all USB ports and controllers are compatible with all USB flash drives.  Try a different flash drive.  Try a different USB port.

Ubuntu Server won't have any GUI. It will use a text interface.  In fact, if you like you can install using a true serial console and no GPU at all.

For better help, you'll need to say exactly step-by-step where the process is failing.  Does the BIOS even see the USB stick?  

Also, I think i686 support was dropped from the normal server ISO.  Have you tried using the Alternate Install ISO?  Non-64-bit support is likely to be ended for new installs in the future.  Not immediately, but there has been talk about ending all 32-bit support.

---

### Post by theshroom on 2018-09-02
> **TheFu said:**
> Could be lots of things.

A 12 yr old system will use BIOS/Legacy to boot, not EFI like a Mac.  So  if you are asked any questions about EFI, UEFI, or BIOS booting, always  choose the last, BIOS.

Not all USB ports and controllers are compatible with all USB flash  drives.  Try a different flash drive.  Try a different USB port.

Ubuntu Server won't have any GUI. It will use a text interface.  In  fact, if you like you can install using a true serial console and no GPU  at all.

For better help, you'll need to say exactly step-by-step where the process is failing.  Does the BIOS even see the USB stick?  

Also, I think i686 support was dropped from the normal server ISO.  Have  you tried using the Alternate Install ISO?  Non-64-bit support is  likely to be ended for new installs in the future.  Not immediately, but  there has been talk about ending all 32-bit support.

I'm not asked anything about EFI, UEFI or BIOS when booting, it just automatically takes me to the "boot device selection" screen, and when I select the USB device in the list it takes a few seconds and then it prints out the error to the screen.

The BIOS does see the USB device, it's labeled as SanDisk in the boot-device selection menu.

I'm aware that Ubuntu Server won't have any GUI. The PC is extremely slow (it can take up to 3 minutes to open google chrome), it can barely run Windows 7 at all, so I figured it would be a good idea to use a non-graphical OS to increase performance.

I'm using a 64-bit version of Ubuntu Server, Windows 7 is running 64-bit and that works. Should I try a 32-bit version of Ubuntu anyways?

---

### Post by TheFu on 2018-09-02
So I googled that error.
[https://ubuntuforums.org/showthread.php?t=2311383](https://ubuntuforums.org/showthread.php?t=2311383) came up.  Does that help?

There were other answers too.

---

### Post by theshroom on 2018-09-03
> **TheFu said:**
> So I googled that error.
[https://ubuntuforums.org/showthread.php?t=2311383](https://ubuntuforums.org/showthread.php?t=2311383) came up.  Does that help?

There were other answers too.

Changed the boot order to: 
**1.** Harddisk
**2.** Removable (USB)
**3.** CDROM
**4.** Empty

Still getting the same error :(

**Edit:**
Realized I forgot to mention what I already tried in my original post.

When I initially encountered the error I googled it, and most of the answers were: 

[LIST]
[*]**Format USB as FAT instead of FAT32** - I couldn't, the only option was FAT32.
[*]**Rename isolinux files and folders to syslinux** - Didn't solve the problem.
[/LIST]

[B]Edit 2:
[/B]After trying with 6 different versions of Ubuntu (non-server version), and trying 3 different Rufus settings with each version, I decided to try using the DD option instead of ISO in Rufus when writing the ISO to the USB.
This actually worked. After trying the DD option with the newest version of Ubuntu server, but sadly that did not go very well.

This time I was greeted by a linux kernel panic error: 
**Kernel panic - not syncing: IO-APIC + timer doesn't work!**I managed to find [this post]("https://askubuntu.com/questions/372187/12-04-kernel-panic-not-syncing-io-apic-timer-doesnt-work"), and using it I fixed the error.

---

