---
title: "Configure script of Qingy unable to find curses.h"
date: 2007-08-22
forum: General Help
---

### Post by trevorv on 2007-08-22
I'm trying to install Qingy (a non-X graphical replacement for Getty) on my Ubuntu system, but am having a problem with the configure script being unable to locate the curses header file. The output is as follows.

```
checking curses.h usability... no
checking curses.h presence... no
checking for curses.h... no
configure: error: One or more system headers that are necessary to compile this program are missing on this system. Cannot continue.
```

As far as I can tell it is installed; /usr/include/ncursesw/curses.h exists. How do I make the script realise this? I've tried PATH=$PATH:/usr/include/ to no avail, so I assume it's not $PATH it looks in.

Help would be appreciated resolving this :-)

---

### Post by lloyd_b on 2007-08-22
> **trevorv said:**
> I'm trying to install Qingy (a non-X graphical replacement for Getty) on my Ubuntu system, but am having a problem with the configure script being unable to locate the curses header file. The output is as follows.

```
checking curses.h usability... no
checking curses.h presence... no
checking for curses.h... no
configure: error: One or more system headers that are necessary to compile this program are missing on this system. Cannot continue.
```

As far as I can tell it is installed; /usr/include/ncursesw/curses.h exists. How do I make the script realise this? I've tried PATH=$PATH:/usr/include/ to no avail, so I assume it's not $PATH it looks in.

Help would be appreciated resolving this :-)

I have no clue what that "/usr/include/ncursesw/curses.h" file is.  The "standard" curses.h file is "/usr/include/curses.h", and it's a part of the package "libncurses5-dev".

Try installing that package, and hopefully the problem will disappear...

Lloyd B.

---

### Post by trevorv on 2007-08-23
Thanks, I could have sworn I tried installing that, but apparently not. After installing a tonne of dev packages I've got Qingy up and running but with a problem --- it won't start X.

When I choose to start my .xsession it simply throws me back to Qingy after attempting to start. My guess is the problem is that I do not have a ~/.xsession file, but what should be in it? I simply want Qingy to run startx.

Cheers.

---

### Post by trevorv on 2007-08-23
On second thoughts, that isn't the problem at all. Does anyone have any ideas?

Cheers

---

