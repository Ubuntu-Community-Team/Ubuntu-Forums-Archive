---
title: "Firefox 2 crashes X after installing flash 9"
date: 2006-10-31
forum: General Help
---

### Post by emid on 2006-10-31
I went ahead and tried to install the new flash 9 beta for firefox 2.  Since then firefox crashes X and takes me back to the login screen everytime I open it and click a link.  It opens up to my homepage fine, but when I click a link on the page it starts to load, then suddenly crashes X.  I had the random firefox (just the app not X also) crashes since I've moved to Edgy, but this is definitely something more.

I tried to remove flash 9 but the crashes still continue.  This never happened until I installed flash 9.  I see many threads about firefox crashing but none where firefox causes X to crash.  If anyone has any insight as to a solution to this problem please let me know.

---

### Post by pay on 2006-10-31
Look here [http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html](http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html)
Make sure that your default depth is 24bit in /etc/X11/xorg.conf

---

### Post by emid on 2006-10-31
Yeah, I've seen some other threads that say to check your default depth.  Mine is at 24, so I guess that's not the problem for me.  I should've mentioned that above. Thanks for the input though.

---

### Post by lonce on 2006-10-31
Had the same issue.  its a really easy fix.

Edit /usr/bin/firefox
and add "export XLIB_SKIP_ARGB_VISUALS=1" anywhere in the file without the quotes.  Fixed mine.  All you do is restart firefox and its fixed.  Worked like a champ for me.

---

