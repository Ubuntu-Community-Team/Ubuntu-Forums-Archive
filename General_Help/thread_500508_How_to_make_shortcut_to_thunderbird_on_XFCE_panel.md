---
title: "How to make shortcut to thunderbird on XFCE panel"
date: 2007-07-14
forum: General Help
---

### Post by Ted Nancy on 2007-07-14
I'm trying to add a Thunderbird shortcut to my xfce panel. Command lines like "thunderbird" or "mozilla-thunderbird" don't work. Same if I try to run them from terminal.

How do I do this?

Also, I've got some threads that I consider solved. Is there some format or forum usage rules to follow? Change subject line to [solved] or something?

---

### Post by UJoe4 on 2007-07-14
First, make sure you have it installed (if "dpkg-query --show|grep mozilla-thunderbird" doesn't return anything you'll need to install it).

Then find the executable. On my system it's in /usr/bin and is called mozilla-thunderbird. See if yours is there ("ls -l /usr/bin/mozilla*") and if not, try to find it ("locate mozilla-thunderbird"). Once you've found it, make sure the directory it's in is in your path ("echo $PATH") and that there are three x's in the permissions. Then it should work from either the command line or panel.

---

### Post by Ted Nancy on 2007-07-15
Thanks for the detailed reply. Very good. Running locate returned so much stuff that it made no sense, but then I saw the same entry you said, /usr/bin/mozilla-thunderbird

Typing that in terminal started it up. After that, it was a snap to add to panel.

Many thanks.

---

