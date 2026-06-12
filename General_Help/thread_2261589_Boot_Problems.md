---
title: "Boot Problems"
date: 2015-01-20
forum: General Help
---

### Post by ceil210 on 2015-01-20
I recently used the 14.04 wubi.  Installation went swimmingly, but I can't boot into Ubuntu!  Here is the error I get on bootup:

```
\ubuntu\winboot\wubildr.mbr
0xc0000007b
```

Any help is appreciated!

Thanks, Alex

---

### Post by yancek on 2015-01-20
Wubi is no longer supported and is not expected to work if you have windows 8.  Do you?  See the wubi page below.  I've read posts of people getting it to work so you might be able to.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by oldfred on 2015-01-20
Because all new systems with Windows 8 use UEFI with gpt and wubi does not work with gpt partitioning, wubi is not supported anymore. Last supported version was 12.04.

Better to install full partitioned version, or run live installer in live mode, or install to an external hard drive or flash drive if do not want to modify existing partitions.

 Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

