---
title: "firefox fail to open new window"
date: 2007-12-07
forum: General Help
---

### Post by kgsstyle on 2007-12-07
Hi,

I got problem with firefox.

This is my firefox information.

$ sudo dpkg -l|egrep -i firefox
ii  firefox                                    2.0.0.11+2nobinonly-0ubuntu0.7.10    lightweight web browser based on Mozilla
ii  firefox-gnome-support                      2.0.0.11+2nobinonly-0ubuntu0.7.10    Support for Gnome in Mozilla Firefox
ii  mozilla-firefox-locale-en-gb               2.0.0.7+1-0ubuntu2                   Mozilla Firefox English language/region pack
ii  mozilla-firefox-locale-ko                  2.0.0.7+1-0ubuntu2                   Mozilla Firefox Korean language/region packa
ii  ubufox                                     0.4~beta1-0ubuntu6                   modifications for ubuntu firefox (default) i

when I open more than 2 new windows, firefox freezes and turns grey.

I've never seen this error when I use Ubuntu 7.04.

What's wrong with Gutsy Gibbon?

---

### Post by Emerzen on 2007-12-07
I'm not sure but Firefox does eat up RAM/Swap pretty quickly.  What's your computer config in those areas?  I know when my PC is swamped the window turns grey until it catches up.  You could try turning off all desktop (compiz) effects to spare your memory and CPU cycles.

---

### Post by kgsstyle on 2007-12-15
Thank you, Emerzen.

However, it doesn't work, either...

Anyway, thank you for your interest :)

---

### Post by kgsstyle on 2007-12-23
I found the reason. It was caused by Google Toolbar.

And I solved it by using ubuntuzilla.

Thank you for all.

---

