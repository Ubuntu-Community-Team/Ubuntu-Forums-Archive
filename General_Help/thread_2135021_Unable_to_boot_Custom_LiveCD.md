---
title: "Unable to boot Custom LiveCD"
date: 2013-04-12
forum: General Help
---

### Post by jefflarkin on 2013-04-12
Hi all. I've been trying to build a custom livecd with certain drivers and software that I need. I've followed various tutorials around the help wiki and these forums, including:

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
and
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

I'm able to generate an iso with either isolinux or grub installed as a bootloader (I've tried both) and all the various pieces in place, but it fails to boot. In each case the boot process ends with 

```
Begin: Running /scripts/init-bottom ... done.
init: container-detect pre-start process(671) terminated with status 127
mountall: Event failed.
```

In some cases I notice failed mount attempts for paths in the format of /root/foo (as opposed to just /foo). I'm wondering if the "/root" is the key to my problems. I've followed the steps very carefully multiple times (and with multiple, similar tutorials), but always end up in the same place. I'm using 12.10 (i386) as my starting point. Has anyone else attempted to build a custom livecd from 12.10 or hit this same boot problems?

Thanks

---

