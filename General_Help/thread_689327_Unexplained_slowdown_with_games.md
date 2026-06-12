---
title: "Unexplained slowdown with games"
date: 2008-02-06
forum: General Help
---

### Post by Bablefish on 2008-02-06
First  of all I am running Ubuntu 7.04 with restricted drivers. The laptop I am running it on has an ATI Graphics card. With that out of the way I will explain what happened, when I first started using Ubuntu way back in May of last year I could run some 3D games such as Neverball, Planet Penguin Racer, along with Tux Cart with no problem at all. Then suddenly about 3 months along long before I started fooling around getting my ATI fully functional. I started getting slowdown, as in sometimes these games would run so slow I was afraid my computer which uses a 1.2 GHZ CPU with 512 MB of RAM was going to crash. Then the other day I tried to install the latest version of Supertux 0.3.0 which if you did not know is a 2D game. Once again I was getting the same slowdown with a 2D game? Does anyone here have an explanation for this...or at least a fix?

If you have one please keep in mind I am no computer expert

---

### Post by Gen2ly on 2008-02-06
Is direct acceleration showing as enabled?

---

### Post by Bablefish on 2008-02-06
Dumb question...How do I check on that?

---

### Post by Gen2ly on 2008-02-06
glxinfo | grep -i direct

---

### Post by Bablefish on 2008-02-07
This is what I got after entering that command line

X Error of failed request:  GLXBadContext
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  17
  Current serial number in output stream:  17

---

### Post by Gen2ly on 2008-02-07
This thread  might explain more:

[http://groups.google.com.hk/group/comp.os.linux.hardware/browse_thread/thread/2ac6bba33f950eef](http://groups.google.com.hk/group/comp.os.linux.hardware/browse_thread/thread/2ac6bba33f950eef)

Have you tried reinstalling or installing the new ATI driver?

---

### Post by Bablefish on 2008-02-07
But there in lies a long story involving crashing of  Xserver. Believe me I tried, there is only 1 current driver available for my card and it's 64 bit, the CPU on my laptop is on the other hand 32 bit

---

