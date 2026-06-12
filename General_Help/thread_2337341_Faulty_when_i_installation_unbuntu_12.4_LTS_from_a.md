---
title: "Faulty when i installation unbuntu 12.4 LTS from an ISO file using grub4dos"
date: 2016-09-16
forum: General Help
---

### Post by 9blazepo on 2016-09-16
My computer uses Windows 8, and have 3 HDD. I have installed and used grub4dos system always boot the machine. now I want to install in parallel unbuntu with windows 8. I'm download 12:04 Ubuntu LTS vesion and boot from HDD according to instructions,
Here is the code I used.

```

[COLOR=#000000][FONT=Tahoma]title Install Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]find --set-root /ubuntu-11.04-desktop-i386.iso[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]map /ubuntu-11.04-desktop-i386.iso (0xff) || map --mem /ubuntu-11.04-desktop-i386.iso (0xff)[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]map --hook[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]root (0xff)[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed noprompt boot=casper only-ubiquity iso-scan/filename=/ubuntu-11.04-desktop-i386.iso quiet splash --[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]initrd /casper/initrd.lz[/FONT][/COLOR]

```

and this error

```

[COLOR=#000000][FONT=Tahoma]-21, mem: 638k/2046M/0m, end: 355B35[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][minimal BASH-like line editing is supported. for the firt word, TAB lists possible completions of a device/filename. ESC at any time exits.][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]grub> fine --set-root /1.iso[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma](hd3,0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]grub> map /1.iso (0xff) || map --mem /1.iso (0xff)[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]probed C/H/S = 707/64/32, probed total sectors = 1447936[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]grub> map --hook[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]grub> root (0xff)[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]filesystem type is iso9660,, using whole disk[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]grub> kernel /casper/vmlinuz boot=casper integrity-check noprompt iso-scan/filename=/1.iso quiet splash --[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][Linux-bzimage, setup=0x4200, size=0x52b9e0][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]grub> initrd /casper/initrd.lz[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][linux-initrd @ 0x7efac000, 0xff34e5 byte][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]grub> boot[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]busybox v1.18.5 (ubuntu 1:1.18.5-1ubuntu4.1) built-in shell (ash)[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]Enter 'help' for a list of built-in commands.[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma](initramfs) windows is hibernated, refused to mount.[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]failed to mount '/dev/sda1': operation not permitted[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]The NTFS partition is hibernated. please resume and shutdown windows properly, or mount the volume read-only with the 'ro' mount option, or mount the volume read-write with the 'remove_hiberfile' mount option.[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]For example type on the command line:[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /isodevice[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]mount: mounting /dev/sda1 on /isodevice failed: no such device[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]could not find the iso /1.iso[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]This could also happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of a removable device without first unmounting or ejecting it.. To fix this, simply reboot into windows, let it fully start, log in, run 'chkdsk /r', then gracefully shut down and reboot back into windows. After this you should be able toreboot again and resume the installation[/FONT][/COLOR]

```

I tried to copy files via USB and boot FAT32 format, but the problem continues.
Hope you help

---

### Post by oldfred on 2016-09-16
Is your Windows 8 install UEFI or BIOS?

Either way you must have fast start up off which is always on hibernation.
       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

Do not know grub4dos, do not recommend it. But you show find --set-root /ubuntu-[COLOR=#ff0000]11.04[/COLOR]-desktop-i386.iso to install 12.04?
And if system is new enough to support Windows 8 you should be installing 16.04. Only if you have AMD video, then you should install 14.04 for now.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I use grub2 to boot ISO.

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by ian-weisser on 2016-09-16
I cannot see how those grub instructions could possibly work for a new install.
They seem clearly written to locate and overwrite a previous 11.10 install.
Why do those instructions specify a preseed file? Was there a preseed file? If so, why?

If you are just incanting voodoo without understanding it, then consider an Ubuntu Virtual Machine (VM) on your WIndows 8 host as a safe way to try Ubuntu without all the fussing about with repartitioning and perhaps breaking your Windows install.

---

### Post by 9blazepo on 2016-09-19
Thanks for your help. After i tried and tried learn them, i turned off hibernate functions of the windows and to have solved it.

---

