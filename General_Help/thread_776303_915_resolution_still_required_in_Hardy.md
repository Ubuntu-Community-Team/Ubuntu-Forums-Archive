---
title: "915 resolution still required in Hardy?"
date: 2008-04-30
forum: General Help
---

### Post by fifth_rune on 2008-04-30
I just recently upgraded to Hardy from Gutsy and before that Feisty.  I had 915 resolution installed in Feisty and kept it on all the upgrades.  Now when I try to uninstall it my resolution is broken.  Wasn't there supposed to be a driver fix in Hardy for this, and if so how can I get it to work?

Thanks for any help provided.

***

Turns out I had to make a new Xorg because 915resolution wipes out the new intel entry apparently.  Used this command:

sudo dpkg-reconfigure xserver-xorg

---

