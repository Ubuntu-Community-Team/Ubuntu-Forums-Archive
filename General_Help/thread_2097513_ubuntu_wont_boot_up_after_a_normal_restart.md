---
title: "ubuntu wont boot up after a normal restart"
date: 2012-12-23
forum: General Help
---

### Post by phinsil6 on 2012-12-23
Recently I restarted my perfectly fine ubuntu 12.04 computer. only to find when it came back up that it was reporting a disk boot failure. after searching and troubleshooting a lot, it seems i have a bad superblock. so i tried the following three tutorials:
[http://erikimh.com/linux-recover-cor...ad-superblock/](http://erikimh.com/linux-recover-cor...ad-superblock/)
[http://www.cyberciti.biz/faq/linux-l...tions-command/](http://www.cyberciti.biz/faq/linux-l...tions-command/)
[http://www.cyberciti.biz/tips/surviv...-failures.html](http://www.cyberciti.biz/tips/surviv...-failures.html)
None of them worked, every suberblock i tried said that it couldn't read it. many of them said, could it be a zero length partition. Can somebody please help me out. I have about 150gb of videos on there that i would really not like to lose.

Thanks,
phinsil6

---

### Post by dino99 on 2012-12-23
if you can boot on a livecd (liveusb), then run fsck on the partition(s) supposed to be affected.

but you can also try to boot in recovery mode (hold "shift" key down at bios end process to see the grub menu on a single OS installation), then select to repair the system.

---

### Post by ranger1021994 on 2012-12-23
> **phinsil6 said:**
> Recently I restarted my perfectly fine ubuntu 12.04 computer. only to find when it came back up that it was reporting a disk boot failure. after searching and troubleshooting a lot, it seems i have a bad superblock. so i tried the following three tutorials:
[http://erikimh.com/linux-recover-cor...ad-superblock/](http://erikimh.com/linux-recover-cor...ad-superblock/)
[http://www.cyberciti.biz/faq/linux-l...tions-command/](http://www.cyberciti.biz/faq/linux-l...tions-command/)
[http://www.cyberciti.biz/tips/surviv...-failures.html](http://www.cyberciti.biz/tips/surviv...-failures.html)
None of them worked, every suberblock i tried said that it couldn't read it. many of them said, could it be a zero length partition. Can somebody please help me out. I have about 150gb of videos on there that i would really not like to lose.

Thanks,
phinsil6


try this ? :
[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

---

