---
title: "ntfs-3g causing bluescreen when booting winows?"
date: 2013-02-09
forum: General Help
---

### Post by thermion on 2013-02-09
I think there may be a bug in ntfs-3g in connection with windows 8.

I tested this with quite a few live systems, as well as normal installations on my HDD.
Every time I access a NTFS volume within linux using nfts-3g, windows 8 is unable to boot because it's nearly instantly showing a bluescreen (errorcode 0x00000018). Windows is able to boot properly, as long as I don't mount any NTFS volumes when running linux (I was even able to reproduce this in a VM).

I "googled" a bit on this subject, but ended up with results regarding windows XP and Vista. Is this a known problem? Has anyone here had similar experiences with this kind of dual-boot setup running Linux and Windows 8?

Thanks in advance!

---

### Post by oldfred on 2013-02-10
Do you still have fast boot (hibernation) still on?

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

---

### Post by thermion on 2013-02-10
No, I don't. This was the first thing I did after installing Windows 8.
I'll have a look at the other links you posted. Maybe they will help be solve this little problem.

Thanks!

---

