---
title: "Can install Audacity or Wired...not both."
date: 2007-05-15
forum: General Help
---

### Post by deadlikeoscar on 2007-05-15
Hello all,

I am running Ubuntu 7.04 with all updates applied. I installed Wired after reading about it being in Ubuntu Studio. It installed great. The problem came when I attempted to install Audacity. Doing so broke Synaptic and I had to uninstall Audacity. I then tried it the other way installing Audacity first and then Wired. This is what I got. (which is the same thing I got before just with Audacity instead)

deadlikeoscar@Network:~/Wired$ sudo dpkg --install wired_0.3.1-1_i386.deb
(Reading database ... 167033 files and directories currently installed.)
Unpacking wired (from wired_0.3.1-1_i386.deb) ...
dpkg: error processing wired_0.3.1-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libportaudio.so.2.0.0', which is also in package libportaudio2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 wired_0.3.1-1_i386.deb

Is there anyway that I can fix this whole mess or can I really only use one at a time? Thanks in advance!

---

### Post by deadlikeoscar on 2007-05-15
Nevermind on the sound. Still need help with the original post.

---

### Post by deadlikeoscar on 2007-05-21
Bump.

---

### Post by FuturePilot on 2007-05-21
I think you need to try this```
sudo dpkg -i wired_0.3.1-1_i386.deb
```

---

