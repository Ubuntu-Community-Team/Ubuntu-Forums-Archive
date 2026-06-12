---
title: "How do I install grub on a certain partition through the livecd?"
date: 2008-03-07
forum: General Help
---

### Post by bobleny on 2008-03-07
OK, here is the deal, I'm doing some really screwed up ubuntu install on my laptop. It not only has a recovery partition at sda1, it also has vista installed at sda2.

I set my install up as:
sda1 recovery - Primary
sda2 vista - Primary
sda3 Blank Primary or Extended
sda4 Blank Primary or Extended
sda5 /boot - logical
sda6 swap - logical
sda7 / - logical
sda8 /usr - logical
sda9 /home - logical


Anywas, what I need to do is install grub at sda5 using the livecd.
So, could someone tell me how to do this?

Thanks!

---

### Post by Rocket2DMn on 2008-03-08
You should check out this guide for reinstalling GRUB (it's primarily for people who need GRUB after reinstalling windows, but it should work for your case, too).
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

