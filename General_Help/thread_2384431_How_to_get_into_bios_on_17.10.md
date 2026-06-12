---
title: "How to get into bios on 17.10"
date: 2018-02-07
forum: General Help
---

### Post by David4321 on 2018-02-07
I'm having trouble accessing the bios on boot in 17.10, no commands work or shown during boot sequence.
I have earlier and for other reasons disabled wayland and boot with xorg.

Let me tell you what I'm actually trying to do, in case this evokes comment also.
I've installed VMware player, and trying to install virtual windows 7.
I get this error:
"This host supports Intel VT-x, but Intel VT-x is disabled.Intel VT-x might be disabled if it has been disabled in the BIOS/firmware settings or the host has not been power-cycled since changing this setting.
(1) Verify that the BIOS/firmware settings enable Intel VT-x and disable 'trusted execution.'
(2) Power-cycle the host if either of these BIOS/firmware settings have been changed.
(3) Power-cycle the host if you have not done so since installing VMware Player.
(4) Update the host's BIOS/firmware to the latest version.
This host does not support "Intel EPT" hardware assisted MMU virtualization.
Module 'CPUIDEarly' power on failed.
Failed to start the virtual machine."

Other forum threads suggest this can be edited in bios.
I've never tried to enter bios yet in 17.10
I've tried esc, del, F2, F12, F10, and others.

Is there any way to determine with certainty which key or steps will open bios?
Is there any command to set machine to restart one time only directly into bios settings?

Thanks for any help.

---

### Post by tinylagarto on 2018-02-07
What machine do you own?

On my old Thinkpad I can access the BIOS at start by pressing the blue ThinkVintage button.

---

### Post by deadflowr on 2018-02-07
You don't enter the bios from Ubuntu.
You need to enter the bios when you first turn on the machine.
> Is there any way to determine with certainty which key or steps will open bios?
Depends on if your system gives you any hints at the very first screen that shows when you turn the machine on.
Sometimes it's F2 sometimes delete key sometimes F1. It can be different from machine to machine or vendor to vendor.
You should be, with almost 100% certainty, able to find out with ease by running a web search of the machine and it's bios menu key entry.

---

### Post by irv on 2018-02-08
On my Asus, it is the "Esc" key, on my Dell, it is the "F2" key. If you don't know just Google it!

---

