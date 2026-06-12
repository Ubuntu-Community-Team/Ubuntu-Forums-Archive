---
title: "dd'ing  gpt disk"
date: 2013-04-10
forum: General Help
---

### Post by Ceiber Boy on 2013-04-10
Is cloning a GPT disk different to cloning a MBR disk with dd?

Can a GPT clone be dd'ed to a clean unformatted disk?

---

### Post by oldfred on 2013-04-10
Not partitions, nor from MBR to gpt.

 Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)
Do not use dd with gpt partitions. Whole drive ok if old drive not used anymore, or no duplicates.
But do not use dd for copies from MBR to gpt partitioned drives
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)

---

