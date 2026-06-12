---
title: "Windows removing New Files and restore Removed Files"
date: 2013-05-26
forum: General Help
---

### Post by UnUnlucker on 2013-05-26
I've got Windows 7 and Ubuntu 13.04 (with Ubuntu 12.04 nothing changed) on my Acer on varied drives and I've got drives for only Data. And after using the Ubuntu, when I switch systems, Windows removing New Files which appeared using Ubuntu and restore Removed Files which I removed using Ubuntu. So how can I ban Windows doing it. May be I could just ban Windows using drive with Data, but how?

---

### Post by sandyd on 2013-05-26
> **UnUnlucker said:**
> I've got Windows 7 and Ubuntu 13.04 (with Ubuntu 12.04 nothing changed) on my Acer on varied drives and I've got drives for only Data. And after using the Ubuntu, when I switch systems, Windows removing New Files which appeared using Ubuntu and restore Removed Files which I removed using Ubuntu. So how can I ban Windows doing it. May be I could just ban Windows using drive with Data, but how?

[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)

---

### Post by UnUnlucker on 2013-05-27
Sorry girl, but it's about Windows 8, and he means that Windows 7 haven't got this problems

---

### Post by sudodus on 2013-05-27
Any Windows version creates this problem when you ***hibernate*** instead of shutting it down completely. So if you make Windows shut down also when closing the lid or timing out (screen-saving, locking and ...), you will avoid this problem.

---

### Post by Mark Phelps on 2013-05-27
When Windows hibernates, it saves a copy of the partition information so that when it re-awakens, it can restore the partitions to the states they were when it was hibernated.  So, not only are any changes lost during hibernation, you are also risking corrupting the filesystem if you make such changes.

As sudodus indicates, you should NOT hibernate Windows if you are dual-booting.

---

### Post by UnUnlucker on 2013-05-30
Thanks a lot guys, but I don't what to do now, as I in the Linux, and if I try to switch it to Windows to avoid the hibernating, he'd again do it.

---

### Post by Mark Phelps on 2013-05-30
> **UnUnlucker said:**
> Thanks a lot guys, but I don't what to do now, as I in the Linux, and if I try to switch it to Windows to avoid the hibernating, he'd again do it.

Sorry, but as long as Windows continues hibernating, this problem will remain.

---

### Post by UnUnlucker on 2013-05-30
OK, that's good, how can I close the Thread?

---

### Post by BlinkinCat on 2013-05-30
> **UnUnlucker said:**
> OK, that's good, how can I close the Thread?


Hi,

This is how you mark thread as solved on your first post -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

