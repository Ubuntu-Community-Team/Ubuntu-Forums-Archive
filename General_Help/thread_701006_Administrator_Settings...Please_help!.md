---
title: "Administrator Settings...Please help!"
date: 2008-02-18
forum: General Help
---

### Post by Clayton South on 2008-02-18
Hi everyone...

here's my question: I want to let non-administrator users be able to change the monitor settings in Screens and Graphics. Is there a way to somehow move these functions over to allow regular users to affect changes without me logging in? I tried moving the menu items over, but it still asked me for admin password.

Is there a way to re-assign the security or priviledges for these functions?

Thanks!

-Clayton South
__________________

---

### Post by bodhi.zazen on 2008-02-18
Yes

Try xrandr, can be run as a user

If you need more then that, you will want to configure sudo, sudo allows you to give access to limited commands.

[http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33)

	[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

