---
title: "Issues with UEFI and startup disk"
date: 2013-12-08
forum: General Help
---

### Post by itsljallday on 2013-12-08
After hours of searching and trying different things I have yielded no results and need help figuring this out. 

I got a new dell inspiron laptop, intel pentium processor. Its my first computer with a efi bootloader. As soon as it was out of the box I was installing Ubuntu Gnome remix 13.10. I booted from usb created by unetbootin from a Windows 8 prompt. It booted and installed. As I hate windows 8 I felt no reservations in keeping it so I wiped it clean for ubuntu. Well now Im trying to install a different distro, specifically pinguy. I have tried creating a usb with unetbootin. It gets ignored. usb-creator won't pick up the iso file at all. burned to disc gets ignored. there is no boot order in the setup menu. I don't want to change to legacy because I know ubuntu suports efi. Any help would be appreciated, Ive read countless articles and forum posts and can't find anyone else having the same issue.

---

### Post by jeremy1701 on 2013-12-08
Do you have secure boot disabled in your BIOS? Are you using the 64-bit Pinguy ISO? 12.04 was not as stabled as more updated distros for UEFI support (13.04 and 13.10).

---

### Post by itsljallday on 2013-12-08
I do have secure boot disabled, I did that before original ubuntu install. I am using an x86_64 version of pinguy. I've done many bios installs of linux. I tried using efibootmgr to boot into usb and it returned with error system not set up for usb install

---

### Post by oldfred on 2013-12-09
Lots of Dell installs.

 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
[http://ubuntuforums.org/showthread.php?t=2179297](http://ubuntuforums.org/showthread.php?t=2179297)

---

### Post by itsljallday on 2013-12-09
I checked out your links, especially the one about the dell inspiron as its closest to my laptop. But none address my issue of my uefi ignoring my install media, usb and DVD, and boots into ubuntu gnome remix instead. I can get to a grub menu, but it lacks the boot options for my install media too.

Edit: Since original post I've redownloaded pinguy 13.10, was able to use usb-creator finally and made another usb boot drive with it, but its still ignored and boots ugr.

---

### Post by oldfred on 2013-12-09
Is UEFI/BIOS most current version from Dell? Vendors are also updating UEFI to fix various things.

Are you sure download was good and it was correctly installed to flash drive. Some combinations of installers or flash drives just seem to have issues.

       [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM

      [/URL]
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    [URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]
 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
Common USB BIOS boot options
[http://www.pendrivelinux.com/usb-bios-boot-options/](http://www.pendrivelinux.com/usb-bios-boot-options/)
Some ISO writers truncate to 64 char, fix perl script to rename
[http://cirrus.ucsd.edu/~pierce/fix_ubuntu_usb/](http://cirrus.ucsd.edu/~pierce/fix_ubuntu_usb/)

[URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]

---

### Post by itsljallday on 2013-12-09
I did not update the uefi/bios before installing ugr, I assume its a windows exe intsall package? I just tried using efibootmgr to boot to efi usb, I get this error: System not set up for USB boot. Please select another option throught the boot manager menu. Ive used unetbootin for awhile on normal bios systems, but through my forum searches ive read posts saying unetbootin wasn't suitable for uefi and to try usb-creator instead.

---

