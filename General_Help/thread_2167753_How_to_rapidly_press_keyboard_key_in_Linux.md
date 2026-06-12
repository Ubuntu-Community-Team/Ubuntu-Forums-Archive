---
title: "How to rapidly press keyboard key in Linux?"
date: 2013-08-14
forum: General Help
---

### Post by lavini557 on 2013-08-14
I am looking to press a key rapidly in Linux. I would prefer to emulate it because I don't want to break my keyboard :)
So far, I've tried xte, but it's not fast enough for me. Anyone know how to make it press faster/a program that can press key really fast?

---

### Post by tgalati4 on 2013-08-15
Perhaps a script that cat's the input to the device.  That would be really fast.  Your keyboard can be found in /var/log/Xorg.0.log.  For me it is /dev/input/event3.

**WARNING:  The following will cause some keyboard disruption**.

```
sudo su
cat "x x x x x x" /dev/input/event3
```

Control-C to get control of the keyboard back.

There may be a better way to do this, but the input stream will be really, really fast.

---

