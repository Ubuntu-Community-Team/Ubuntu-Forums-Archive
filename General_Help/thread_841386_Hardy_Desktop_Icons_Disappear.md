---
title: "Hardy: Desktop Icons Disappear"
date: 2008-06-26
forum: General Help
---

### Post by varaonaid on 2008-06-26
Hello,

I'm running Hardy and most on logins (not every single time, but more often that not), none of my desktop icons are there.  I can't seem to figure out what it's doing this nor have I found a fix.  I'd would love some suggestions on how to solve this. 

Any thoughts would be much appreciated!  Thanks in advance.

---

### Post by ryanhaigh on 2008-06-26
Do they come back when you go to somewhere like Places>home folder? The desktop icons are drawn by nautilus (the filemanager) so if it isn't starting they won't be drawn. Opening a folder should start nautilus and thus draw the icons again, if it doesn't then it is likely a bug with nautilus in which case you might want to look here: [https://bugs.launchpad.net/ubuntu/+source/nautilus](https://bugs.launchpad.net/ubuntu/+source/nautilus)

---

### Post by bodaciousllama on 2008-06-28
I've been having the same problem for the past 2 weeks, at first it was rare, but now the icons are gone 99% of the time I log in.

Maybe this means it has something to do with a recent update?

---

### Post by caprilo on 2008-08-03
I can confirm the same problem. Since today morning, when restarting the computer, the dektop isn't there (not even the right-button menu). Nautilus is started (I can see it with top and in the system monitor), but only when I kill it and restart it, or when I unckeck and re-check the show_desktop option in the gconf-editor, the desktop icons come back. I didn't change any Nautilus configuration.

---

### Post by Ozman on 2008-10-02
This has happened to me too.  I'm totally new to Linux, so any advice would be most gratefully received.

---

### Post by davygravy on 2008-10-05
I can confirm a bug or problem as described here above.  This is a serious bug/problem.

- none of the menu items (Desktop, for instance) bring the icons back;the redraws seem to be frozen

- in a terminal, executing   ls Desktop  freezes, ^C does not unfreeze the terminal

- also, executing   nautilus  freezes the term...

I think this may be some sort of lock or perm problem.

This is a serious bug and is making my install of Hardy quite unusable.

A restart temporarily fixes things, but only for 2-8 hours or so...

:(

---

### Post by pagaboy on 2008-10-14
Just started happening to me as well, although I can do an ls Desktop with no problems.

---

