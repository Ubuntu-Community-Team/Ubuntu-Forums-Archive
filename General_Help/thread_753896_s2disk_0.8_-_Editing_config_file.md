---
title: "s2disk 0.8 - Editing config file"
date: 2008-04-13
forum: General Help
---

### Post by SIO_ on 2008-04-13
I have Ubuntu 7.10 Gutsy. As you know *uswsusp* package for 7.10 doesn't include *s2ram* utility...

That's why I installed it from source. s2ram works well. But s2disk doesn't.

The problem is I don't know how to tune it properly. Ubuntu package could be configured with '*dpkg-reconfigure uswsusp*'. In repository there is 0.6 version, so while configuring, we edit **/etc/uswsusp.conf** file.

For version 0.8 config file is **/etc/suspend.conf**. Something had changed between vesions. So, simple _cp /etc/uswsusp.conf /etc/suspend.conf_ doesn't help.

I edited this file a bit. Now it looks so:
```
resume device = /dev/sda6
early writeout = y
image size = 1003741824
shutdown method = platform
snapshot device = /dev/snapshot
compute checksum = n
splash = n
```

/dev/sda6 is my swap partiton.
In 0.6 config snapshot device was set to /dev/sda6 too, but 0.8 says *"Invalid snapshot device"*

When I ran '*sudo s2disk*' it suspended to disk. But when I tried to load, something gone wrong... Ubuntu loaded like it wasn't  switched off properly. And after it loaded, swap partition has gone! I had to format it..

I know, that I should define the right resume device, but I don't know what device is it... Further experiments are too dangerous, so I'm asking you for help..

---

