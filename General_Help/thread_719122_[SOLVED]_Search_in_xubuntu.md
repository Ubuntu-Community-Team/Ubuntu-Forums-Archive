---
title: "[SOLVED] Search in xubuntu?"
date: 2008-03-08
forum: General Help
---

### Post by tstack77 on 2008-03-08
I'm helping out my dad's friend with an old thinkpad that ran windows 2000. It failed to boot but I was able to load xubuntu (gutsy) and transfer most of his personal documents to a flash drive. The problem I am having is with locating his outlook contacts (.pst file). I've been looking around using the live cd but I can't figure out how to search his c-drive for a .pst file and am feeling really stupid...help!

---

### Post by x1a4 on 2008-03-08
Sadly, XFCE doesn't have a native search app.  You have to use **slocate** on the command line.  Or, if you have Xubuntu already installed, install and use GNOME Search (**gnome-search-tool**) or, if you have Gutsy, the Tracker search tool.  You might also want to try the **find** command, but **slocate** is better

---

### Post by tstack77 on 2008-03-08
how would I use slocate in this example?

# slocate .pst?

---

### Post by kryth on 2008-03-08
maybe
slocate *.pst

---

### Post by x1a4 on 2008-03-08
> **tstack77 said:**
> how would I use slocate in this example?

# slocate .pst?

You can, although something like this would be better: ```
slocate -i --regexp='/*.pst'
```

---

### Post by tstack77 on 2008-03-08
All I get running off the xubuntu live cd is:

slocate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old
ubuntu@ubuntu:~$


EDIT: x1a4, I ran your idea and it gave me the same warning followed by many lines of langauge, cups, firefox, and zoneinfo settings. Unfortunatrly nothing from the c-drive.

---

### Post by x1a4 on 2008-03-08
Run ```
sudo updatedb
```  Sorry, should have mentioned it earlier.

---

### Post by tstack77 on 2008-03-08
Thanks for the quick reply but I had already reset the computer and used the pclinuxOS live cd to find it...was able to boot using the 'safeboot' methode (unlike regular and kubuntu gutsy).

---

