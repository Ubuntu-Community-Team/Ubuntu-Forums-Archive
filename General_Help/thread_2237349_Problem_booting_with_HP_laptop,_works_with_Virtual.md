---
title: "Problem booting with HP laptop, works with Virtualbox"
date: 2014-08-01
forum: General Help
---

### Post by benbrockn on 2014-08-01
I copied this from my Linux Mint forums since I wasn't getting any help, and I'd like to see this solved fairly soon.

Here are links to earlier posts I had on the subject:  [http://ubuntuforums.org/showthread.php?t=1883577](http://ubuntuforums.org/showthread.php?t=1883577)

I think it boils down to a BIOS problem, but I never could get it fixed. Is there anyone out there having an HP laptop and a fix for this? (Yes, BIOS is latest version).
--------------------------------------------------------------------------------------------------------------

This is a problem I've noticed with my laptop, I'm not sure why. Back in  the day I experimented with Ubuntu 10 & 11 and put it on a USB  external HDD. Worked fine in VirtualBox (several versions). When I tried  to boot from my laptop - nothing. For the Ubuntu ones it would get to  about 3.0 seconds and freeze, not loading anything else. It also worked  on my older Compaq Laptop with Win XP 32bit installed. On my Linux Mint  17 MATE version, it works in VB but on my HP laptop, loads a black  screen with blinking cursor. (I don't have my old XP with me to test it  there). 

Both of these are NOT pendrives, they are full versions  tested in VirtualBox & set up the way I like them. I used Clonezilla  to save partitions and restore partitions on the drives. With Ubuntu 10  & 11  used both a USB stick (partitioned) and a USB HDD  (partitioned). With LM17 I only used a USB stick (Partitioned). I have  used live persistent pendrives in the past (using syslinux) and those  always work. Just when I try this method, HP doesn't like it.

I  know it has something to do with the way my HP laptop boots up, but I  can't figure it out... I'm hoping to maybe change the way grub loads to  fix this problem.


Specs:

Laptop_______________HP Pavilion dv6z Quad Core Laptop
Operating System______Windows 7 Home Premium 64-bit SP1
CPU__________________AMD A6-3400M	134 °F
_____________________Llano 32nm Technology
RAM_________________5.00GB DDR3 @ 665MHz (9-9-9-24)   [6 GB RAM]
Motherboard__________Hewlett-Packard 358B (Socket FS1)	135 °F
Graphics_____________Generic PnP Monitor (1366x768@60Hz)
_____________________512MB ATI AMD Radeon HD 6520G (HP)	133 °F
Storage______________596GB SAMSUNG HM641JI SATA Disk Device (SATA)	101 °F
Optical Drives_________ELBY CLONEDRIVE SCSI CdRom Device
_____________________hp BD CMB UJ141AF SATA CdRom Device
Audio________________IDT High Definition Audio CODEC
Ports_________________2 USB 2.0 ports,  2 USB 3.0 ports  (tried all sets of ports, same things happens)

AMD USB 3.0 Host Controller, Standard Enhanced PCI to USB Host controller, Standard OpenHCD USB Host Controller

--------------------------------------------------------------------------------
Linux OS:

Linux Mint 17 MATE 64 bit
16GB USB flash drive

Root 7500 MiB (7.86 GB)  [1.22 GB unused]
Home 7766 MiB (8.14 GB) [5.41 GB unused]
No Swap (since I have 6GB RAM)

---------------------------------------------------------------------------------

Here's what's in grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text nomodeset"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"

```


The original grub had ***GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"*** but I changed it to ***"text nomodeset"*** hoping that would work, it didn't.
I also uncommented the line below for it to beep, it doesn't beep either.

It just loads a black screen with blinking cursor...

---

### Post by sp40140 on 2014-08-01
I have a feeling one or more of the mount points are off.
However, I am confused about your set-up. You refer to VirtualBox and native install both! Can you please explain this?

---

### Post by benbrockn on 2014-08-01
> **sp40140 said:**
> I have a feeling one or more of the mount points are off.
However, I am confused about your set-up. You refer to VirtualBox and native install both! Can you please explain this?


I effectively made a full install on a USB flash drive with 2 partitions  (ROOT & HOME) using Clonezilla & Virtualbox. This is how I did  it:

1) Fully installed LM17 on a Virtualbox HDD
2) Customized/updated LM17
3) Used Clonezila to saveparts to a file
4) Used Clonezilla to restoreparts onto a partitioned USB flash drive
5) booted only USB flash drive using Virtualbox -> works
6) booted only USB flash drive using HP laptop -> doesn't work, creates blank screen with blinking cursor

It has to do with either the BIOS on my HP laptop or additional parameters in grub to properly boot.
The same thing happened when I used Ubuntu in the past (see thread link above).

_**EDIT:**_ I did the exact same setup in the past and it worked with an older laptop. I assume that my LM17 would work with my older laptop as well, but I can't test it since I am deployed. I doubt it has to do with mount points as it worked perfectly in the virtual machine (loaded completely from the USB drive and nothing else).

---

