---
title: "Ubuntu 16.04 Freezes and reboots"
date: 2018-05-11
forum: General Help
---

### Post by jakop92 on 2018-05-11
Hello all,

I built a brand new computer to do some MATLAB data analysis at work, but I am having issues with the computer sporadically freezing and subsequently rebooting. So far I have updated the video drivers and kernel, and ran a mem test. I ran it for about 12 hours, with no errors. I tried different memory configurations as well, but the crashes keep occuring.
The computer will completely freeze up for about 20 seconds, and will proceed to do a full reboot (BIOS POST, grub screen, etc). I'm not familiar with Ubuntu, so any help would be appreciated... Not really sure how to go on about troubleshooting this issue. I'm trying to follow the guide on how to get system crash logs, but haven't been successful yet.

---

### Post by TheFu on 2018-05-11
Welcome to the forums.

Yep, start with the logs.  Look for errors and warnings.  Then look above it in the logs. Hopefully, the system saw something and logged it BEFORE dying.   journalctl has a way to get kernel logs, system logs based on the time, so keep track of when it happens.
This is the horses mouth: [https://www.freedesktop.org/software/systemd/man/journalctl.html](https://www.freedesktop.org/software/systemd/man/journalctl.html)
Near the bottom of that link are examples. Learning to read the manpages-like stuff takes a little time, but after a few months, you'll see there is a method and it is pretty smart.

---

