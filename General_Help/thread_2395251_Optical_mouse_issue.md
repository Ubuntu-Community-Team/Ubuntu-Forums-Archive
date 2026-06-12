---
title: "Optical mouse issue"
date: 2018-06-29
forum: General Help
---

### Post by rasaborio on 2018-06-29
It's not actually a bug, it could just be I'm not as clever with Ubuntu to begin with... I've got a new optical mouse from a local store, but it's a cheap one, even the mark is just 'Optical Mouse', it works well with my laptop, but I must run this every time I turn on the laptop if I want it to be detected:

```
sudo modprobe -rv psmouse usbhid
sudo modprobe -v usbhid
sudo modprobe -v psmouse
```

I just edited ~/.bashrc to run it with a single command, but I was wondering if there's a way to make it be detected without doing that. I'm using Ubuntu 16.04 (64 bits), by the way...

Thanks for any help :cool:

---

### Post by The Cog on 2018-06-29
[https://wiki.debian.org/KernelModuleBlacklisting](https://wiki.debian.org/KernelModuleBlacklisting)
[http://manpages.ubuntu.com/manpages/bionic/man5/modules.5.html](http://manpages.ubuntu.com/manpages/bionic/man5/modules.5.html)
Should help.

---

