---
title: "Ubuntu 18.04.3, crashed after update"
date: 2020-04-27
forum: General Help
---

### Post by Corvair on 2020-04-27
I loaded Ubuntu 18.04.3 on a virgin ssd, and still have Ubuntu 16 on another ssd, which is a good thing and I can revert to it. I have been using it and getting accustomed to it t for about a month now. This morning after installing updates, Skype and Brave, I started having issues so I reset the computer and it would not load. This is the screen I got on black background. I am not a computer analyst or programmer so what can I do next? I hope I don't have to re install 18.04.03 and and start everything from scratch.

/dev/sda1 contains a file system with errors, check forced.
/dev/sda1:
Inodes that were part of a corrupted orphan linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
                (i.e., without -a or -p options)
fsck exited with status code 4
The root filesystem on /dev/sda1 reqyires a manual fsck

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3.2) built-in shell (ash)
Enter  'help' for a list of built-in commands.

(initramfs) -
so what can I do now other than start 18.04.0 from scratch?

Corvair

---

### Post by mörgæs on 2020-04-27
[https://ubuntuforums.org/showthread.php?t=2334766](https://ubuntuforums.org/showthread.php?t=2334766)

---

### Post by Corvair on 2020-04-27
Thank you so much, this fixed the problem

---

