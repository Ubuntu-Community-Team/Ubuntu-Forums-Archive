---
title: "Crashes overnight"
date: 2006-11-21
forum: General Help
---

### Post by TWitek on 2006-11-21
Hello,

first of all, i'm not very experienced with Linux, so please don't bite me. :) 

I used VMWare Server 1.01 to install 6.06.1-server-i386.
Other programs i installed include VMWare-Tools, Webmin, Squid, Squidguard, Apache2 and webtunnel.

Actually, everything is running fine. But when i check the system in the morning, it crashed overnight. This happend two times in a row now. I cannot use Shift-PageUp to lookup the complete error message, the error is not in the logfiles in /var/log (i tried e.g. with "grep -e lock_buffer *") and i only have this screenshot:

[IMG]http://www.cosconeu.com/crash.gif[/IMG]

Does this have something to do with power saving settings which maybe conflict with VMWare?

Please help me. :frown:

Best regards,
Thomas Witek

---

### Post by yopnono on 2006-11-21
Have never use ubuntu under WM. 
Anyhow, on my dapper I did need to add this to xorg.conf do make it resume from suspend.

Option  "VBERestore"  "true"

In the section "device".

---

### Post by TWitek on 2006-11-21
Dear yopnono,

thanks for the tip, but i don't have any x-window system installed, because i use the server version.

Somebody another idea, please? It seems to have something to do with EXT3, but what?
Is there some trouble with VMWare-SCSI, EXT3 and 6.06.1 LTS?

Best regards,
Thomas

---

### Post by TWitek on 2006-11-21
Just for info -- the filesystem:

proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


When i try to use "fdisk -l" nothing happends. "fdisk -l /dev/sda1" and "fdisk -l /dev/sda" give the error message: "Cannot open /dev/sda1".
Isn't this supposed to work?

Best regards,
Thomas

---

