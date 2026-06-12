---
title: "Ubuntu 16.04 Freezes After Updates"
date: 2017-02-09
forum: General Help
---

### Post by ThePowerpuffGirls on 2017-02-09
I noticed that the OS freezes; the mouse/keyboard, time will stay frozen.
I noticed the time hadn't changed and the circle indicator when the password is checking, it frozen, because I had pressed 'Enter' as soon as it loaded.

This had happened after the latest update a day or two ago.
I thought it was a fluke, so reinstalled Ubuntu 16.04 x64, and the same thing happened.
I freezes a split second after the login screen shows.

[COLOR=#000000]Motherboard [/COLOR][COLOR=#333333]ASUS H110M-A/M.2 (LGA1151)
Processor: Intel Core i3-6100
RAM: Kingston HyperX DDR4 2133MHz (16GB) x1
Drive(s): Samsung EVO 850 120GB M.2 | Western Digital Caviar Black 2TB (64MB Cache/7200RPM) SATA/HDD
Keyboard/Mouse: Logitech MK320 (Combo)[/COLOR]

---

### Post by ThePowerpuffGirls on 2017-02-10
It is only on that computer. No other computers here have the same motherboard. I never had a problem before.

---

### Post by af.nl on 2017-02-26
Same problem here. Using the Guest account works fine, but switching to my account got it to freeze instantly. I would appreciate any help on this as soon as possible as I am basically locked out. I have tried a number of suggestion using Ctrl Alt F7, or F1, or F2 or F8 ... none of them help to get me back to my account. I would really like to avoid a re-install to get some trust in Ubuntu. If not I will have to think of an alternative (this is the first I got in trouble with Ubuntu 16.04).

As the title says, this happened a day after I made an update/upgrade on Feb 25th 2017. So something happened with the updates within I think a week or so (my previous update/upgrade was about last week).

Machine: Desktop Dell OptiPlex 990

Thanks.

---

### Post by oriolmas on 2017-02-28
I'm having the same problem after updating a week ago. There is a workaround.

1. Enter grub by pressing shift (or esc if shift does not work) when booting.
2. Select "Advanced Options for Ubuntu".
3. Choose the version prior to the update that caused this problem.

This will let you use your computer. Let's hope someone at Canonical makes a fix for this soon.

---

### Post by dragonfly41 on 2017-02-28
There are various tips I've noted while trying to solve the mystery of freezes  .. in my case Ubuntu 14.04.

First, a workaround to try to unlock the freeze .. assuming that the keystrokes below work ..

Switch to console mode then immediately back ..

ctrl+alt+F1

then immediately
ctrl+alt+F7

...


This second tip comes from here ...

[https://ask.fedoraproject.org/en/question/83930/how-to-intel_idlemax_cstate1/](https://ask.fedoraproject.org/en/question/83930/how-to-intel_idlemax_cstate1/)

It is easier if you first install Grub Customizer utility.

In fact there was a recent discussion here with same advice (comes from many discussions found in searching) ...

[https://ubuntuforums.org/showthread.php?t=2353693](https://ubuntuforums.org/showthread.php?t=2353693)

...

However I still have freezes from time to time.

---

### Post by af.nl on 2017-03-02
The workaround proposed earlier to get to a previous installation via the "advanced ubuntu" worked for me. 

It looks like the version 4.4.0.62 works, but the new ones 4.4.0.64 and the latest 4.4.0.65 do not work and the freeze is still there. So I hope canonical can get a diff betwwen those versions and get a fix for this very annoying bug.

With regards.

---

