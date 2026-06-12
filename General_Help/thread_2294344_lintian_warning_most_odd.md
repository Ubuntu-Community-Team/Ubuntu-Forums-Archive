---
title: "lintian warning most odd"
date: 2015-09-10
forum: General Help
---

### Post by roland-logikalsolutions on 2015-09-10
I have created a debian package and I'm poking around with lintian cleaning things up. Yes, it will install from the command line and run, but some of the graphic tools like the horrible-yet-bundled-in Software Center seem to not always like it. The following lintian error befuddles me.

W: myapp: syntax-error-in-debian-changelog line 1 "badly formatted heading line"
W: myapp: syntax-error-in-debian-changelog line 1 "found eof where expected first heading"

I even copied the top of this file:

[http://surfraw.alioth.debian.org/debchangelog](http://surfraw.alioth.debian.org/debchangelog)

Does anyone have a link to an actual changelog which passes lintian without overrides? Not a useless Debian documentation link which goes to another useless link that goes to another useless link....and so on and so on.... I've already burned a few hours down that rabbit hole.

I just want a short example which cleanly passes lintian.

Thanks,

====
The error was bogus.

Someone added a "changelog.Debian" text file which had the error, it was not in the "changelog" file that is actually maintained.

I need to file a bug with lintian team so they can update the text. The expanded help and resolution only said "changelog" not "changelog.Debian" It sent me down a rabbit hole.

---

### Post by mc4man on 2015-09-10
why not just post your changelog in a code box?

---

### Post by roland-logikalsolutions on 2015-09-10
Because right now it is the top N lines of that file down to the first --- line

---

