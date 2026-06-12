---
title: "Ejecting Second Optical Drive"
date: 2014-02-10
forum: General Help
---

### Post by Brandon_MacEachern on 2014-02-10
This should be an easy one for you guys.

My computer case doesn't allow access to the optical drives physical buttons, and usually have to command an eject through software.  This is fine usually.

In Ubuntu, the eject hot key only controls the master drive.  Eject command in terminal is the same way.  Only controls the primary drive.

Is there any way to actually eject a second optical drive?

---

### Post by tomearp on 2014-02-10
The [man page for eject]("http://manpages.ubuntu.com/manpages/precise/man1/eject.1.html") describes how to tell the command which drive to eject. If you run the command without telling it which drive to eject it defaults to cdrom.

If you have two drives the second one will be called something different.

---

### Post by Brandon_MacEachern on 2014-02-10
> **tomearp said:**
> The [man page for eject]("http://manpages.ubuntu.com/manpages/precise/man1/eject.1.html") describes how to tell the command which drive to eject. If you run the command without telling it which drive to eject it defaults to cdrom.

If you have two drives the second one will be called something different.
Well I found two problems.  One, I didn't even know what the second drive (a bluray burner) was called.  Second, my computer booted into BIOS mode meant that particular SATA port was not accessable.  Turns out I needed grub EFI.  Installed that, booted to it, now I was able to identify the drive.

eject /dev/sr1

Appears I need a shell script to make it useable as a hot key though.

---

### Post by mörgæs on 2014-02-11
Good, please mark the thread 'solved'.

---

