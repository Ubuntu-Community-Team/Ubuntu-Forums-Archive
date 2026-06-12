---
title: "School me on this HFS+ problem"
date: 2008-06-10
forum: General Help
---

### Post by TheAlmightySam on 2008-06-10
Here's the setup I've got:

Old-school x86 running 8.04 attached via USB to a HFS+ drive that used to be attached to my Mac.  It's main purpose in life is to act as a file server and storage repository.  It sends a DAAP feed using Firefly out to the rest of the network

A G4 iBook networked to it via Samba over wifi that serves as the "control unit," so to speak.

All the media I have is on the big HFS+ drive, and iTunes on the iBook can access, modify, and work with the files without issue, including deleting them, but Finder cannot delete them, although it can add, nor can an application I use to remove duplicate MP3s.

The Ubuntu terminal can add files and folders, but not delete.

I gksudo'ed into Nautilus to see if I could change the permissions on the drive, and it showed everyone having read/write permissions.  However, when I tried to change the owner/group the drive belongs to, it would not allow me to.

What's going on here, and how do I go about fixing it?  I'm afraid I'm a total Linux noob.  Thank you!

---

### Post by avtolle on 2008-06-10
From memory; you need to disable the journaling for the HFS+ files. You might check the Forum Archives under either of the Apple Users (PPC or Intel) for guidance on this, or, hopefully, someone with a lot more knowledge and information will respond.

---

### Post by TheAlmightySam on 2008-06-11
I just checked the drive in Disk Utility on the Mac, and journaling is turned off.  Permissions seem to be set correctly as well.

Please, wise Ubuntu users, help me get this sorted out :)

---

