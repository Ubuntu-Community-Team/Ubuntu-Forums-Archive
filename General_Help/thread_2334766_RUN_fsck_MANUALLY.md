---
title: "RUN fsck MANUALLY"
date: 2016-08-22
forum: General Help
---

### Post by WrexhamWill on 2016-08-22
Hi, 
I've been running Ubuntu for a few weeks on an old-ish laptop (I've used it before on other computers), and trying to log on just now, it's telling me:


/dev/sda1: UNEXPEXTED INCONSISTENCY; RUN fsck MANUALLY. 
(i.e., without -a or -p options)
fsck exited with status code 4
The root filesystem on /dev/sdal requires a manual fsck


It's then started something called:
BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)

And my command line begins with:
(initramfs)


Any help with what to do from here would be greatly appreciated :-)

p.s.
I've turned on & off again few times, including starting in recovery mode - same result.
I've also already run Ubuntu from disk to get my files copied onto a pen drive.

---

### Post by SeijiSensei on 2016-08-22
Boot the system from a disc or USB drive.  Then open a terminal and run the command
```
sudo fsck /dev/sda1
```

---

### Post by howefield on 2016-08-22
Note that when you run fsck that won't be /dev/sdal as you write in your original post. It'll be /dev/sda1 as in the number one at the end.

---

### Post by WrexhamWill on 2016-08-22
Thanks, running now

---

### Post by WrexhamWill on 2016-08-22
[B]Right, after Pass 1:
Error reading block 115867719 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error<y>?

Should I just click y to ignore error?

[/B]

---

### Post by SeijiSensei on 2016-08-22
Yes.  The problems won't be fixed unless you do.  You can use "sudo fsck -y /dev/sda1" to reply "yes" automatically, but if that worries you, stick with manual.  It's likely you have some bad blocks on that drive so you may be hitting "y" quite a few times.

---

### Post by WrexhamWill on 2016-08-22
Fab - that's sorted it :-)
Thanks every so much.

---

### Post by SeijiSensei on 2016-08-22
You're welcome.  Please visit the "thread tools" drop-down above and mark the thread [SOLVED].

---

