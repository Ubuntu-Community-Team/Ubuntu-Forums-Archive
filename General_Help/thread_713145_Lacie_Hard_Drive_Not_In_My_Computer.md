---
title: "Lacie Hard Drive Not In My Computer"
date: 2008-03-02
forum: General Help
---

### Post by M4v3r1kk on 2008-03-02
I have [this]("http://www.lacie.com/ca/support/support_manifest.htm?id=10282") Lacie External 500GB Hard Drive. My problem is that I cannot see it in *My Computer*. The device is visible in* Device Manager* and *Safely Remove Hardware*. It is up to date with all drivers.

I believe this could be because the driver is empty of all information due to me formatting it with Ubuntu. This can impact it as the driver is suppose to format itself with its files after first connecting to a computer. Can someone find me this software if it is the issue?

---

### Post by red_Marvin on 2008-03-02
If you formatted it with ubuntu there's a chance you formatted it to use the ext3 file system format, which windows can't read natively.
(But there are ways to make windows read and write ext3, I have however not done it, so I can't really help you, but I've heard about some windows drivers being available on sourceforge.net)

To check if it's ext3, plug it in (in ubuntu (it still works in ubuntu, right?)) and when the icon pops up on the desktop, right click on it and choose properties.
Then go to the volume tab (the last one) and you should be able to see what file system type it uses.

---

### Post by M4v3r1kk on 2008-03-02
Yet it is ext3. But it's to late now. I'm going to return it for a better model anyways.

---

### Post by M4v3r1kk on 2008-03-02
How can I reformat it to NTFS or w/e Vista reads.

---

### Post by M4v3r1kk on 2008-03-02
Anyone?

---

### Post by wednesday allfather on 2008-03-02
Format the drive to FAT32.  Windows likes that.

---

### Post by wednesday allfather on 2008-03-02
I forgot the "How" part.  If Ubuntu is the OS you are going to use to format the drive, open "gparted" aka "Partition Editor" and choose FAT32 instead of ext3.

---

