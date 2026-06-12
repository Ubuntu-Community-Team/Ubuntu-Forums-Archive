---
title: "ext4 formatted to ntfs how to restore data from prev ext4"
date: 2013-05-19
forum: General Help
---

### Post by geripgeri on 2013-05-19
Hello, unfortunately with a bad click my ext4 (home) particion is  formatted to nfts.

How can I restore my data from previous ext4 partition?

Thanks in advance
Geri

---

### Post by ajgreeny on 2013-05-19
Use a live system, install and run testdisk which should be able to restore the old partition.  Do not use that partition in any way, or you may cause more problems in restoration of the old partition

I have never needed to use this so unfortunately, I can not give you any more details.

---

### Post by geripgeri on 2013-05-20
I tried the deep search in testdisk, but unfortunately nothing...

---

### Post by zero2xiii on 2013-05-20
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Also ext4 is not easily recoverable to begin with.. See why here:
[http://askubuntu.com/questions/41601/is-there-any-recovery-software-available-for-ext4](http://askubuntu.com/questions/41601/is-there-any-recovery-software-available-for-ext4)

A few years... uhh, months ago there weren't even tools that could recover ext4 lost files.

testdisk is the best way, but if it fails for you I HIGHLY doubt you will be able to recover it without professional help. (See manual block specification etc in the first link as to why).

But I do wish you good luck.

---

