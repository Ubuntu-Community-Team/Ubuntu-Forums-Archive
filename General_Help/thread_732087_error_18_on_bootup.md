---
title: "error 18 on bootup"
date: 2008-03-22
forum: General Help
---

### Post by slimjim8094 on 2008-03-22
Kubuntu 8.10 KDE4, WUBI "Wubi-8.04-alpha-rev450.exe".

I download and restart, it pops up the NTLDR menu and I  choose Kubuntu KDE4 from the list. On selection, it does the memory check and "Press ESC to see menu". 

Then it breaks with "Error 18 - Inconsistent File System Structure" (might not be actual description, but correct error number)

Is this just what I get for using alpha software, or can this be fixed? I haven't seen any solutions yet, or really anybody else having the same problem.

contents of C:\ubuntu\install\boot\grub\menu.lst
```

#This file is modified at runtime by bootmenu.nsh

debug off
hiddenmenu 
timeout		5
default		0

title Start installer in normal mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-amd64.iso quiet splash ro automatic-ubiquity locale=en_US.UTF-8 noprompt --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in safe graphic mode (only if you have display problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz xforcevesa boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-amd64.iso quiet splash ro automatic-ubiquity locale=en_US.UTF-8 noprompt --  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer with ACPI workarounds (only if you have ACPI problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz quiet boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-amd64.iso ro automatic-ubiquity locale=en_US.UTF-8 noprompt -- acpi=off noapic nolapic  
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in verbose mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debug boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-amd64.iso ro debug-ubiquity automatic-ubiquity locale=en_US.UTF-8 noprompt --  
initrd /ubuntu/install/boot/initrd.gz
boot

```

---

### Post by ago on 2008-03-22
The menu.lst file is ok, that is more like a generic grub problem which might be due to your disk structure not being particularly clean. Try first googling for the specific error message and see if any solution helps.

---

### Post by tvtech on 2008-03-22
grub is very very very well documented  

for a list of erros go to 
[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting]("http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting")

this has saved my bottom more than once!

simple solution create a really small boot partition less than a gig.  this is a hardware issue usually only encountered on older hardware, you might want to upgrade your bios

---

### Post by slimjim8094 on 2008-03-22
16 : Inconsistent filesystem structure
    This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB. 

Sorry - mistyped 16 as 18. Forget it - I'll just install to a partition.

---

