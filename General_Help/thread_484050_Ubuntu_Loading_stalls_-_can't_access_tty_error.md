---
title: "Ubuntu Loading stalls - can't access tty error"
date: 2007-06-25
forum: General Help
---

### Post by Marcus522 on 2007-06-25
Downloaded the latest wubi which got me farther that the test versions. Have a RAID0 array and the test versions came up with errors. Latest version appears to install but when it reboots and the splash screen comes on Ubuntu stops loading. Eventually I get an error that says can't find tty. Downloaded this twice and still the same error. Any help?

---

### Post by ago on 2007-06-25
can't access tty error is not the actual error, the error is "before". You may want to start Ubuntu in verbose mode (delete quiet splash from c:\wubi\boot\grub\menu.lst) or look at the logs (/var/log).

---

### Post by Marcus522 on 2007-06-27
Tried the first suggestion with negative results. I don't know enough about this when I read the logs. I see what appear to be errors but they are followed by "success". I could post them if someone had the time to look. Tried the install on another Dell XPS with a RAID array and came up with the same problem. Thanks for the help. I use Ubuntu on my laptops and like it but lots to learn.

---

### Post by martin10018 on 2007-06-28
Same problem here:

[ATTACH]36705[/ATTACH]

/var/log is empty

With the last version everything worked fine...

---

### Post by ago on 2007-06-28
The logs in this stage are under /tmp. Also is this a fresh installation?

---

### Post by martin10018 on 2007-06-28
> **ago said:**
> Also is this a fresh installation?
Yep!

---

### Post by ago on 2007-06-28
I'd need the lupin.log and zenigata.log

---

### Post by martin10018 on 2007-06-28
How do I get them to my XP installation? Can I use my USB stick or mount an XP partition?

---

### Post by ago on 2007-06-28
> **martin10018 said:**
> How do I get them to my XP installation? Can I use my USB stick or mount an XP partition?

It depends at which stage it fails. If you are lucky the windows partition is already mounted under /media/host and you can simply copy the logs in there.

---

### Post by martin10018 on 2007-06-29
There is only a zenigata.log (see attachment) and no lupin.log.

[ATTACH]36803[/ATTACH]

---

### Post by ago on 2007-06-29
Try to boot into Windows TWICE (or even 3 times) in a row. Then try to boot Wubi.

---

### Post by martin10018 on 2007-06-29
Booted three times into Windows. Then booted Wubi. No change. :(

---

### Post by ago on 2007-06-29
Try to run chkdisk then from windows

---

### Post by martin10018 on 2007-06-29
I did that. All partitions are okay.

Remember: The previous version worked.

---

### Post by ago on 2007-06-29
From the log you have 4 ntfs partitions: 1, 3, 5, 6. 
/wubu/boot/linux is not found in partitions 1,5, 6
and partiotion 3 is not mountable since "Volume is scheduled for check".

So you have to check why wubi is not in partition 1, 3, 6 if it should be or why partition 3 does not work properly. A quick fix is probably to reinstall on a different partition

---

