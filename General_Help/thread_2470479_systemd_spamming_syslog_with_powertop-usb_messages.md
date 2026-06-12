---
title: "systemd spamming syslog with powertop-usb messages"
date: 2021-12-31
forum: General Help
---

### Post by squiffy3 on 2021-12-31
Hello (first time poster).

syslog is being constantly spammed with the messages (below). Nothing appears to stop working (the mouse, a wireless trackball, seems to work perfectly), but it's writing a 20M file every day.

powertop must have been installed automatically (at least I didn't do it), and the tuneables tab for powertop shows two "bad" lines for 

Bad           Autosuspend for USB device USB Receiver [Logitech]                                                     
Bad           Autosuspend for USB device USB Keyboard [3-1.1]

Is there any way to stop the spamming?

My system - 
junocomputers 14" laptop running Ubuntu 18.04 LTS, fully updated.
wired keyboard and wireless trackball, both run through a USB extender

$ uname -a
Linux user 5.13.0-22-generic #22~20.04.1-Ubuntu SMP Tue Nov 9 15:07:24 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

$ tail syslog -n20
Dec 31 12:21:01 user powertop-usb-mouse[2824361]: Enabling USB Receiver
Dec 31 12:21:01 user systemd[1]: powertop-usb-mouse.service: Succeeded.
Dec 31 12:21:02 user systemd[1]: powertop-usb-mouse.service: Scheduled restart job, restart counter is at 267146.
Dec 31 12:21:02 user systemd[1]: Stopped USB Mouse support for Powertop.
Dec 31 12:21:02 user systemd[1]: Started USB Mouse support for Powertop.
Dec 31 12:21:03 user powertop-usb-mouse[2824369]: Enabling USB Keyboard
Dec 31 12:21:03 user powertop-usb-mouse[2824371]: Enabling USB Receiver
Dec 31 12:21:03 user systemd[1]: powertop-usb-mouse.service: Succeeded.
Dec 31 12:21:05 user systemd[1]: powertop-usb-mouse.service: Scheduled restart job, restart counter is at 267147.
Dec 31 12:21:05 user systemd[1]: Stopped USB Mouse support for Powertop.
Dec 31 12:21:05 user systemd[1]: Started USB Mouse support for Powertop.
Dec 31 12:21:06 user powertop-usb-mouse[2824379]: Enabling USB Keyboard
Dec 31 12:21:06 user powertop-usb-mouse[2824381]: Enabling USB Receiver
Dec 31 12:21:06 user systemd[1]: powertop-usb-mouse.service: Succeeded.
Dec 31 12:21:07 user systemd[1]: powertop-usb-mouse.service: Scheduled restart job, restart counter is at 267148.
Dec 31 12:21:07 user systemd[1]: Stopped USB Mouse support for Powertop.
Dec 31 12:21:07 user systemd[1]: Started USB Mouse support for Powertop.
Dec 31 12:21:08 user powertop-usb-mouse[2824389]: Enabling USB Keyboard
Dec 31 12:21:08 user powertop-usb-mouse[2824391]: Enabling USB Receiver
Dec 31 12:21:08 user systemd[1]: powertop-usb-mouse.service: Succeeded.

---

