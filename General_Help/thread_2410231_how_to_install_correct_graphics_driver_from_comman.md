---
title: "how to install correct graphics driver from command line"
date: 2019-01-12
forum: General Help
---

### Post by brightstargiftss on 2019-01-12
Computer 1: installed Kubuntu18.04 on hdd
 has Nvidia GEforce 9500 video card

moved drive to another computer

Computer 2: upon boot, error "Plasma is unable to start as it could not use OpenGL2"
has Radeon HD 7560D
black screen - alt-f2 terminal works
No internet connection. Cant use apt.

Anyone know how do I solve this?

---

### Post by Bashing-om on 2019-01-12
brightstargiftss; Hello -

In this instance we want to get rid of the Nvidia driver, and have the kernel pick up on the AMD driver.

Try:
```

sudo apt remove --purge nvidia*

```

then make sure that the file "  /usr/share/X11/xorg.conf.d/10-nvidia.conf " no longer exists.
reboot and see if the kernel now picks up AMD.

[INDENT]maybe Yes
[/INDENT]

---

### Post by brightstargiftss on 2019-01-12
Thank you SO much!!! Worked perfectly. fyi after remove operation, no 10-nvidia.conf file exists.

---

### Post by Bashing-om on 2019-01-12
brightstargiftss; Great !

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away :)
[/INDENT][/INDENT]

---

