---
title: "Thunderbird will not load my profile"
date: 2007-09-30
forum: General Help
---

### Post by lapsey on 2007-09-30
One day it was working, the next it was not! No upgrades or plugin updates took place at the time. This is about a week ago, but have found nothing about this issue anywhere else.

I have tested the same profile on gentoo and windows. Loading the profile makes TB take me to the 'create account' dialog.

uname -a: Linux Celeron 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux (that's the latest kernel on Feisty)

TB version: version 1.5.0.13 (20070824)

Tools > JavaScript Console: 
```
Error: syntax error
Source File: file:///usr/lib/mozilla-thunderbird/defaults/isp/US/
Line: 1, Column: 1
Source Code:
300: file:///usr/lib/mozilla-thunderbird/defaults/isp/US/^
```

The fault may be with my profile files, but finding the right one is a wild goose chase. I just don't want to lose my emails!

---

### Post by ajgreeny on 2007-09-30
You won't lose your emails if you just rename the current ~/.mozilla-thunderbird folder as backup and let TB make a new one when you start it up.  You will need to enter your email account info again, of course, and also copy the alpahnumeric.default/Mail folder in to the newly made .mozilla-thunderbird folder but everything will still be there so don't worry.  It may be that one of the config files in the profile has caused the problem so it is best to let TB make a new one and then copy across just the bits you really need from the old, rather than everything.

---

