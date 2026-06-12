---
title: "Usplash switches to text mode"
date: 2006-09-12
forum: General Help
---

### Post by Köntzä on 2006-09-12
Hi there!

I added a second hard drive to my computer. Since doing that usplash has started switching back to text mode at some point during boot up. It happens at about the time when boot process checks the second drive's journal (ReiserFS in use).

I've tried looking for help on usplash, but they mainly focus on adding a new  image for the splash screen.

Any ideas?

---

### Post by wieman01 on 2006-09-12
This is probably because of some error occurring during startup. Check this file which should tell what the problem is:

> /var/log/boot.log

...or similar (cannot tell for sure what the file is called because I have disabled logging). After eliminating the error your USplash should stay up until GDM starts.

---

### Post by Köntzä on 2006-09-12
Hi,

Tried enabling boot logging but got nothing out of it. There are no files looking like /var/log/boot*.* after reboot. I grepped dmesg's output for the word error, but found nothing. Also, dmesg's output for ReiserFS checking hda1-7, and hdb1 were all identical. So no errors there.

--
Köntzä

---

### Post by wieman01 on 2006-09-12
Mmm... Perhaps you have not enabled the right program. Not sure but this is as much as I can say. Try to find out what kind of error occurs while the computer boots. Can you tell from the boot-screen what's going on and what might be the problem"

USplash can be a pain as on occasion it does not deal correctly with failed services, etc.

---

### Post by Köntzä on 2006-09-17
Hi there,

I filed a bug about this on Launchpad. I got a reply that this was already filed as a bug, and that original bug's ([https://launchpad.net/bugs/22658]("https://launchpad.net/bugs/22658")) discussion on Launchpad gave a hint to change usplash's timeout.

This is what I did, as per suggestion:
I created a file /etc/rcS.d/S29usplash_timeout.sh and its contents are
-- clip here --
#!/bin/sh
/sbin/usplash_write "TIMEOUT 60"
-- clip here --

I hope the above info will help others with the same problem.
--
kontza

---

### Post by kkellner on 2006-11-04
thank you - that worked perfectly.  I couldn't figure out why usplash was always giving up until I realized it was my giant new external hd.

---

