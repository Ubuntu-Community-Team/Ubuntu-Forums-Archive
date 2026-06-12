---
title: "Asus T-100TAM Executing 'grub-install/dev.mmcblk0' Failed install 15.10"
date: 2015-12-29
forum: General Help
---

### Post by Giuseppe_ on 2015-12-29
Happens every time when it's trying to install grub, trying to do single install not dual boot with windows, must be some issue with EFI completely lost.

---

### Post by oldfred on 2015-12-29
Did you partition in advance?
With an ESP - efi system partition?

Not sure how grub is supposed to install to a memory card. With USB devices and a full install it is a bit of a hassle as USB devices only boot from /EFI/Boot/bootx64.efi. But grub does not create that.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Giuseppe_ on 2015-12-29
> **oldfred said:**
> Did you partition in advance?
With an ESP - efi system partition?

Not sure how grub is supposed to install to a memory card. With USB devices and a full install it is a bit of a hassle as USB devices only boot from /EFI/Boot/bootx64.efi. But grub does not create that.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)



I'm installing on my laptops internal storage, I can't give you the boot info cause the machine only has one USB port and wifi isn't working on the live cd, I tried fixing it but the only way to do that to install the OS first. Which in my case I can't do that, heres a list of my partitions though.[ATTACH=CONFIG]266448[/ATTACH]

---

### Post by oldfred on 2015-12-29
Is this one of the crippled 64 bit systems that has to have 32bit UEFI?
       The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)

Some are now older threads. There is 32 bit UEFI boot available, but you still have to work around as it is not standard in installer.

 [http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393](http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393)
Trying to install Ubuntu on an Acer one 10 (S1002)  32 bit
[http://ubuntuforums.org/showthread.php?t=2305272](http://ubuntuforums.org/showthread.php?t=2305272)
Instructions to install Ubuntu 14.10 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
Sound issues on Bay Trail
[http://ubuntuforums.org/showthread.php?t=2255425](http://ubuntuforums.org/showthread.php?t=2255425)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

---

### Post by Giuseppe_ on 2015-12-30
> **oldfred said:**
> Is this one of the crippled 64 bit systems that has to have 32bit UEFI?
       The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)

Some are now older threads. There is 32 bit UEFI boot available, but you still have to work around as it is not standard in installer.

 [http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393](http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393)
Trying to install Ubuntu on an Acer one 10 (S1002)  32 bit
[http://ubuntuforums.org/showthread.php?t=2305272](http://ubuntuforums.org/showthread.php?t=2305272)
Instructions to install Ubuntu 14.10 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
Sound issues on Bay Trail
[http://ubuntuforums.org/showthread.php?t=2255425](http://ubuntuforums.org/showthread.php?t=2255425)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)




I've been trying to follow this tutorial for the same exact netbook but the author made it through the installation just fine he just had to manually install something to make grub load but I can't make it to that point. He doesn't mention the installation failing on him. Here's the link to it. [http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)

---

### Post by oklokl on 2015-12-30
1. Creating the hardware environment
only disk gpt.. and.. Motherboard only EFI 

2.Checking file and usb(Check after booting via the Options ....)
```
md5sum ubuntu-15.10-desktop-amd64.iso
```
[http://releases.ubuntu.com/15.10/](http://releases.ubuntu.com/15.10/)
MD5SUMS 
(url) file hash check
 If the damage is in the download process.

How my rights
```
sudo dd if=ubuntu-15.10-desktop-amd64.iso of=/dev/sdX bs=512k

```

[http://sourceforge.net/projects/boot-repair-cd/?source=recommended](http://sourceforge.net/projects/boot-repair-cd/?source=recommended)

3. usb... (making usb)
```
mount
umount -l /dev/sdX
sudo dd if=boot-repair-disk-64bit.iso of=/dev/sdX bs=512k
sync
udisks --unmount /dev/sdX
```

or..
usb gpt..
this copy..  boot-repair iso usb..


[https://youtu.be/bVx86VbRJkQ?t=3m22s](https://youtu.be/bVx86VbRJkQ?t=3m22s)



[http://superuser.com/questions/713919/efi-gpt-windows-7-boot-loader-manager-issue-and-grub](http://superuser.com/questions/713919/efi-gpt-windows-7-boot-loader-manager-issue-and-grub)


boot-repair(If you want to recover.)
First, please repair the window completely



[COLOR=#ff0000]If completely broken.[/COLOR]
[http://en.community.dell.com/techcenter/os-applications/w/wiki/4689.how-to-create-windows-8-windows-server-2012-bootable-usb-media-for-deployment-on-uefi-based-systems](http://en.community.dell.com/techcenter/os-applications/w/wiki/4689.how-to-create-windows-8-windows-server-2012-bootable-usb-media-for-deployment-on-uefi-based-systems)
[http://www.qliktips.com/2012/11/fix-windows-8-boot-issue.html](http://www.qliktips.com/2012/11/fix-windows-8-boot-issue.html)

ms windows cd

windows boot cd (shift + F3) terminal :)

```
diskpart
list vol
exit
```

ms windows cd
```
bcdboot d:\windows /s c: /l all
bootsect /nt60 c:
```

and..
Ubuntu Recovery Solutions ..  boot-repair(start)

---

### Post by oldfred on 2015-12-30
One of the links has a link to a place to download the complied 32 bit UEFI boot files.
[https://sturmflut.github.io/linux/ubuntu/2015/02/04/installing-ubuntu-on-baytrail-tablets-version-2/](https://sturmflut.github.io/linux/ubuntu/2015/02/04/installing-ubuntu-on-baytrail-tablets-version-2/)
[http://ubuntuforums.org/showthread.php?t=2307022&page=2&p=13410393#post13410393](http://ubuntuforums.org/showthread.php?t=2307022&page=2&p=13410393#post13410393)

Most of the older links have you compiling it yourself.

---

