---
title: "USB VFAT Drive and NFS"
date: 2007-05-07
forum: General Help
---

### Post by ratovan on 2007-05-07
I have a 320GB external drive attached to Ubuntu 7.04.  I want to be able to access it through NFS from a Fedora Core 6 machine also.

I added it to /etc/exports but the other machine can't access it.

I noticed that in /media the permission given to the USB drive are

drwx------ 76 scott root 32768 1969-12-31 19:00 USB-HDD

How can I add other permissions to this.  chmod doesn't work.

Thanks

---

