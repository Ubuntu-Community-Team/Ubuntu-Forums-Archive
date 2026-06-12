---
title: "shutdown after WOL results in autostart"
date: 2013-11-02
forum: General Help
---

### Post by Masher23 on 2013-11-02
Hi there !

I have a very strange thing going on here and I hope someone can help.

When I wake my machine up using wake on lan, and then shut it down, it first goes down like a normal shutdown (leds and fans go off) but after a few seconds it automatically starts. If I shut it down again, it works and it stays off.

If I start the machine using wake on lan and do a reboot and then a shutdown it will also shutdown and stay off. If I start the machine manually and then shutdown it will also correctly shutdown and stay off.

It only restarts automatically after a shutdown if the machine was started using wake on lan and not rebooted afterwards.

OS: Ubuntu 12.04 x64
Mainboard: MSI C847MS-E33 (latest bios)

In the bios under "wakeup event setup" I have set "wake up event by" to "bios". I have enabled "resume by PCI or PCI-E Device". All other events are disabled.

I am completely out of ideas with this one. If I wouldn't need the wake on lan functionality so badly, I would just turn it off and the problems were gone.

Would really appreciate any help ! I can post additional details or log files if requested.

- Masher

---

### Post by Masher23 on 2013-11-02
OK, I just found the answer in another forum. It seems like the driver for the network card has problems with WOL. Installing [this driver]("https://code.google.com/p/r8168/") has fixed the problem for me. Found the hint in a german forum in [this thread]("http://www.hardwareluxx.de/community/f12/intel-nm70-desktop-mainboards-ft-celeron-800-1000-series-920867-14-print.html"). Maybe that helps someone else with the same problem.

- Masher

---

### Post by sammiev on 2013-11-02
> **Masher23 said:**
> OK, I just found the answer in another forum. It seems like the driver for the network card has problems with WOL. Installing [this driver]("https://code.google.com/p/r8168/") has fixed the problem for me. Found the hint in a german forum in [this thread]("http://www.hardwareluxx.de/community/f12/intel-nm70-desktop-mainboards-ft-celeron-800-1000-series-920867-14-print.html"). Maybe that helps someone else with the same problem.

- Masher

Glad you found the fix. Please mark this thread as "Solved" to help the next folks. :)

---

### Post by Masher23 on 2013-11-02
Oh yes, you are right.

Done. Thanks.

- Masher

---

