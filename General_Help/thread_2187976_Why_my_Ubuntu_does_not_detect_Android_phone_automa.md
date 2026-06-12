---
title: "Why my Ubuntu does not detect Android phone automatically when lightdm is disabled?"
date: 2013-11-14
forum: General Help
---

### Post by godchueh2 on 2013-11-14
Hi all,

I use Ubuntu to be my Android development environment.
Everything worked fine when I was working in the Ubuntu desktop.
However, I decided to disable lightdm by default and log into Ubuntu through ssh.
It turns out that ADB doesn't recognize my Android phone anymore.
It constantly says "error: device not found"
I have to start lightdm to make Ubuntu recognize the phone and stop lightdm service again in order to use adb command.
Is there any command to connect to the device or a way to make Ubuntu recognize the Android device automatically without running lightdm service?

ps.
I can see my device with lsusb command

jason@Jason-Ubuntu:/$ lsusb
Bus 001 Device 008: ID 0489:c026 Foxconn / Hon Hai
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc.


Any info would help, thank you!!

---

