---
title: "Problems with fstab mounting, USB drive and bind"
date: 2007-07-21
forum: General Help
---

### Post by KristoferP on 2007-07-21
Hi!
I'm trying to mount the filesystem on my Lacie USB harddrive during boot so i can remount some of the subdirectories on that filesystem in my ftp directory. I have no problems mounting the Lacie after boot (its mounted in /media/LACIE/ and i have no problems mounting the subdirectories (using mount --bind /media/LACIE  /DIRECTORY /var/ftp/DIRECTORY). But when i try to mount it using the following lines in fstab it just does not work:
/dev/sdc /media/LACIE auto rw,user,noauto 0 0
/media/LACIE/DIRECTORY /var/ftp/DIRECTORY none bind 0 0

Is there any way to log the fstab mounting during boot? Where is that log?

I guess i could just write a script thats executed during/after boot and mounts the directories, but i would prefer not to do that

Thankfull for any advice

---

### Post by bernied on 2007-07-21
Try ```
sudo mount -v /media/LACIE
```That should tell you something.

---

### Post by bernied on 2007-07-21
After re-reading your post I realise it might not tell you anything, as you say it works perfectly after boot. Sorry.

You might find something in /var/log/dmesg (just 'sudo dmesg' to view).

---

### Post by KristoferP on 2007-07-24
Jupp, already checked dmesg, didn't really give me any information on the fstab mounting actions. Anyone else have any tips on how to log the fstab actions?
Anyone have any tips on how to force an usb harddrive to mount during boot?

---

### Post by bernied on 2007-07-24
I just spotted the noauto option in the fstab line for the device. This will prevent it mounting at boot. Change it to auto.

---

