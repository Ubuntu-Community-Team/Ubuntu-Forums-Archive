---
title: "[SOLVED] Keyboard layout options not applied"
date: 2008-06-13
forum: General Help
---

### Post by scribu on 2008-06-13
Hello!

I recently installed Hardy (8.04) and it works great, except that every time I boot up, the keyboard layout is set to default.

When I go to Preferences -> Keyboard all my setting are in place, but the keyboard acts as if they weren't. After I reset to default and reload the layout that I want, I work fine, but that only lasts untill I reboot.

Can anyone help me on this?

Update: I was able to solve this issue by adding the "setxkbmap" command at startup. Other possible workarounds can be found at [bug #196277]("https://bugs.launchpad.net/xorg-server/+bug/196277/")

---

