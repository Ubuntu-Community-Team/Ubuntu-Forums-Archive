---
title: "failed to start x server after new install"
date: 2007-09-19
forum: General Help
---

### Post by lumbercutter on 2007-09-19
When loading 7.04 on a used Dell Latitude C800, it took hours to read the disk and kept getting a gnome error. Gave up after several hours. Moved the hard drive to another Dell and installed successfully. Put the drive back into the C800 and received the "Failed to start X server" error. At this point I do get command prompt after logging in.

I suspect the reason for my problem may be the graphics card but it did work fine with windows 2000 before I installed Ubuntu. Any suggestions cause I want to dump microsoft as fast as I can.

---

### Post by por100pre1 on 2007-09-19
I think the same. Try this command there:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

type your user password and answer some questions, then:

```
startx
```

or

```
sudo reboot
```

---

### Post by lumbercutter on 2007-09-19
Ok - I am now at the package configuration and have to make some choices and unfortunately don't have a clue as to which one to select. vesa is already highlighted

---

### Post by por100pre1 on 2007-09-19
Try that generic driver first. If that doesn't work you can try again using another one.

---

### Post by lumbercutter on 2007-09-19
Bingo! Appreciate the help. You're good. I am glad to now be a part of the club.

---

### Post by por100pre1 on 2007-09-19
Welcome to Ubuntu! :)

---

