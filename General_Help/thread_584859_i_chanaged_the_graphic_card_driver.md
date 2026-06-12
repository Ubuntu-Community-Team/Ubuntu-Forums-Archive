---
title: "i chanaged the graphic card driver"
date: 2007-10-21
forum: General Help
---

### Post by nned7 on 2007-10-21
hi
 i just installed   ubuntu 7.10 yesterday;
i chanaged the graphic card driver from "screen and graphic preferinces", and now ubuntu won't  start.
what can i do?

---

### Post by forestpixie on 2007-10-21
when you say it doesn't start - does it not start at all or do you get to a command prompt?

if you get a prompt try this at the prompt

sudo dpkg-reconfigure -phigh xserver-xorg

if you don't get a prompt - boot to recovery mode and enter the same command

It will reconfigure x for you, answer the questions as best as you can, I think I remember tab moving fields.

---

### Post by nned7 on 2007-10-21
i got the blank screen.
now i will try your sugestion with the command line.

---

