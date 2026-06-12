---
title: "Ubuntu Live Persistence Full - Unable to login"
date: 2023-08-05
forum: General Help
---

### Post by ravirajbasis on 2023-08-05
Hi

I have Ubuntu 23.04 Live on USB with 4 GB persistence.

While installing software received an error that persistence space full.

Now i am unable to login there! Error message before login screen "systemd-journal cannot create user as space is full".

Is it possible to login or delete space using bleachbit installed there?

Thanks
rraj

---

### Post by Xian on 2023-08-05
Journal logs can easily take up several GB's.

Ubuntu Handbook article: [https://ubuntuhandbook.org/index.php/2020/12/clear-systemd-journal-logs-ubuntu/](https://ubuntuhandbook.org/index.php/2020/12/clear-systemd-journal-logs-ubuntu/)

---

### Post by yancek on 2023-08-06
Do you have an installed Linux OS on the computer or another Linux USB/DVD?  If so, you can boot it and delete log files on this the referenced persistent USB.

---

### Post by HermanAB on 2023-08-07
In general, boot with install media, mount the persistent USB widget, navigate to /var/log and delete everything.  Important log files will be recreated next time the system starts up.

BTW, rather than using the Live with Persistance thing, you could just do a normal install to a USB widget or SD card - it works much better.

---

### Post by ravirajbasis on 2023-08-07
Hi

Thanks for reply!

Deleted journal logs, still not able to get past login screen!

Now new error appears “failed to start apt-daily-upgrade.service 
Failed to start [email]tor@default.servic[/email]e”

Thanks 
rraj

---

### Post by ravirajbasis on 2023-08-09
Hi

Contents of dmesg the day issue happened

===============================================
ubuntu@ubuntu:/var/log$ cat dmesg.0 | grep error
[    0.317677] kernel: ACPI Error: Aborting method \_PR.CPU0._PDC due to previous error (AE_AML_OPERAND_TYPE) (20221020/psparse-529)
[   17.722138] kernel: spi-nor: probe of spi0.0 failed with error -22
===============================================
ubuntu@ubuntu:/var/log$ cat dmesg.0 | grep Error
[    0.317568] kernel: ACPI Error: Needed type [Reference], found [Integer] (____ptrval____) (20221020/exresop-66)
[    0.317614] kernel: ACPI Error: AE_AML_OPERAND_TYPE, While resolving operands for [Store] (20221020/dswexec-433)
[    0.317677] kernel: ACPI Error: Aborting method \_PR.CPU0._PDC due to previous error (AE_AML_OPERAND_TYPE) (20221020/psparse-529)
[    0.523183] kernel: RAS: Correctable Errors collector initialized.
===============================================

How to resolve these error?

Thanks
rraj

---

### Post by ravirajbasis on 2023-08-09
> **yancek said:**
> Do you have an installed Linux OS on the computer or another Linux USB/DVD?  If so, you can boot it and delete log files on this the referenced persistent USB.

Hi

Used ubuntu live on same USB but different persistence, to delete log files. But no luck!

Different error before login, [Failed] failed to start <service>.

Thanks
rraj

---

### Post by sudodus on 2023-08-09
I suggest that you boot into another system, connect the failing persistent live system and copy all the files that you want to keep (documents, pictures etc) to a backup drive. Then I suggest that you get a bigger drive (USB pendrive or USB-connected SSD) and make a fresh persistent live system or portable installed system in that drive. (Today 4 GB for persistence won't last long because the application software is growing, particularly if you use snaps).

Please make backups regularly in order to manage hardware and/or software failures in the future.

---

### Post by ravirajbasis on 2023-08-10
Hi

Thanks for reply!

Is it possible to do a terminal login (devoid of GUI)?

ALT+CTRL+F3/F4/F7 does not work!

Thanks
rraj

---

### Post by sudodus on 2023-08-10
It should be possible to switch to text mode that way, but when the system is corrupted, that might no longer work.

Have you got another Ubuntu system running (in another computer)? Have you got another drive (for example another USB drive) or can you get or borrow such a drive? In that case it is much easier to save files that you want to save (and can save) when booted from another Ubuntu system. And then simply create a fresh system in this problematic USB drive, and then prepare more than 4 GB for persistence.

If you want a text mode interface, you can install Ubuntu Server, for example according to [this link](https://ubuntuforums.org/showthread.php?t=2474692). Please read the whole thread before using the method (and I recommend to use the current LTS version, 22.04.x, "Jammy").

---

### Post by sudodus on 2023-08-11
If you have no other Linux system, it should be possible to boot into your system on the USB drive live-only (without persistence). At the grub menu you can edit the 'linux line' by removing the boot option 'persistent'.

Then it should run just like an ordinary live system, and you can remove the content of the 'writable' partition, and after that start all over to configure your persistent live system.

Warning:

If you want to save some personal files, and the file system works so that they are available, you should do that before removing the content of  the 'writable' partition.

---

### Post by ravirajbasis on 2023-08-14
> **sudodus said:**
> It should be possible to switch to text mode that way, but when the system is corrupted, that might no longer work.

Have you got another Ubuntu system running (in another computer)? Have you got another drive (for example another USB drive) or can you get or borrow such a drive? In that case it is much easier to save files that you want to save (and can save) when booted from another Ubuntu system. And then simply create a fresh system in this problematic USB drive, and then prepare more than 4 GB for persistence.

If you want a text mode interface, you can install Ubuntu Server, for example according to [this link]("https://ubuntuforums.org/showthread.php?t=2474692"). Please read the whole thread before using the method (and I recommend to use the current LTS version, 22.04.x, "Jammy").

Hi

I have two live usb's with linux(debian) installed. What to do with it?

I believe i can uninstall the problematic package, if i am able to do a text (terminal) login. But the issue is i can't!

If nothing works guess will have to do a reinstall.

Thanks
rraj

---

### Post by sudodus on 2023-08-14
It is difficult to repair a full persistent live system. This is why I recommend reinstalling instead. And I recommend using a partition for persistence, and to use a USB drive with at least 15 GB and use as much drive space as possible for the partition for persistence.

You can install [mkusb](https://help.ubuntu.com/community/mkusb) in a linux system and use it to create a persistent live drive or [Rufus](https://rufus.ie) in Windows for that purpose.

---

### Post by #&amp;thj^% on 2023-08-14
> **sudodus said:**
> It is difficult to repair a full persistent live system. This is why I recommend reinstalling instead. And I recommend using a partition for persistence, and to use a USB drive with at least 15 GB and use as much drive space as possible for the partition for persistence.



+1 I too prefer 15-16 Gig installs, you taught me well sudodus. :)

---

### Post by HermanAB on 2023-08-16
If you are using the live system on a single machine, then it is best to just do a normal install to the USB widget.

---

