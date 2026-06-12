---
title: "USB 2.0 Flash Drive hangs mysteriously, please help."
date: 2007-09-16
forum: General Help
---

### Post by endo on 2007-09-16
So I'm having this very strange and irritating problem. I have a Corsair Flash Voyager USB flash drive and I am using Gnome. When I log in and plug my flash drive, I start copying files from or to it. While copying at some (random) point, it just hangs and stops working. Even the LED goes out. This hang continues for about 20 seconds and then the device reactivates itself and continues the copy process. And this may happen several times during one copy operation. It's very irritating. I made several experiments, attempting to localize the problem and I was astonished by some strange facts:
This happens only on my user account and only when I log in (using my account) graphically. I have several user accounts on the system and none of them has this problem! The drive works perfectly fine on all other accounts, including root. So, it's not a hardware problem. The next thing I tried was to log in into another account (that doesn't have the problem) and su into my account and try to copy something onto/from the drive via console. Works perfectly fine! So my user account has no problem with the drive via another user's GDM-session! The problem exists only when I log into my account via GDM and then the problem exists when using both Nautilus and the console to copy files. It's so strange!
I explored /var/log/messages and found that the following message is logged in there every time the problem occurs:```
kernel: [19282.200762] usb 3-6.1: reset high speed USB device using ehci_hcd and address 31
```Is this supposed to tell me something important?
And one more thing - the problem occurs not only when I'm copying something from/to the drive, but also in some other situations, for example:```
badblocks -v /dev/sda1
cat /dev/sda1 > /dev/null
``` and so on. So it turns out that every time the drive is continuously active, the problem occurs.

And after all these clues, I have no idea what exactly the problem is. I'm almost desperate. :(
I suppose it has something to do with my personal gnome session (at least this can be concluded from the evidence), but I'm not sure at all.
Does anyone have any idea how I could fix this problem?
Thanks in advance.

P.S.
I forgot to mention I'm using Ubuntu 7.04

---

### Post by endo on 2007-09-17
I just discovered another astonishing clue:
I logged into my account (that has the problem) via GDM and checked again - the problem occured. So far, no news. Then I swiched to tty1 by pressing Alt+Ctrl+F1 _without_ logging out of my gdm session. On tty1 I logged in again with my account and there I did another test. It worked perfectly fine!!!
So, even if I'm logged in via GDM, the problem doesn't occur as long as I am on another tty, even with the same user!
So the problem exists ONLY when I am logged in via GDM with my account and I start working with the device from there. If I switch the tty, the problem disappears.
Ironically, I happen to use the drive most often under exactly the same circumstances that (only) cause the problem. :(

Any ideas?

---

