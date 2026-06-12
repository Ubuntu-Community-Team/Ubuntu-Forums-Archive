---
title: "Kismet Error"
date: 2005-07-27
forum: General Help
---

### Post by jallen on 2005-07-27
Hello All,

Lastnight I installed Ubuntu Hoary on my Inspiron 6000 and I'm pulling my hair out over a Kismet error I'm recieving.

I've got libncurses5 and libncursesw5 installed but other forums are suggesting that the ncurses-devel is needed.  I've searched the ubuntu forums as well as many others and can't seem to find out of the ncurses-devel package is available for ubuntu or not?  Does anyone have any advice?

Thanks!
Joe

--[ERROR]--

checking for group 'man'... checking for initscr in -lncurses... no
configure: WARNING: Unable to find libncurses
checking for initscr in -lcurses... no
configure: error: Unable to find libncurses or libcurses

---

### Post by jallen on 2005-07-27
Sorry for the waste of space.  Found the dev package here:

[http://packages.ubuntu.com/hoary/libdevel/libncurses5-dev](http://packages.ubuntu.com/hoary/libdevel/libncurses5-dev)

d'oh!

---

