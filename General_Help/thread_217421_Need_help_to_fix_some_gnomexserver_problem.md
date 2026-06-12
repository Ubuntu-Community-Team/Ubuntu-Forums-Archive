---
title: "Need help to fix some gnome/xserver problem"
date: 2006-07-17
forum: General Help
---

### Post by tocky on 2006-07-17
Hi!

I have no idea what I have done to get this error message but yet I have it. When I go to System>Preferences>keyboard and try to change my layout to swedish I get this message twice.

Ohh beacause of it's in swedish I'll try to translate it:

Problem with activation of XKB-configuration
This can happen under these circumstances
- a bugg in the library libxklavier
- a bugg in the X-server (xkbcomp, xmodmap)
- X-server this incompitable implantation of libxkbfile

Version of X-server
The X.org Foundation
70000000

If you rapport this as a bug we beg you to also include
- the result of xprop -root  grep XKB
- the result of gconftoll-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

