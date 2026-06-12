---
title: "mount: only root can mount /dev/sda1 on /media/sda1"
date: 2007-03-24
forum: General Help
---

### Post by kpjoyce on 2007-03-24
Forgive the noob question ... I have the sense that this is an easy fix, a simple permission or setting change.

I have a new install of 6.06, and the system is not automatically mounting my usb thumb drives when plugged in.  The error message is the title of the entry.

I have no problem mounting the disk via the terminal using sudo.

thank you.

---

### Post by david.rahrer on 2007-03-25
Actually, this just started happening to me and I was just looking for some information on it.  I have 6.10 and the only thing I did recently in the area of mounting is to install Automatix2's new NTFS mount/write utility.  Has anyone else run into this problem?  BTW, NTFS volumes and external drives are auto-mounting and working perfectly.  The drive that started giving me the above error is a USB Flash Drive.

---

### Post by dibble on 2007-03-25
Are you in the group plugdev (pluggable devices) - AFAIK you need to be in this to be able to mount/umount.

Jim

---

### Post by david.rahrer on 2007-03-31
Hmm, I don't find that group but one of my priveleges in user admin says I can access eternal drives automatically.  I finally uninstalled the Automaticx NTFS/FAT32 Read/Write access and everything works as before (except the NTFS Write and auto mount).  I'm going to check in their support forum again.  Thanks.

---

