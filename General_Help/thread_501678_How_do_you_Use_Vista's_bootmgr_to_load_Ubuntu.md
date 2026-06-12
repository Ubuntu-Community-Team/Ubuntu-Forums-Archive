---
title: "How do you Use Vista's bootmgr to load Ubuntu"
date: 2007-07-15
forum: General Help
---

### Post by adromidon on 2007-07-15
Hello,
I would like to use the bootmgr in vista to configure a boot menu option for Ubuntu.

I know it is easier through grub but i specificaly want it to be setup on the vista boot menu. I have my reasons

Anyway what would i need to do once both OS are installed to make the vista bootloader load Ubunutu

---

### Post by Daveth on 2007-07-15
I doubt it ever would as Windows seems to singularly ignore any other file system, even when on the partition next to it.

---

### Post by merlinus on 2007-07-15
I remember a thread on the forums about this. Do a search.

-merlin

---

### Post by Uncle Spellbinder on 2007-07-15
[WUBI](http://wubi-installer.org/index.php)

[WUBI forum](http://ubuntuforums.org/forumdisplay.php?f=234)

---

### Post by dfreer on 2007-07-15
Not sure about Vista, but you can definitely do it in XP. In XP, these would be the steps you would need to take, they may be able to help you:

(1). Make sure that GRUB is installed to the boot sector of a linux partition, and not to the MBR (MBR being the boot sector of the hard drive itself, which is where it is installed by default). This isn't really a problem as you can reinstall GRUB to the boot sector with a Live CD and a few commands, but the important thing here is that you want Vista to have it's boot loader installed in the MBR, so it can manage the boot process. 
(2). Make a copy of ubuntu's boot sector using the "dd" command, and place it in a file somewhere that vista can read it (generally somewhere on the C:\ drive, of course).
(3). Create an entry in C:\boot.ini that points to the ubuntu boot sector you saved earlier, so that NTLDR can load GRUB. Note that in this case you are actually dealing with two boot managers, NTLDR and GRUB, I do not believe any windows OS can boot a linux kernel itself, it just passes control to GRUB and let's GRUB deal with it.

Here's some helpful links (especially note the exact "dd" command to use to make a copy of the boot sector):
[http://jaeger.morpheus.net/linux/ntldr.php](http://jaeger.morpheus.net/linux/ntldr.php)
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

Here's some specifically related to using Vista to boot linux (although I haven't tried this myself):
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)
[https://blogs.technet.com/voy/archive/2006/10/13/how-to-use-windows-vista-s-boot-manager-to-boot-linux.aspx](https://blogs.technet.com/voy/archive/2006/10/13/how-to-use-windows-vista-s-boot-manager-to-boot-linux.aspx)

**Please** if you get this working, post the solution you followed (or even just which guide and a link that you used) so that others following this thread can easily figure out what to do :D Good Luck!

EDIT: After reading on WUBI, it would definitely be an easier way to go about things (although it would require a new installation of Ubuntu). It uses the NTLDR instead of GRUB as well.

---

### Post by adromidon on 2007-07-25
Ok I actually found a cool program alot of you guys may use allready it installs in Vista but it scans for other OS boot parms and adds them to the Vista Boot Manager if you want it to 


[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

It works great just thought i would post how i did it here

---

