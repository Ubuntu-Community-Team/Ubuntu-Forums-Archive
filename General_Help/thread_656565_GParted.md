---
title: "GParted"
date: 2008-01-02
forum: General Help
---

### Post by -Zeus- on 2008-01-02
Hi,

I've searched regarding an answer to this to no avail so here goes.

I'm trying to move the unallocated space between /dev/sda2 and /dev/sda4 and give it to /dev/sda1 but I have been unable to.  When I first resized /dev/sda2 I was unable to move the left boundary at all, and that still remains the case.  I'm sure there must be a way to do this :confused:

Attached is a screenshot

[IMG]http://zeus.momjian.us/gparted.png[/IMG]

---

### Post by jken146 on 2008-01-02
You can't give it to sda1 without deleting sda2 first.  Each partition has to be continuous.

---

### Post by sciencewhiz on 2008-01-02
You can't resize a mounted partition (see the little lock icons). Since you want to resize your root partition, you should boot from your installation CD and do the partitioning from there.

After you've done that, you should be able to move sda2 over and expand sda1.

---

### Post by -Zeus- on 2008-01-02
I was doing it from the Live CD... I just booted to Ubuntu to take the screenshot.

jken146, are you sure I can't do it?  can't I move the files from the beginning to the end of sda2?

---

### Post by -Zeus- on 2008-01-02
I fixed the problem by burning the latest version of GParted Live, and that had the option to move the data to the right end

---

