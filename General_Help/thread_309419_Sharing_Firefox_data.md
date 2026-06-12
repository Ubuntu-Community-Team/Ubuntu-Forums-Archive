---
title: "Sharing Firefox data"
date: 2006-11-29
forum: General Help
---

### Post by Globox on 2006-11-29
Hey, I went through a couple of tutorials for sharing Firefox/Thunderbird data between Windows and Ubuntu, and so far so good. Everything is working fine except one little problem: when I close firefox -ProfileManager it launches Firefox with all of my bookmarks and extensions (the way I want), but if I exit Firefox and re-launch it using a normal shortcut, it opens with  the default blank profile (even though it doesn't exist, it re-creates it and uses it).

My profiles.ini file looks like this:
```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/shared/_application data/firefox.default
Default=1
```
I tried changing StartWithLastProfile to "0" but that didn't help. I even deleted the directory it had created in my home /.mozilla/firefox/ folder and it STILL re-created it.

What am I doing wrong?

---

### Post by ingo on 2006-12-01
> I even deleted the directory it had created in my home /.mozilla/firefox/ folder and it STILL re-created it.
how about linking your proper profile to the above directory?

---

