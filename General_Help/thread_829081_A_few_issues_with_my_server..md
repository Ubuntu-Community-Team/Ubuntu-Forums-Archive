---
title: "A few issues with my server."
date: 2008-06-14
forum: General Help
---

### Post by EmanresuusernamE on 2008-06-14
I recently installed Ubuntu Server on an old machine of mine so that I could run a web server or three from my home.  What I'm trying to do now is give it FTP capabilities, (which I thought I did when I installed Ubuntu).  I installed Ubuntu Server on a USB drive so that it's easy to remove and so that it's not consistently eating up electricity to keep the drive spinning, (Ubuntu can be very green :)...... (I'm also not tempted to put a bunch of junk on the server with it only being a 4G jumpdrive). 

Here's issue 1: I cannot install vsftpd right now because it asks me for the CD whenever I do apt-get. I've tried to remove the portion of the lists to bypass the CD and download it, however when I do that, it says that apt-get cannot find the package for it.  I know it can find it when it tries to look for it with the CD but then it asks for the CD and won't budge afterwards.

Here's issue 2: I cannot mount the cd because /dev/scd0 does not exist, fact is the only block device listed in /dev is my USB drive that I installed Ubuntu Server on.  I've tried using /dev/MAKEDEV to put the CD rom back into the with no luck.  I also tried using the noacpi (sp) and acpi=no (sp) that where suggested in other forums, but that doesn't work as my server won't boot up then, (at least I think it won't boot up, I'm not sure, I removed the monitor and have been doing everything remotely).

---

### Post by HermanAB on 2008-06-14
Find the vsftpd or proftpd .deb package, copy it to the server by any means - ssh, ftp, usb stick... then use dpkg to install the package.  See 'man dpkg' for details.

---

### Post by spiderbatdad on 2008-06-14
It sounds like you may have gone too far in editing sources.list.
You should only comment out the line referencing the cd. In my case ot looks like this:```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20071129.3)]/ hardy main restricted
```

---

### Post by EmanresuusernamE on 2008-06-14
> **spiderbatdad said:**
> It sounds like you may have gone too far in editing sources.list.

:( That's the only line I took out.  I left the rest alone.

[QUOTE=HermanAB]Find the vsftpd or proftpd .deb package, copy it to the server by any means - ssh, ftp, usb stick... then use dpkg to install the package. See 'man dpkg' for details.[/QUOTE]
AHHH, many thanks that worked wonderfully.  :D  Didn't know about dpkg until now.

---

