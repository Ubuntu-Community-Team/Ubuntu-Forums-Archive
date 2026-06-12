---
title: "Lubuntu 19.10 Cursor changes in chrome"
date: 2019-11-17
forum: General Help
---

### Post by username52 on 2019-11-17
In the settings you can change the cursor. I have "Breeze" selected. Hoverever if i move my cursor to the chromium window it gets changed.
It is really annoying..

---

### Post by esa1975 on 2019-11-18
TLDR - It's because Chromium is now a snap instead of a native package.

Ubuntu is moving toward using snaps for core packages in order to make maintaining them across multiple releases easier. Chromium in 19.10 is a snap now and unfortunately snaps don't integrate perfectly with the desktop. This is a longstanding issue as described in [https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1585332](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1585332). I am giving the devs the benefit of the doubt because the positives outweigh the negatives in the long run but in the short term, it's going to be a problem. It also bothers me quite a bit and I am hoping for a solution sooner than later, particularly because there is no alternative to using the Chromium snap on 19.10 (no, I'm not going to run the downloaded binary for a myriad of reasons).

---

### Post by uRock on 2019-11-18
> **username52 said:**
> In the settings you can change the cursor. I have "Breeze" selected. Hoverever if i move my cursor to the chromium window it gets changed.
It is really annoying..
Why'd you say Chrome in the title and Chromium in your post? Two different browsers.
> **esa1975 said:**
> TLDR - It's because Chromium is now a snap instead of a native package.

Ubuntu is moving toward using snaps for core packages in order to make maintaining them across multiple releases easier. Chromium in 19.10 is a snap now and unfortunately snaps don't integrate perfectly with the desktop. This is a longstanding issue as described in [https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1585332](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1585332). I am giving the devs the benefit of the doubt because the positives outweigh the negatives in the long run but in the short term, it's going to be a problem. It also bothers me quite a bit and I am hoping for a solution sooner than later, particularly because there is no alternative to using the Chromium snap on 19.10 (no, I'm not going to run the downloaded binary for a myriad of reasons).
Hopefully they get that fixed soon.

---

### Post by Dennis N on 2019-11-18
> **username52 said:**
> In the settings you can change the cursor. I have "Breeze" selected. Hoverever if i move my cursor to the chromium window it gets changed.
It is really annoying..
I saw this problem in Chromium snaps installed several months ago (one in Lubuntu 19.10), but the changing cursor problem has disappeared in all of them. Is it still a problem after restarting? The cursor that is working properly for me is DMZ-White. You might try that one.

As to the theme bug, that seems to be fixed - at least in the snap version of Chromium browser in Lubuntu 19.10, which (I'm using it now) I can see is using the openbox window manager theme I select. Outside of the window manager theme, an alternate browser theme can be installed from the Chrome Web Store. I'm using Morpheon Dark.

---

