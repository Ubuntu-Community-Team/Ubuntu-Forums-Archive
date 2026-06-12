---
title: "firefox interface lag"
date: 2007-04-26
forum: General Help
---

### Post by soundguy24 on 2007-04-26
I use 7.04, and a Radeon X1400 controlled with ATI's fglrx module. When I click to switch tabs in firefox, it switches to the correct page, but the tab bar lags behind about .5 seconds, *slowly* switching to show the new active tab. When I restart X (ctrl-alt-backspace), firefox is speedy again, but after a few hours, this behavior returns.

Does anyone else have this problem?

---

### Post by wyth on 2007-04-26
I haven't had that specific problem, but I'm back on Edgy.  One thing I found was [swiftfox]("http://getswiftfox.com/") helped quite a bit.  There's an Ubuntu repository, and what you do is choose a version for your specific cpu.  It doesn't affect any of your firefox settings; in fact it automatically uses any addons and bookmarks you already have.  In short, it's exactly like your current firefox setup, but faster and more efficient.

You could manage all the tweaks they use, but have fun hunting them down.  I just went with swiftfox about a month ago and haven't looked back.

---

### Post by soundguy24 on 2007-04-26
I've actually tried swiftfox--same problem. The issue appears to be the XUL interface which both browser builds use.

---

### Post by soundguy24 on 2007-04-26
I have some new info. I monitored dmesg, and right around the time firefox started lagging again, I got this message:

[   15.908126] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   15.910520] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[   15.910541] [fglrx] module loaded - fglrx 8.36.5 [Apr 17 2007] on minor 0

It appears the module reloaded once it *completely filled up* my 2GB of RAM. Anyone?

---

