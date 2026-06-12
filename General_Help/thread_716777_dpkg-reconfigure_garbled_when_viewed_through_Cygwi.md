---
title: "dpkg-reconfigure garbled when viewed through Cygwin/rxvt"
date: 2008-03-06
forum: General Help
---

### Post by Kadin2048 on 2008-03-06
This may not be entirely an Ubuntu problem, but I'm hoping I can't be the only person who's experienced this issue and that somebody will point me in the right direction.

I have a server running Ubuntu 6.06.02 LTS (no xwindows) which I access and administer via SSH.  Mainly I use the "rxvt" terminal emulator running under Cygwin on a WinXP machine.

I have noticed that whenever I try to use 'dpkg-reconfigure' that the output is garbled.  It seems to be something to do with dpkg-reconfigure's use of non-ASCII characters in its interface.  But it really makes it difficult to use, not to mention ugly. (See screenshot in attached file.) Some other ncurses-based programs do the same thing (centerim does, if I don't run it with the -a option to force ASCII mode).

I feel like there's some sort of termcap problem going on here, but I really don't know where to begin to fix it.  I've made sure that my TERM variable on the server is set to rxvt, but that doesn't seem to help.

Does anyone have any idea how to fix this? Or barring that, how to force dpkg-reconfigure to use a plainer ASCII interface that won't cause rxvt/cygwin to choke?

Thanks very much in advance.

---

### Post by Kadin2048 on 2008-03-15
Well, seems maybe I'm the only one.  But just in case there's somebody else having the same issue ... after a lot of research I think the problem may be related to the user's issue in this thread:
[http://ubuntuforums.org/showthread.php?t=116053]("http://ubuntuforums.org/showthread.php?t=116053")

It seems to be a UTF-8 issue.  I resolved it temporarily by fudging around with my terminal and locale settings.  It's still ugly (not displaying the right border characters) but it's at least usable.  Unfortunately I'm not exactly sure what I did that fixed it, though. (And something that I did has broken perl and now I get error messages from anacron every night...) 

But UTF-8 seems to be part of it.

---

