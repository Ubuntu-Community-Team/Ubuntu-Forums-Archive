---
title: "Newly installed Kubuntu freezes after minutes"
date: 2007-05-07
forum: General Help
---

### Post by KillaBeeZ on 2007-05-07
Hi,

I am as new to Linux, and Ubuntu, as any one can be!
I chose to install Kubuntu and it boots up nice, in a multiboot with WinXP on the same drive.

When it booted the first time, my bluetooth mouse and keyboard didn't work, so I got hold of a wired keyboard and deleted all the bluez stuff. Now it works, and that is not my problem.

My problem is that it only works for some time. No specific time, just after an amount.
It freezes the desktop, so I can do nothing, but move my mouse. The mouse doesn't freeze.

My specs are:

Pentium 4 3.00 Ghz
2 Gb DDR Ram
256 Mb GeForce FX 5500

I really hope someone understand my problem, and can help :)

---

### Post by Wiebelhaus on 2007-05-07
I didn't have any luck with Kubuntu , IMO if you want to use KDE go with [OpenSUSE]("http://en.opensuse.org/Welcome_to_openSUSE.org").

---

### Post by iopo on 2007-05-07
Hi!

this is a common issue and there are many threads discussing it. You should check out:

[http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)

[http://ubuntuforums.org/showthread.php?t=405993](http://ubuntuforums.org/showthread.php?t=405993)

people suggested many solutions, but for me the only one that worked was downgrading my kernel to the 386 one (since I don't have a dual core it's not a big deal for me).

I found this solution here: 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243)

there are also some other options suggested. You can give it a try.

---

