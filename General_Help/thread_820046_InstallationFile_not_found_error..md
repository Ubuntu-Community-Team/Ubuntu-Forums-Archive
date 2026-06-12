---
title: "Installation/File not found error."
date: 2008-06-05
forum: General Help
---

### Post by olympios on 2008-06-05
Installing from Windows XP desktop, using wubi.exe. Installation starts normally and then asks to reboot. Boot screen now gives me the option to boot to Windows XP or Ubuntu. I choose Ubuntu, goes through the installation process, and when it reboots again I get this:
Filesystem type is ntfs, partition type 0x7
Kernel /boot/vlinuz-2.6.24-16-generic root=UUID=6848F42748F3F1A4 loop=/ubuntu/disk/root.disk ro quiet splash
Error is: File not found.

If I use the CD to install, I get a similar error and I think it says: Disk not found.

Any help, please?

---

### Post by ago on 2008-06-06
[https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

---

### Post by digitalggs on 2008-07-13
> **olympios said:**
> Installing from Windows XP desktop, using wubi.exe. Installation starts normally and then asks to reboot. Boot screen now gives me the option to boot to Windows XP or Ubuntu. I choose Ubuntu, goes through the installation process, and when it reboots again I get this:
Filesystem type is ntfs, partition type 0x7
Kernel /boot/vlinuz-2.6.24-16-generic root=UUID=6848F42748F3F1A4 loop=/ubuntu/disk/root.disk ro quiet splash
Error is: File not found.

If I use the CD to install, I get a similar error and I think it says: Disk not found.

Any help, please?


Open the file ?:\ubuntu\disks\boot\grub\menu.lst (?= the drive you installed ubuntu to) in a text editor. Anything with a 'find and replace option. Notepad will do, but I much prefer Notepad++ (can find it at [http://portableapps.com](http://portableapps.com)). 

After you open in viewer minimize it and open My Computer. and navigate to ?:\ubuntu\disks\boot. Look for a file named vmlinuz-2.6.24-##-generic, '##' will be an actual number and may not be 16 wich leads me to how to fix your problem. 

Back to the text editor with menu.lst do a find and replace 
find: vmlinuz-2.6.24-16-generic
replace with: vmlinuz-2.6.24-##-generic ('##' of course matching the file you found in prev step)


the version I had when I installed today was vmlinuz-2.6.24-19-generic.

---

