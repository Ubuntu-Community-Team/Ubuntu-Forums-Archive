---
title: "booting problems"
date: 2007-02-16
forum: General Help
---

### Post by jbob286 on 2007-02-16
After seeing this article on linux.com:

[http://applications.linux.com/applications/07/02/02/2117209.shtml?tid=47&tid=121](http://applications.linux.com/applications/07/02/02/2117209.shtml?tid=47&tid=121)

I followed the intstructions and ran his suspend.sh script after installing uswsusp. After trying to suspend to ram and it failing, I restarted and got this error message after the kernel was loaded by lilo:

```

RAMDISK: Compressed image found at block 0
invalid compressed format (err=1)
VFS: Cannot open root device "804" or unknown-block (8,4)
Please append a correct "root" boot option
Kernel panic - not syncing: VFS: unable to mount root fs in unknown-block (8,4)

```

I have checked my lilo.conf and it is still correct. How do I keep it from trying to read this failed ramdisk?

---

### Post by jbob286 on 2007-02-16
Help please!

---

### Post by jbob286 on 2007-02-16
anyone? :(

On a side note, how do I keep myself from ruining my installation all the time? This is the 4th time or so... any simple guidelines to follow?

---

