---
title: "volumes disappear from desktop after reboot"
date: 2008-04-30
forum: General Help
---

### Post by vaskark on 2008-04-30
I have 2 partitions that I like having on my desktop, but when i reboot and log back in they disappear (even though they are still listed in the Places menu). Is there a way to fix this? I do have volumes_visible checked in /apps/nautilus/desktop in Configuration Editor.

Thanks.

---

### Post by TeoBigusGeekus on 2008-04-30
Volumes appear only when you mount them, i.e. select them from the Places menu.
If you want them to be mounted whenever you boot, you need to add entries for them to your fstab file.
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Barriehie on 2008-04-30
This entry in my fstab file keeps my backup partition on the desktop.  With the trailing 0 though I check the files with fsck every so often.  Backup file is usually large enough to create an error; still working on that one.

```
/dev/hdb1 /home/barrie/disk ext3 rw,noauto,user,exec 0 0
```Barrie

---

### Post by TeoBigusGeekus on 2008-04-30
If you change your last 0 to 2, the volume will be checked for errors every time your root partition is.

---

### Post by Barriehie on 2008-04-30
Thank you, I've been having some issue with the backup file being corrupted.  Haven't had time to 'fix' it yet so I'm backing up each dir and so far so good!

Barrie

---

