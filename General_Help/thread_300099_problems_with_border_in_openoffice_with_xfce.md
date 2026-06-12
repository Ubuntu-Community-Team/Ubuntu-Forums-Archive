---
title: "problems with border in openoffice with xfce"
date: 2006-11-15
forum: General Help
---

### Post by a_dejot on 2006-11-15
hello!

i have just recently installed xubuntu on a very old laptop - (almost) everything fine so far expect from abnormal behaviour of openoffice. the border (no matter which one i choose in the windowmanager control panel) is displayed incorrectly (sometimes black, sometimes stars & stripes ;-), sometimes a little flickering). interestingly this happens (so far) only with openoffice and not with other windows, even though (to my knowledge) it is the same border!

thanks in advance!

---

### Post by a_dejot on 2006-11-15
RESOLVED: changed the standard color depth in /etc/X11/xorg.conf to 16 bit (instead of defaulted 24, which the old display obviously couldn't handle).

still interesting that this problem only applied to the openoffice border, not to other windows.

keep it funky!
a_dejot

---

