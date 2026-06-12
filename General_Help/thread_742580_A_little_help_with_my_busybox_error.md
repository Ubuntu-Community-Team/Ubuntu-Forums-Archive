---
title: "A little help with my busybox error"
date: 2008-04-01
forum: General Help
---

### Post by smokingwreckage on 2008-04-01
After viewing several threads about the error, and possibly determining that mine is different, i lay my problem before you...
   I have just used Wubi to install 8.04 onto my Vista 64 bit machine, all went well on the windows end but i am getting a busybox error when trying to boot into ubuntu. All of the threads on this issue seemed to involve raid 0, or partitioned drives. I am using a raid0 setup as D but both windows and the ubuntu install are on C which is not a raid array or partitioned in any way.
   The cat /casper.log command (thanks Ago) ended with lots of "cannot mount /dev/sdb1 on /isodevice"
   Any help would be greatly appreciated.  i'm completely new to linux and would love to safely give it a go without killing my windows install (i game).

---

### Post by ago on 2008-04-02
grep sda /casper.log

---

### Post by smokingwreckage on 2008-04-02
Just tried it and i didnt see anything that looked like an error message, but i dont know what i'm looking at. Is there a way to get to any of this information from within windows, or should i grab a pen and jot all this stuff down?

---

### Post by smokingwreckage on 2008-04-02
Got to looking at the cat /casper.log and saw something odd (but again i really dont know what i'm looking at).
i believe it went something like "FSTYPE unknown" followed by "FSSIZE 0".
A little googling led me to believe this has to do with the file system, which is NTFS. No clue if thats helpful.

---

