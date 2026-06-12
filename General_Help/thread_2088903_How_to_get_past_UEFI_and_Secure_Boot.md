---
title: "How to get past UEFI and Secure Boot?"
date: 2012-11-27
forum: General Help
---

### Post by ublondie on 2012-11-27
After buying a new laptop with Win8 pre installed, making a liveUSB with Ubuntu 12.10, I brutally learn about new UEFI and Secure Boot ....and no matter what I try, I cannot get the laptop to boot from the USB!!

Am so frustrated...

I have tried adjusting various BIOS options including turning Secure Boot off and adjusting the UEFI settings, as well as making sure that USB is listed as first item in the boot order menu (but this is prefixed with [UEFI...] but nothing works!

I used the Universal USB Installer (from pendrivelinux site) to create the live USB, which is also that recommend on the Ubuntu website.

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

Can someone help with how you get around this please?

---

### Post by coffeecat on 2012-11-27
Did you use the 32-bit or 64-bit Ubuntu ISO? You need to use the 64-bit. The 32-bit version cannot boot in efi mode.

A useful link for you:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2012-11-27
What computer. Some work without much issue, some have issues like video or other, and some just do not work as it has a UEFI bug.

       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

    
In addition to coffeecat's link.

       [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
    
       Dual-boot Windows 8 and Ubuntu 12.10 on UEFI hardware
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)
    
       Acer V5-571P-6815 secure boot off worked
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Windows 8 & Ubuntu worked
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

---

### Post by ublondie on 2012-11-28
Thanks guys...

It is 64bit and I have a Samsung NP535U3C

I'll have a look at the links you posted, but if you have any other ideas in the meantime, please let me know.

---

### Post by ublondie on 2012-11-28
Hi again.... ok, got it working

The link you provided coffeecat provided me with what was helpful. Thanks.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I downloaded the 'Ubuntu-Secure-Remix' and re-did the Live USB with that iso, using Unetbootin

When I checked the BIOS (with the USB plugged in) there were two new items on the Boot List that weren't there previously. The USB (and something else) was added, but this time without the UEFI prefix also.

It has not booted and all good. Thank you.

---

### Post by ublondie on 2012-11-28
...how do I mark this as SOLVED ??

---

### Post by coffeecat on 2012-11-28
Glad you got it fixed.

> **ublondie said:**
> ...how do I mark this as SOLVED ??

Just above the top of the thread you'll see a dropdown called "Thread Tools". "Mark this thread as solved" in that list.

Good luck with your dual-boot.

One other thing you need to know about Windows 8/Ubuntu dual-booting - if you are saving files to a NTFS partition from Ubuntu - is the hybrid hybernation/shutdown that Windows 8 uses by default. This can lead to loss of all files saved by Ubuntu. See this thread for more:

[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)

The last post has a link for how to disable Windows 8 fast startup.

---

### Post by ublondie on 2012-11-28
Thanks for the heads up.  Is this something new to Windows 8?  ...I haven't had issues in the past when dual booting with Ubuntu (and Win 7) and saving files to the NTFS partition.

Maybe it's just best to keep the files separate (or multiple copies at least). I tend to use Linux most of the time anyway and pretty much only use Windows for iTunes!  :/

Thanks for the help

---

### Post by oldfred on 2012-11-28
I think it is best not to hibernate.

But I also used a shared NTFS data partition when I used to boot XP a lot. Then set the system partition as read-only to avoid errors. But if file is open in Windows and then Windows is hibernated, you still will get corruption if you try to do something in Ubuntu with that file.

The Linux NTFS driver shows all Windows files & folders like Windows does when you unhide system files. I always used to unhide those files but then managed to damage system too often when clicking and moving mouse too fast and dragging an essential folder someplace where it did not belong.

---

### Post by coffeecat on 2012-11-28
> **ublondie said:**
> Is this something new to Windows 8?  ...I haven't had issues in the past when dual booting with Ubuntu (and Win 7) and saving files to the NTFS partition.

You will have issues if you hibernate Windows 7 and then save files from Ubuntu. What's new in Windows 8 is that it has a hybrid hibernate/shutdown. If you shut Windows 8 completely and then restart the machine, boot into Ubuntu and save files from Ubuntu you'll probably run into this issue. I *believe* that if you do a restart from Windows 8, it shuts down properly and you don't see the problem.

---

### Post by ublondie on 2012-11-28
Thank you. Will bare it all in mind :)

---

