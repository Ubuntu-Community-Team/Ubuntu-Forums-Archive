---
title: "Ubuntu 13.04 hang (or crash) when recover from suspend mode"
date: 2013-06-14
forum: General Help
---

### Post by johnyy on 2013-06-14
Hello,

I have installed ubuntu 13.04 for a week now. It hangs/crashes everytime I am gone more than a few hours. Screen is black (no signal), keyborad "Num Lock" light is on but does not respond to any key stroke.

What could be wrong?? Don't know where to look now.

Hardware spec:
I5, 3450 sandy bridge
P9B75-M motherboard
nvidia 560 ti with prop driver 313
Intel 120G ssd

Any suggestions?

---

### Post by kurt18947 on 2013-06-14
Do you know your processor/motherboard/video info?  I've had a problem with in-development distros when using the open source video driver.  I have an nvidia 8400GS video card on a Gigabyte AMD motherboard.  Installing the current Nvidia video drivers fixed the suspend/resume problem for me.  I'm sure there are other causes and solutions.

---

### Post by johnyy on 2013-06-14
Thanks for the reply!
I am updating the post to include hardware specifications.
Video card is nvidia 560 ti with prop driver 313-update.

---

### Post by cruz12141214 on 2013-06-14
ok i had a similar issue, what fixed it was to disable "lock screen" durring suspend/wakeup, i dont remember what it was called

---

