---
title: "USB storage devides not detected"
date: 2008-06-26
forum: General Help
---

### Post by ProbablyX on 2008-06-26
Hi!

I'm using KDE 4.1 beta2, and it seems it cannot mount my camera or SD cards from my card reader.

When I plugin an external "drive", nothing happens, when I click the computer icon "Recent devices" appear but only my harddrive(s) appear there.

I checked fstab and the only non-harddrive line in it is:
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Of what I understand there should be a line for the USB device too shouldnt there?

When I plug the card reader in it blinks a quick blink and then remains "not blinking".
My HP camera just says "attempting to connect..." but nothing more.

I'm not sure if its KDE or the system, but I'm leaning towards the system...

I also tried mounting sda: says its busy
sda1: mounts a harddrive.
There is no sda2.

It's kinda weird =/

Thankful for any help! :)

---

### Post by russlar on 2008-06-26
run sudo fdisk -l, and post the results

---

### Post by ProbablyX on 2008-06-26
OK this is weird, it suddenly started working again =/
I ran an update.. might have been that.
I'm going to browse arround on my memory/camera and see if everythings OK or Ill get back :)

Thanks :)

---

### Post by ProbablyX on 2008-06-26
OK this is weird, it suddenly started working again =/
I ran an update.. might have been that.
I'm going to browse arround on my memory/camera and see if everythings OK or Ill get back :)

Thanks :)

---

