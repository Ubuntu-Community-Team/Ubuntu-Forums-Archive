---
title: "sh: 1: cannot create /proc/sys/vm/overcommit_ratio: Permission denied, command line"
date: 2013-10-19
forum: General Help
---

### Post by kturkowski on 2013-10-19
I have several command line tools (unit tests specifically) that started complaining about a week ago, with

   sh: 1: cannot create /proc/sys/vm/overcommit_ratio: Permission denied

What is going on? I never got these messages before.

I am an avid upgrader, so it was probably triggered by a system upgrade that I did about that time.
The current system is:
ubuntu 12.04 LTS
Memory: 495.5 MiB
Prtocessor: Intel® Core™ i5 CPU M 540 @ 2.53GHz 
Graphics: Unknown
OS Type: 32-bit
Disk: 32.4 GB
running in VMWare Fusion 5.0.3
on a Mac Book Pro with 4 Gb memory.

Do I need to add more memory or disk space?
Do I need to echo 1000000 > /proc/sys/vm/overcommit_ratio?
Or what?

-Ken

---

### Post by Gyokuro on 2013-10-19
The information in /proc get exported from the kernel and in your case case the overcommit_ratio is in % which goes from 0 up to 100 (standard is 50) to change the value you should do this via sudo echo. Your value is high maybe you mean overcommit_memory??

---

