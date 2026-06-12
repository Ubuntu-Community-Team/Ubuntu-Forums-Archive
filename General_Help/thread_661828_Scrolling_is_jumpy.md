---
title: "Scrolling is jumpy"
date: 2008-01-08
forum: General Help
---

### Post by tcreek on 2008-01-08
Whenever I scroll a document, webpage, or anything else the page does not scroll smoothly but has a jumpy movement.  This happens when I scroll with the mouse, scroll bars or arrow keys.  Scrolling is smooth in Windows XP.

The situation is the same no matter what the mouse settings are on Firefox or Ubuntu.  This happens with both ATI driver options for my video card.

I have searched the forums but have found no resolution to the problem.

Any ideas,
Thanks

---

### Post by kshane on 2008-01-08
> **tcreek said:**
> Whenever I scroll a document, webpage, or anything else the page does not scroll smoothly but has a jumpy movement.  This happens when I scroll with the mouse, scroll bars or arrow keys.  Scrolling is smooth in Windows XP.

The situation is the same no matter what the mouse settings are on Firefox or Ubuntu.  This happens with both ATI driver options for my video card.

I have searched the forums but have found no resolution to the problem.

Any ideas,
Thanks

Are you running compositing?  If so, make sure the "smooth scrolling" is off in Firefox, otherwise, make sure it's set to on...

Kevin

---

### Post by tcreek on 2008-01-08
I have turned "smooth scrolling" on and off in Firefox with no difference.  Also auto scrolling.

Whether I run compositing or not, the problem remains.

I have an ATI Radeon 9800 Pro card so I suspect that is the problem. It was a pain getting the advanced Compiz graphics to work but they were so erratic and unreliable that it wasn't worth it. 

I can live without the graphics but the scrolling jumpiness is a major pain.

---

### Post by LeDechaine on 2008-01-19
Totally disabling effects solved the problem for me, note that it's a known bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/110384](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/110384)

---

