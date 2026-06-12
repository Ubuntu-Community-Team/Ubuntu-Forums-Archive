---
title: "Qemu crashes my whole (real) computer."
date: 2007-10-25
forum: General Help
---

### Post by tgoose on 2007-10-25
Well I'm trying to install Windows XP on Qemu to try out rdesktop, and every time I run it it eventually crashes my whole Ubuntu desktop. It can take up to half an hour, but I've yet to get through the installation process.

What happens is, if I have any music or video playing on Ubuntu, it stops and the mouse becomes very unresponsive. Then stops completely and I can't do anything short of restarting. Crashes also occur when I have no music or video, I just don't get much of a warning.

VirtualBox works fine but I couldn't get networking right and Qemu seems perceptually faster, so I'd rather run that if all possible. Since this is crashing my system outright I don't have anywhere to read messages in the terminal.

Is there a way I can log error messages so that I can retrieve them on restart? Or, better still, does anybody know what the problem is just from my poor description?

---

### Post by shad0w_walker on 2007-10-25
No idea what the problem is, but if you run the command from a terminal like this

```
qemu <options here> > ~/qemu.log
```

It should direct all the usual output of stout (The message you end up with in the terminal) to a file in your home directory called qemu.log

---

### Post by tgoose on 2007-10-25
Ok thanks, I'll try that today.

---

