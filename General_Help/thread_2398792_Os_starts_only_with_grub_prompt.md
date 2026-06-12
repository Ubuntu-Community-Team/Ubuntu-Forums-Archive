---
title: "Os starts only with grub prompt"
date: 2018-08-17
forum: General Help
---

### Post by a3lm on 2018-08-17
Hello,
I am new to ubuntu and linux in general, and I have a little problem about grub. I think I messed something up when installing ubuntu 18.04.
At each start I need to manually load the kernel before booting, as it starts with grub prompt.
All I have to do is to start from command line with following commands:

set root=(hd0,2)
linux /vmlinuz root=/dev/sda2
initrd /initrd.img
boot

I tried grub-update, grub reinstall on /dev/sda, setting sda2 partition as bootable, but none worked.
I don't understand where it could be the problem, system works, but simply I have to manually load kernel at each restart.
This is a screenshot from gparted:
[ATTACH=CONFIG]280765[/ATTACH]

I also tried boot-repair, both recommended and advanced with secure boot unchecked, but nothing changed.

Can someone help me with this situation? Even because I was planning to install win7 in another partition and if I don't understand what is happening I fear I will have troubles.

Thank you all!!

---

### Post by oldfred on 2018-08-17
You have to have boot flag on the FAT32 formatted partition with UEFI boot, your sda1. That makes it the ESP which UEFI uses to find boot files. Use gparted and move flag back to sda1.

Since you have UEFI, do not use the default Windows 7 boot. The DVD is BIOS only. But can be copied to a flash drive & minor file rename/copy to make it UEFI bootable. How you boot install media is then how it installs. And Windows only boots from a gpt partitioned drive with UEFI. If you force install in BIOS mode it convert drive to MBR and in effect destroys you Ubuntu install.

You also need to set UEFI/BIOS to UEFI boot mode and UEFI Secure Boot off. You may have UEFI setting that says "Windows" or "Other". But fine print somewhere will say to use "Other" if installing Windows 7 as Windows 7 does not support UEFI Secure Boot. 

If booted in UEFI mode, you should just be able to reinstall grub. If that does not work, post link to summary report.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by a3lm on 2018-08-18
Hi, thank you for your reply.
The fat32 partition has boot and esp flags as you can see from the screenshot, so I can't figure out why continue to act like this.
Anyway this is the boot-info summary:
[http://paste.ubuntu.com/p/DtbvJvGqD6/](http://paste.ubuntu.com/p/DtbvJvGqD6/)

thanks again!

---

### Post by oldfred on 2018-08-18
Boot-Repair copies the mount entry of the ESP in fstab to change permissions, so it can make changes in the ESP.
But you had boot flag on the / partition.

       #UUID=793D-6557	/boot/efi	vfat	defaults	0	1
UUID=a7f9da97-8d2c-4cd1-97f1-3dbe6f1430b9	/boot/efi	ext4	defaults	0	1 
    
Mount your fstab from the live installer or if you can boot and remove the # from the first line above (is second from bottom) and put # to convert last line to comment or delete it. You cannot have an ext4 partition as /boot/efi anyway.

---

### Post by a3lm on 2018-08-19
I'm not sure I understood what you mean.

I have no problem to boot, I am able to by typing those commands I wrote before in grub prompt.

Anyway I commented the line you said and uncommented the other in /etc/fstab file, but I still can see no changes, booting I am always asked to type those commands in grub prompt. 
this is fstab file current situation:[ATTACH=CONFIG]280788[/ATTACH]
and this is a screenshot from gparted:[ATTACH=CONFIG]280789[/ATTACH]

---

### Post by oldfred on 2018-08-19
If you now have correct ESP, try this:
       sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi 
    
If not use Boot-Repair's advanced options and a full uninstall/reinstall of grub.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by a3lm on 2018-08-20
First command did not worked, but a reinstall now solved the issue!
Thanks, you've been very helpful!

Just a question, now it directly starts on ubuntu, without showing a menu or something like that before booting, for now it's ok but what should I care when installing windows 7 in another partition?
I would install it from a pendrive

---

### Post by oldfred on 2018-08-20
Grub knows if you only have one install and default boots to that.
You can get to menu with Escape key between UEFI start up screen and grub loading. But if UEFI fast boot (different than Windows fast start up) is on, you may not have time to press any key before system boots.

If installing Windows 7, you must copy to flash drive and move/rename a couple of files to make it UEFI bootable. The DVD is BIOS boot only. 
How you boot install media is then how it boots. 
And Windows in BIOS mode will convert drive from gpt (incorrectly) and make it MBR(msdos) effectively erasing your Ubuntu install. So you must boot & install in UEFI mode.

---

### Post by a3lm on 2018-08-20
Thanks again for your help!

---

