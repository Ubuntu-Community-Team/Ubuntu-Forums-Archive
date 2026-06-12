---
title: "Firefox keeps eating my profiles!"
date: 2005-06-04
forum: General Help
---

### Post by simianMiscreant on 2005-06-04
A lot of times when I boot, it says my Firefox profile is already in use. I don't know why this is, and I've already ended up having to create a profile other than "default." Now when I boot, it says both "default" and "brady" are in use, and I'd be sort of ticked if I had to make yet another profile. Anyone know what the deal is? Thanks in advance.

---

### Post by Xerampelinae on 2005-06-04
If you go to .mozilla/firefox/*.default/ you will find a lock file.  Just remove that.  If you shut firefox down badly, that lock file doesn't get removed and so you have this problem..

---

### Post by bored2k on 2005-06-04
[QUOTE=simianMiscreant]A lot of times when I boot, it says my Firefox profile is already in use. I don't know why this is, and I've already ended up having to create a profile other than "default." Now when I boot, it says both "default" and "brady" are in use, and I'd be sort of ticked if I had to make yet another profile. Anyone know what the deal is? Thanks in advance.[/QUOTE]
 It has happened here when firefox exits abruptly. It usually gets fixes if you kill it with Applications > system tools > system monitor.

---

### Post by simianMiscreant on 2005-06-04
I'm having this hard-lock system problem...

[http://ubuntuforums.org/showthread.php?t=39158](http://ubuntuforums.org/showthread.php?t=39158)

That probably explains it. Thanks guys!

---

