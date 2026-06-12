---
title: "New problem with Beryl...any ideas?"
date: 2006-12-01
forum: General Help
---

### Post by djsroknrol on 2006-12-01
Suddenly, I'm not able to run programs like Celestia or Flight Gear, and Beryl isn't starting...everything worked fine and I don't have a clue as to why it stopped working.

I have the Intel i810 driver and I'm using xgl...this is what I get now when I try to start Beryl:

```
bob@Ubuntu:~$ beryl-xgl
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl-xgl: No composite extension

```

---

### Post by kop316 on 2006-12-01
Wut you will wanna do is add

Section "Extensions"
      Option "Composite" "Enable"
 EndSection


to your /etc/X11/xorg.conf file

good luck with it

---

