---
title: "Stopping Ubuntu writing"
date: 2007-09-04
forum: General Help
---

### Post by numberboy on 2007-09-04
I've got a number of "thin client" machines that currently have Windows XP Embedded installed. They have flash storage rather than hard disks, and use Enhanced Write Filter to redirect any writes to RAM (so if the machine reboots no changes are stored unless I specifically tell it to). Is it possible to replicate this behaviour in Linux (preferebly Ubuntu or one of its related distributions), because I'd like to replace XPe.

Thanks

---

### Post by HermanAB on 2007-09-04
Puppy Linux is good at preventing unnecessary saves to a memory stick.  Maybe you should try this Linux version for your thin clients.

A good first stab at minimizing writes would be to disable syslogd.

Cheers,

H.

---

