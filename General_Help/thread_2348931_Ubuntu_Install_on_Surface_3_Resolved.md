---
title: "Ubuntu Install on Surface 3 Resolved"
date: 2017-01-09
forum: General Help
---

### Post by acdbill on 2017-01-09
Hello all,

I had the same issue as this user from 2012 when installing Ubuntu (and/or its derivatives) on my Microsoft Surface 3 (not a pro - Intel Atom 64bit CPU):
[https://ubuntuforums.org/showthread.php?t=2027736](https://ubuntuforums.org/showthread.php?t=2027736)

I could not answer that post as it was to old so therefore locked.

Basically the install would get to the end then I would get this message:

The 'grub-efi' package failde to install into /target/. Without the GRUB boot loader, the installed system will not boot.
I got this on Ubuntu 16.04, 16.10, Ubuntu Mate 16.04 and Mint Mate 18.

As I came here researching the same issue it must still be around so I figured I would post it here as well in hopes it would help someone else.

This turned out to be a networking issue surprisingly. There are a few bugtrackers for it for different linux's (linuxii?) live boot CD's. Apparently the installation of grub is either missing some files and tries to download them or the grub install itself wants connectivity. I'm not sure and don't know enough to tell.

As my Surface only has WIFI, I resolved the issue by buying one of those USB hubs with the built in ethernet port and having that connected to my home network while leaving the WIFI disconnected. It installed fine then and I'm now rocking a dual boot MS Surface 3.

---

