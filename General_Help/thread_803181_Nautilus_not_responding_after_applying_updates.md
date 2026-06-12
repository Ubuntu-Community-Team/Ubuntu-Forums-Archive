---
title: "Nautilus not responding after applying updates"
date: 2008-05-22
forum: General Help
---

### Post by barichardson5727 on 2008-05-22
I have a machine that has been having major problems using the nautilus file browser just going non-responsive and locking up. I have noticed that this issue mostly happens when I try move or copy files, but sometimes it will just happen for no apparent reason at all. Once nautilus goes non-responsive I try restarting nautilus, ending the process using the system monitor, then I try killing the nautilus process with the kill command. Every time I end the process for nautilus the file browser window disappears for about a second then respawns a new window. The new nautilus window is immediately in a non-responsive state that has to be killed again. When nautilus goes non-responsive I have noticed that the cpu and memory usage for the nautilus process jump significantly.

I have been having the problem on two machines, both running ubuntu 8.04 (2.6.24-16-generic i686) with nautilus version 1:2.22.2-0ubuntu6. I have another machine that is running the same ubuntu kernel version, but I haven't allowed nautilus to be updated so it is still at version 1:2.22.2-0ubuntu5. The machine that has not been updated runs without any problems. I have a hard time believing that I am the only having this problem since after nautilus was recently updated but I have not seen anything posted regarding this issue.

I will happily try to provide any other useful information such as call traces but I am just not sure where to start with gathering this information or if this is even the best place to seek assistance regarding this problem.

---

### Post by barichardson5727 on 2008-05-22
Found similar issue already reported as a bug:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233865](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233865)

---

