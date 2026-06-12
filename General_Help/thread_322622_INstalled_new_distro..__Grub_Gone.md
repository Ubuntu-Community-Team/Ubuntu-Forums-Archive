---
title: "INstalled new distro..  Grub Gone"
date: 2006-12-20
forum: General Help
---

### Post by Master Shake on 2006-12-20
OK, here's the situation...

I currently have a dual boot XP and Ubuntu.  I installed SymphonyOS to a seperate partition (HDA6), and now it boots directly to Symphony.  Grub is toast.  How can I get Grub back, and have both Ubuntu, SymphonyOS and XP on the list?

---

### Post by bodhi.zazen on 2006-12-20
> **Master Shake said:**
> OK, here's the situation...

I currently have a dual boot XP and Ubuntu.  I installed SymphonyOS to a seperate partition (HDA6), and now it boots directly to Symphony.  Grub is toast.  How can I get Grub back, and have both Ubuntu, SymphonyOS and XP on the list?

Start with looking in /boot/grub/menu.lst in Symphony.

Your gurb menu may be "hidden" - hit Esc as you boot

[http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu](http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu)

or have a short time to boot to default.

If not, you will have to re-install grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

This how-to should work just the same for you 8)

---

### Post by Master Shake on 2006-12-20
Found that how-to not too long ago, and it worked like a charm. :)

---

