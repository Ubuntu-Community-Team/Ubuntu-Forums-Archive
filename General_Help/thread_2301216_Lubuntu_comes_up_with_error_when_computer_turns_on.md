---
title: "Lubuntu comes up with error when computer turns on, cant use computer"
date: 2015-10-31
forum: General Help
---

### Post by anthony58 on 2015-10-31
I`m running lubuntuu 15.10.  I was trying to open Firefox but it said it was already running even though it wasn`t.  I clicked this thing that started with and f and ended in icks (or something like that) in applications somewhere.  I clicked it before I tried to open Firefox.  Then I went to the task manager and stopped the f icks thing from running.  I then turned off my computer, turned it back on, and this came up:

[    2.198820][drm:intel_parse_bios [i915]] *ERROR* Child device config size 27
 is too small.
Fsck from util-linux2.26.2
/dev/sda1 contains afile system with errors, check forced.
/dev/sda1: Inodesthat were part of a corrupted orphan linked list found.


/dev/sda1:UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
             (i.e.,without -a or -p options)
fsck exited withstatus code 4
The root filesystemon /dev/sda1 requires a manual fsck


BusyBox v1.22.1(Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter `help` for alist of built-in commands.


(initramfs)  (I can type something here)



I dont know how to fix this or if I have to do a reinstall of Lubuntu.  Also, I am a noob at linux so I don`t know a lot of the terminal coding aspects.

---

### Post by sudodus on 2015-10-31
Your problems looks very similar to the problem discussed in the following thread (also today).

[Ubuntu 15.10 can't boot!](http://ubuntuforums.org/showthread.php?t=2301206)

Maybe you can try the same solution. But I think is it good to keep your questions in your own thread (here). Otherwise it can be confusing.

---

### Post by anthony58 on 2015-11-01
Thanks!  That thread really helped!  I was just wondering what you meant by keeping my questions in its own thread, I'm new to this forum.

---

### Post by Rex Bouwense on 2015-11-01
You should always start a new thread when you have a question even though it may appear that a thread that you are reading appears to be the same.  Occasionally the threads get muddied with questions that have nothing to do with original posters problem.  It doesn't hurt and will probably assist you to search the forums for a solution before you pose a question.  It may have been asked and answered before.

---

### Post by sudodus on 2015-11-01
+1 to Rex's explanation.

-o-

I'm glad you found the solution via that other thread, and that Lubuntu works for you now :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

