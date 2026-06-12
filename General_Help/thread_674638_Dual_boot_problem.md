---
title: "Dual boot problem"
date: 2008-01-21
forum: General Help
---

### Post by DJSpeakeasy on 2008-01-21
Im trying to dual boot Vista and Ubuntu.  I dl the CD and it isnt corrupted.  I get to the main menu and select install Ubuntu...then it loads the kernal...then loads some set up files..then nothing.  Any ideas?  This is on a Thinkpad t61.

---

### Post by DapperMe17 on 2008-01-21
Re-burn the disk under Windows with the software program ImgBurn. Enable "verify" before you burn the ISO. Sounds like a corrupt disk.

Be sure to "defragment" Vista prior to partitioning your hard drive to enable dual-booting of Ubuntu & Windows.

---

### Post by logos34 on 2008-01-21
> **DapperMe17 said:**
> Re-burn the disk under Windows with the software program ImgBurn. Enable "verify" before you burn the ISO. Sounds like a corrupt disk.

Be sure to "defragment" Vista prior to partitioning your hard drive to enable dual-booting of Ubuntu & Windows.

+1

Also, you should shrink vista with it's own Disk management tool rather than with gparted on the install cd.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by jerrykenny on 2008-01-21
Both the above posts are VITAL   :)

My installation went very smoothly on an HP deskjet, following the procedure on the above posts, and using the alternative install cd, ie with no GUI, just the basic screen

---

### Post by Sef on 2008-01-21
Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing").

---

### Post by DJSpeakeasy on 2008-01-21
I get as far as the progress bar.  After that screen goes blank then nothing. I dont make it to the live session.  Ill try the advice and see if that works.  Thanks everybody.

---

### Post by rosegarden78 on 2008-01-21
If this is your first attempt to install:

1) verify checksums of ISO before burning
2) burn the disc as 4x speed or slower

---

### Post by DJSpeakeasy on 2008-01-27
Ok i tried all suggestions and im still having problems.  Now after I get past the initial screen, it is telling me that there was an i/o error.  Would it be easier to install ubuntu first then vista?  Maybe this wasnt meant to be...lol

---

### Post by HolyJoe on 2008-01-30
> **DJSpeakeasy said:**
> Ok i tried all suggestions and im still having problems.  Now after I get past the initial screen, it is telling me that there was an i/o error.  Would it be easier to install ubuntu first then vista?  Maybe this wasnt meant to be...lol

I had the same problem, I checksum the iso file and burn it at 4x speed.

---

### Post by danwood76 on 2008-01-30
It might be a hardware driver issue.
Try booting in safe graphics mode to see if it helps.

Does the disk check at the initial loading screen pass ok?

regards,
Danny

---

