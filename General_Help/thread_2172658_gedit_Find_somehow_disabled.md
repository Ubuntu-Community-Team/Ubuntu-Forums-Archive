---
title: "gedit Find somehow disabled"
date: 2013-09-05
forum: General Help
---

### Post by jneedle29 on 2013-09-05
Ok so this has been annoying me for a while. At some point in the last few weeks, I must have accidentally disabled Find in gedit.
Going into Search > Find, clicking the magnifying glass icon, and the shortcut Ctrl+F all do nothing.

Oddly, this is only for my profile- Find works just fine if I use (gk)sudo gedit.
I tried some time ago to uninstall/reinstall gedit, but it didn't seem to do anything.

I can't imagine what I did to disable Find, save maybe using sudo instead of gksudo a few times; then again, if I recall correctly, I had to install gksu myself
(I'm running Ubuntu 13.04; if this sounds off let me know).

If anyone can help me re-enable Find and/or help figure out how I disabled it in the first place, I'd be very thankful.

(btw Find and Replace works just fine for me, but it's rather cumbersome if all I want to do is look for occurrences and not replace anything)

--edit--
Also just realized that go to line also doesn't work as user (works as root). Again, neither the menu option nor the key combination seems to work.
I guess whatever this problem is has to do with tabs popping up in the corner, but I can't think of any setting like that.

---

### Post by ajgreeny on 2013-09-06
I don't use gedit but could the find utility be a plugin or extension you have inadvertently disabled?

---

### Post by jneedle29 on 2013-09-06
I'm inclined to say no-unless it's located somewhere different from the other plugins, I don't think so; nothing in Edit > Preferences > Plugins looks like a regular find, except maybe the GDP find, but that's for searching through a bunch of files, not the current one; besides I have it enabled. Unless one of these search things i overriding the default...

Btw another odd thing I noticed- looks as if Ctrl+i centers the line I'm currently on and also removes my cursor temporarily as opposed to opening the go to line panel. Maybe I somehow overwrote these functions?

--Edit: Just figured out what this is-started removing plugins, and discovered that when my cursor goes away (after pressing Ctrl+i or Ctrl+f), it's because I am able to use these now (maybe they were disabled by the modelines plugin? I don't even know why I enabled that in the first place). However, the little window isn't popping up for either. Still really confused.--

---

