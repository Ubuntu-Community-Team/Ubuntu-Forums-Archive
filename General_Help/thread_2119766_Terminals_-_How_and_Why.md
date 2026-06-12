---
title: "Terminals - How and Why"
date: 2013-02-24
forum: General Help
---

### Post by whtemple1959 on 2013-02-24
I am new to Linux , Ubuntu, and LXDE so could some understanding of the system.
Could some one please explain to me the following....
In my menu I have...
System Tools => UXTerm with command uxterm
System Tools => XTerm with command xterm
Other => Terminal with command /usr/bin/lxterminal
Other => XTerm with command xterm
Other => X-Terminal as root with command /usr/bin/gksu -u root /usr/bin/x-terminal-emulator..... btw this will not accept my password, although if I open any other terminal and use sudo I have no problems.
Other => XTerm (Unicode) with command uxterm
Accessories => LXTerminal with command lxterminal

So...
Why so many terminals?
Why locate them in different sections of the menu?
Why wont the root terminal accept my sudo password?
Which terminals can be removed?

Thanks in advance for any advise given.
Bill

---

### Post by Frogs Hair on 2013-02-24
Some terminal application migrated to Linux from Unix and offshoots I think it was a matter of features and preference. The UX terminal was from HP Unix. The X terminal is used in the X window system which Linux uses. 

[http://en.wikipedia.org/wiki/Xterm](http://en.wikipedia.org/wiki/Xterm)

---

### Post by UltimateCat on 2013-02-24
Hi:

When I did my first install of Linux I too wondered why so many terminals-

Did a little searching and these webpages should help you.

[http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

Why so many terminals:
[http://unix.stackexchange.com/questions/60153/why-are-there-so-many-virtual-terminal-devices](http://unix.stackexchange.com/questions/60153/why-are-there-so-many-virtual-terminal-devices)
SOLVED: Why so many terminals:
[http://ubuntuforums.org/showthread.php?t=1346376](http://ubuntuforums.org/showthread.php?t=1346376)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by sisco311 on 2013-02-24
> **whtemple1959 said:**
> 
Why wont the root terminal accept my sudo password?


gksu is a GUI frontend for su and sudo. Run:
```
gksu-properties
```
and make sure that the Authentication Mode is set to sudo.

---

