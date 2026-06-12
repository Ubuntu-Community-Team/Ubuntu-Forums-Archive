---
title: "Acer - no Ubuntu boot option in UEFI after install"
date: 2018-09-13
forum: General Help
---

### Post by haqiu on 2018-09-13
[https://paste.ubuntu.com/p/5JNQJsFTBR/](https://paste.ubuntu.com/p/5JNQJsFTBR/)


**The above URL is taken from the boot-repair tool's report.**


I'm new to Linux. I have a laptop computer with 2 hard drive. One is a 1TB ordinary hard disk drive while the other is a 256GB SSD drive. I installed Windows 10 on the SSD drive(sdb).


**I'm using UEFI boot and Secure Boot is enabled.** At the moment I would prefer keep using UEFI and keep secure boot enabled unless it's really necessary to change them.


Then I want to install Ubuntu 18.04LTS to get dual boot. During installation I chosed manually partitioning and installed Ubuntu 18.04 into the ordinary hard disk drive(sda). I created 2 partitions, one of which is swap area, and the other is for / (root directory). I did not created any other partition for Linux, but when asked for "Device for boot loader installation", I chose the Windows EFI partition(in sdb).


However after installing Ubuntu 18.04 and restarting the computer, there is no grub boot loader showing up and the computer boots directly into Windows 10. **I have checked the BIOS, even there is not a Ubuntu/Linux boot option to choose in the boot priority order in BIOS**.


**I have tried the boot-repair tool (**[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)**) but it doesn't fix it**, even though it says "Boot succesfully repaired". Hence I upload the boot info to the above URL.


Since I'm new to linux, this has driven me crazy today, please help! Thanks in advance

---

### Post by ajgreeny on 2018-09-13
Did you try what is advised at the end of the Boot-Info output?
```
If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
```
So try making the other disk first priority in your BIOS/UEFI setup, rather than the disk that is currently first boot device.

---

### Post by haqiu on 2018-09-13
> **ajgreeny said:**
> Did you try what is advised at the end of the Boot-Info output?
```
If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
```
So try making the other disk first priority in your BIOS/UEFI setup, rather than the disk that is currently first boot device.

I tried the advised command at the end of the Boot-Info output, it says "The operation completed successfully." Then I restarted the computer but nothing changed. It still boots directly into Windows.

I also tried putting other disk first priority in my BIOS/UEFI setup, but nothing changed.

BTW, I used the following command in Windows command line to check whether the ubuntu boot loader is succesfully installed in the efi partition. It shows there is the ubuntu directory. However as I said, in my computer's BIOS there is not even a Ubuntu option in the boot priority order.[INDENT]
*C:\WINDOWS\system32>mountvol i: /s*[/INDENT]
[INDENT]*C:\WINDOWS\system32>i:*[/INDENT]
[INDENT]*I:\>cd efi*[/INDENT]
[INDENT]*I:\EFI>dir*[/INDENT]
[INDENT]* Volume in drive I has no label.*[/INDENT]
[INDENT]* Volume Serial Number is 323E-D31B*[/INDENT]
[INDENT]* Directory of I:\EFI*[/INDENT]
[INDENT]*2018/09/12  18:06    <DIR>          .*[/INDENT]
[INDENT]*2018/09/12  18:06    <DIR>          ..*[/INDENT]
[INDENT]*2018/09/12  18:06    <DIR>          Microsoft*[/INDENT]
[INDENT]*2018/09/13  15:35    <DIR>          Boot*[/INDENT]
[INDENT]*2018/09/13  06:46    <DIR>          ubuntu*[/INDENT]
[INDENT]*               0 File(s)              0 bytes*[/INDENT]
[INDENT]*               5 Dir(s)      66,471,936 bytes free*[/INDENT]

---

### Post by ajgreeny on 2018-09-13
I should have asked this before; what computer do you have as there are several manufacturers that do not follow the accepted standards for UEFI and will not allow anything but Windows to boot without a fair bit of messing around with the boot files in the grub/UEFI bootloader.

Have a good read through the long and detailed thread at [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) in particular the section **Examples** quite a long scroll down about HP, Acer, ASUS, and several other makes.

---

### Post by haqiu on 2018-09-13
> **ajgreeny said:**
> I should have asked this before; what computer do you have as there are several manufacturers that do not follow the accepted standards for UEFI and will not allow anything but Windows to boot without a fair bit of messing around with the boot files in the grub/UEFI bootloader.

Have a good read through the long and detailed thread at [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) in particular the section **Examples** quite a long scroll down about HP, Acer, ASUS, and several other makes.

ffs, I AM using Acer... I'm reading the thread right now. It's so long...:cry:

---

### Post by oldfred on 2018-09-13
Jump to these posts.
Acer has an unique requirement of setting "trust" on the .efi boot files.
And many need UEFI update from Acer to have those settings.

These are all almost the same, just some users explain it slightly differently.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator) 
   Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by haqiu on 2018-09-13
> **oldfred said:**
> Jump to these posts.
Acer has an unique requirement of setting "trust" on the .efi boot files.
And many need UEFI update from Acer to have those settings.

These are all almost the same, just some users explain it slightly differently.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator) 
   Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

> **ajgreeny said:**
> I should have asked this before; what computer do you have as there are several manufacturers that do not follow the accepted standards for UEFI and will not allow anything but Windows to boot without a fair bit of messing around with the boot files in the grub/UEFI bootloader.

Have a good read through the long and detailed thread at [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) in particular the section **Examples** quite a long scroll down about HP, Acer, ASUS, and several other makes.

Big thanks for the help! I have successfully fixed the issue following the instructions in those thread. :P:P

---

### Post by oldfred on 2018-09-13
Glad it worked.

Change title to include Acer, so others with Acer may find it.

---

