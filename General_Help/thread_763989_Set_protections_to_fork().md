---
title: "Set protections to fork()"
date: 2008-04-23
forum: General Help
---

### Post by andradx on 2008-04-23
Yellow there.

I was doing homework for operating systems class and while testing I created a huge number of child processes that in the end of the programme lost their parent. So fork was no longer available to start other processes as I wind up having all resources used and I had to perform the good old reboot.

What I was wondering was, can I set restrictions to the programs I run in C from within a certain folder as to don't create, let's say 100 child processes? (I know that by now I should have learned how to prevent my own code to do such a thing but when all goes wrong and results aren't the aimed for one tend to compile build and run on-the-go)

The child processes with a parent become zombies right? And after a while all zombie processes are killed (btw can I command the zombie killing?). Any suggestion would be appreciated.:-k

---

