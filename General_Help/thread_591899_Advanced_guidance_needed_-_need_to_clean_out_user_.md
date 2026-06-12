---
title: "Advanced guidance needed - need to clean out /user folder"
date: 2007-10-25
forum: General Help
---

### Post by Apostata on 2007-10-25
Hello there - here's my problem: somewhere in my /user folder there is some config file that is telling Ubuntu that I'm in the UTC timezone. I know this because when I setup a new user and log-in, the timezone is EST (Toronto) - when I create a new text file (unlike my current setup) the creation date is EST. When I do the same logged-in as normal, it's 5 hours ahead.

The question is, what could possibly be doing this? In lieu of an answer, because I use KDE and so much important data is stuffed into the /user/.kde folder, I'm not sure what's safe to ditch if I want to start from scratch.

Any ideas?

---

### Post by taurus on 2007-10-25
Maybe you just need to reconfigure your timezone again.

```
sudo dpkg-reconfigure tzdata
```

---

### Post by Apostata on 2007-10-25
Tried that. I've exhausted all of the usual suspects.

---

### Post by Apostata on 2007-10-25
A small recap of what I've tried on the system:

- BIOS (check)
- tzselect (check)
- localtime symlink (check)
- rcS edit (check)

---

### Post by Apostata on 2007-10-27
Solved: my lord I can't believe I finally figured it out. There was some .config file of some sort that had been sitting in my /user main directory (probably from a previous distribution or version of Ubuntu) - I just started clearing out loose/unknown files and sure enough after rebooting I'm in EST again!  :D

---

