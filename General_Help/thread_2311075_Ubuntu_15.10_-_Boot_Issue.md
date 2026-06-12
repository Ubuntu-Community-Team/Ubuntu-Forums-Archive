---
title: "Ubuntu 15.10 - Boot Issue"
date: 2016-01-24
forum: General Help
---

### Post by xkazeshinix on 2016-01-24
Today I have installed ubuntu 15.10 on my Vaio laptop, then i installed nvidia proprietary driver from "Additional Drivers" and now when i boot (screen after grub menu) it gives me following error 
```
[8.764321] intel ips 0000:00:1f.6: thermal reporting for required devices not enabled, aborting 
```
everything works well, but its annoying that screen stucks for a while slowing boot process. Can it be fixed anyway?

---

### Post by xkazeshinix on 2016-01-26
no one?

---

### Post by SantaFe on 2016-01-27
Not having either Ubuntu OR a Sony Vaio, I can't vouch this will work, but googling I found this: [https://forums.opensuse.org/showthread.php/505097-Error-at-boot-Thermal-reporting-for-required-devices-not-enabled-aborting](https://forums.opensuse.org/showthread.php/505097-Error-at-boot-Thermal-reporting-for-required-devices-not-enabled-aborting) 

It looks like the last post has some kind of answer, though.  Kinda wish he would have said where the file was.  

Hope this helps somehow.

---

### Post by xkazeshinix on 2016-01-29
Yea, how can i find this parameter :?:

---

### Post by oldfred on 2016-01-29
Are you actually booting with Intel?

This was Xeon so does not apply directly, but may be something similar?
[http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset](http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset)

With latest Intel drivers this boot parameter is not now requried. But may be worth at least trying.
 Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

---

