---
title: "Epiphany History"
date: 2006-12-19
forum: General Help
---

### Post by frogfusious on 2006-12-19
Is it possible to make Epiphany clear the browser history everytime I close it(like Firefox's Private Data feature). Either this, or make it so the location bar doesn't show history when I begin to type in it? I want to use Smart Bookmarks, but it is hard because when I try to, a long list of history items shows up. Thanks

---

### Post by ubuntu27 on 2006-12-19
As far as I know, there is no option for that in epiphany.
I been looking for it too, but couldn't find it in any menus.

---

### Post by Richard Kut on 2007-07-05
Hi folks! I saw his post appear in my searches because I too was looking for this. After much searching I could not find anything, so I wrote this script:

#!/bin/bash
#
# start_epiphany
#
# This is just a shell wrapper to force epiphany to start clean.
#
# Kludge: Redirect error messages (unknown cause) to /dev/null.
#
# Author: Richard Kut, 04-Jul-2007.
#
# Copyright: There is none! I release this into the public domain 
# for you to do with as you wish. Although I don't foresee this causing
# problems, I also assert that I am in no way liable if this breaks 
# anything in your computer setup. 
#
rm -f ~/.gnome2/epiphany/mozilla/epiphany/Cache/*
rm -f ~/.gnome2/epiphany/mozilla/epiphany/cookies.txt
rm -f ~/.gnome2/epiphany/ephy-history.xml
epiphany & 2>/dev/null

I pretty much does the same things as the Firefox menu pick Tools --> Clear Private Data.

I hope that this helps someone out there.

---

### Post by moopoo on 2007-10-27
It works like a charm. Thank you!

---

