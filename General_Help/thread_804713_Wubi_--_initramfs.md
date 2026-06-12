---
title: "Wubi -- initramfs"
date: 2008-05-23
forum: General Help
---

### Post by jclomp on 2008-05-23
Wubi sounds like a brilliant idea -- but it does not work -- not for me anyway!  In the first place, when I first tried to install it, Zone Alarm reported some trojans.  With some misgivings, I disabled Zone Alarm and succeeded in installing Wubi.  I then rebooted and chose "Ubuntu" at the boot menu.  I then got an "Ubuntu" screen, then a terminal window which stuck at "initramfs".  What am I doing wrong (or, perhaps, what is Wubi doing wrong)???

---

### Post by ago on 2008-05-24
> **jclomp said:**
> In the first place, when I first tried to install it, Zone Alarm reported some trojans.
That is a Zone Alarm problem, nothing to do with Wubi...

> I then got an "Ubuntu" screen, then a terminal window which stuck at "initramfs".  What am I doing wrong (or, perhaps, what is Wubi doing wrong)???

Did you use a DVD or alternate ISO? Did you install it in raid array/encrypted setup? Do you have multiple disks?

If the answer is NO, try to run chkdsk /r from within the partition where you installed wubi, if that is still an issue then press ESC after "Ubuntu" at boot and selects the other options.

---

### Post by blueorder on 2008-05-24
> **jclomp said:**
> I then got an "Ubuntu" screen, then a terminal window which stuck at "initramfs".

I had issues with initramfs and Hardy LiveCD. It might be the same issue I was having. Check out [this post]("http://ubuntuforums.org/showpost.php?p=4576776&postcount=6"). This is my post with the error I was getting and a "work around" I found to get it to boot.

---

### Post by jackhe22 on 2008-05-28
Easy!,
Uninstall Wubi,
Disable ZoneAlarm,
Install Wubi.. STOP! Dont reboot.
edit c:\ubuntu\disks\boot\grub\menu.lst (If C:\Ubuntu dosent exist go to: C:\Wubi\Disks\boot\grub\menu.lst
2. replace "quiet splash" with "all_generic_ide"
3. reboot
4. Ubuntu Install!

---

### Post by ago on 2008-05-28
5. submit a bug report in launchpad so that the workarounds won't be needed in the future ;)

---

