---
title: "Most of my icons have disappeared from Top Bar"
date: 2015-04-23
forum: General Help
---

### Post by ktz84 on 2015-04-23
I'm using Ubuntu 15.04 with Unity and in the last couple of days after an update all my programs that use the top tray have disappeared ie owncloud, copy, dropbox, etc. All I have in that top bar now are the button that brings up the pulldown that allows you logout/shutdown/system settings etc, the time and date, sound, notifications bell & keyboard layout. Where's all my other stuff gone and how do I get it back?

Oops thought I would clarify. The actual programs haven't disappeared - it's just they aren't showing on the top bar.

---

### Post by devilotx-c on 2015-04-24
I had the same issue, boils down to this:

the 32 bit version of Google-Chrome removes/restricts/breaks (or something like that) libappindicator1, I was able to restore my icons by uninstalling the 32 bit Chrome, running apt-get autoremove, re installing libappindicator1 and then installing the x64 version of Chrome.

Hope that helps you :-D

---

### Post by ktz84 on 2015-04-24
Thank you devilotx-c that has sorted the problem for me.

---

