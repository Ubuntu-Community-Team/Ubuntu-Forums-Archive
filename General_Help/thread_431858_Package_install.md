---
title: "Package install"
date: 2007-05-03
forum: General Help
---

### Post by posiedon321 on 2007-05-03
Can anyone tell how to install packages with Add-Remove Programs without an internet connection?

---

### Post by taurus on 2007-05-03
What package do you have in mind?  If you don't have network on your machine, you need to download it and install it by hand.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by posiedon321 on 2007-05-03
Among other things I want to install xmms and/or gstreamer for DVD and mp3 playback. Every time I try to do it I get a "C compilers can't create executables" message. I installed the compiler from the cd but the problem persists.

---

### Post by taurus on 2007-05-03
How did you install a compiler from the CD?

Insert the CD into the drive and run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by posiedon321 on 2007-05-03
I used the Add/Remove option under Applications.

---

