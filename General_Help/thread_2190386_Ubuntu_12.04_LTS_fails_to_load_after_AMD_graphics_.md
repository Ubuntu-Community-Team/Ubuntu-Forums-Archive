---
title: "Ubuntu 12.04 LTS fails to load after AMD graphics driver change"
date: 2013-11-27
forum: General Help
---

### Post by chaosgodkarl on 2013-11-27
I have an AMD Radeon HD 7660G Discrete-Class graphics  card. I tried installing fglrx. The loading screen filled all 5 red  dots and then froze. So I came back here for help. They had me purge  that stuff and install xserver-xord-video-ati and  xserver-xord-video-radeon. since I did that, instead of freezing at  loading screen, the display shuts off completely.

One guy told me to use dmesg. Here's that result when using the command prompt which loads after choosing failsafe graphics mode in recovery, then choosing run: [http://paste.ubuntu.com/6483254/](http://paste.ubuntu.com/6483254/)

I really don't want to fresh install ubuntu. But I needed a better graphics driver than the default. I've been trying to install stuff via the command prompt. Any help would be appreciated.

---

### Post by mikewhatever on 2013-11-29
Actually, dmesg is not the right output for graphics related problems. You should rather look at /var/log/Xorg.0.log.

---

### Post by chaosgodkarl on 2013-11-30
How do I send that using pastebinit?

---

### Post by mikewhatever on 2013-11-30
Hm..., probably the same way you did dmesg. You can get it out in a terminal window just like dmesg with 'cat /var/log/Xorg.0.log'.

---

