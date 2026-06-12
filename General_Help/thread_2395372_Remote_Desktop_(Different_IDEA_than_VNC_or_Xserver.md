---
title: "Remote Desktop? (Different IDEA than VNC or Xserver)"
date: 2018-07-01
forum: General Help
---

### Post by warmango on 2018-07-01
Would it be, in therory, Possible to host a Ubuntu Touch like UI, over a remote desktop protocal? So one could access that Remote Desktop from their phone, and have no problem navigating their desktop as if it was a phone?

think the Ubuntu Touch Dock idea, where you dock the phone, and it becomes a desktop, but instead its reversed. and Wireless?

where i could access my pc with a VNC or Xserver and connect to a Ubuntu Touch interface?

Is this even possible?

---

### Post by cariboo on 2018-07-01
You'd probably get an answer to your question [here]("https://community.ubuntu.com/"), as developers usually don't check the Forums.

---

### Post by warmango on 2018-07-03
I usually am able to get my problem solved here, And i perfer this website as i have less issues with login and multiple accounts being rude.

---

### Post by HermanAB on 2018-07-04
Howdy, looking at it from a technical point of view, the touch interface is part of Xorg, so now that Ubuntu is back in the fold, it should be possible to remote a touch UI, just the same as a keyboard UI.  So, theoretically, you should even be able to remote a touch UI over SSH.

However, I have never really used touch on X, since we ran into too many issues with operators pointing at a screen and accidentally changing something.

Maybe this will help to give you some ideas:
[https://wiki.archlinux.org/index.php/Touchscreen](https://wiki.archlinux.org/index.php/Touchscreen)

---

