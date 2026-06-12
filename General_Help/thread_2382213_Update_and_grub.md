---
title: "Update and grub"
date: 2018-01-10
forum: General Help
---

### Post by rosswmcgee on 2018-01-10
My wife ran the 16.04lts updates last night and now the screen is stuck in  grub. I have tried all the options I know in the bios to no avail. How to fix?

---

### Post by deadflowr on 2018-01-10
Stuck at the menu screen or stuck in the loading splash screen (the screen with the Ubuntu and rolling dots thingy?)

---

### Post by rosswmcgee on 2018-01-10
stuck in menu screen

---

### Post by deadflowr on 2018-01-10
Best option I can think of is to see if running a live cd/dvd/usb and installing boot-repair /boot-info can explain something
I would run boot-info and post the results first before trying boot-repair, just in case someone sees something.

Boot repair:[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
Boot-info: [https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")

---

### Post by DuckHook on 2018-01-10
> **rosswmcgee said:**
> stuck in menu screen

Possibly this problem: [https://ubuntuforums.org/showthread.php?t=2382157](https://ubuntuforums.org/showthread.php?t=2382157)

Try my solution in [post 33]("https://ubuntuforums.org/showthread.php?t=2382157&page=2&p=13729180#post13729180"), starting at step 2 (you won't need to plug in vga cable). That is to say, try booting from an older kernel.

---

### Post by rosswmcgee on 2018-01-10
Thanks for the reply. I just did a complete re-install. Was there something in the update that created the problem?

---

### Post by DuckHook on 2018-01-10
> **rosswmcgee said:**
> Thanks for the reply. I just did a complete re-install.You invoked the nuclear option. :)> Was there something in the update that created the problem?
We won't be able to tell given that you've reinstalled. Any conjecture would just be guessing. I'm not questioning your actions (they probably solved the problem for you without wasting a lot of time); just pointing out that detective work can no longer be conducted on a crime scene that's been wiped clean.

---

