---
title: "Black screen on 14.04 (On Chromebook)"
date: 2017-02-20
forum: General Help
---

### Post by fred330 on 2017-02-20
Hello,

I am using ubuntu 14.04, xfce version I believe, on a chromebook. I had a system where I could switch between Chrome OS and ubuntu easily, by the press of some buttons. However, I was recently playing a game when all of a sudden it froze, along with the rest of ubuntu. In a panic, I force quitted it manually, but now I am always brought back to Chrome OS. Even worse, when I ctrl+alt+t, and type 'shell' and then 'sudo startxfce4', which is the normal procedure, the terminal runs, but I am taken to a fully black and responsive screen, with no way to do anything. I am forced to just hard shutdown the laptop and use Chrome OS. Any reasons why this happens? And ways of solving it?

Thanks,

Fred:grin:

---

### Post by TheFu on 2017-02-21
You are still running ChromeOS.  A subset of Ubuntu is running inside a "chroot" environment in cooperation with ChromeOS.  What probably happened is that Google pushed an update and the Ubuntu-side needs to be updated too.  crouton has commands to update the Ubuntu install - use those.  This GUI issue happens about 2x a month, so expect it. Just remember to stay patched. That alone almost always fixes this sort of issue on a crouton managed ubuntu install.

---

