---
title: "Hangs while typing!"
date: 2007-05-02
forum: General Help
---

### Post by Jonathan Harford on 2007-05-02
I recently installed 7.04 on my HP V5101 laptop and am loving it. One serious problem's been plaguing me: I'll be typing something, and suddenly a key will "catch" and the machine will become unresponsive.

For instance, I typed "www.shoutcast.com" in the address bar of konqueror, but when I looked up at the screen, I saw "www.shouuuuuuuuuuuuuuuuuuuuuuuuuuuuu...". The "u"s soon filled the entire address bar. I whacked the "u" key, but to no avail. The keyboard was unresponsive and the mouse was unresponsive. I had to hold down the power button to turn the machine off.

This has also happened with the "t" key, so it's not a super-low-tech problem (I've also never encountered the problem in Windows XP, and this is a dual-boot machine). It's happened twice in konqueror and once in kate (the text editor).

I don't know if this is relevant, but I did add "i8042.nomux=1" to the kernel line in GRUB to make my Synaptics touchpad quit flaking out.

Does anybody recognize this problem? Thanks.

---

### Post by Jonathan Harford on 2007-05-09
It was the Broadcom Wi-Fi adapter, bizarrely. I switched to ndiswrapper (which was a trial in itself) and the problem went away.

---

