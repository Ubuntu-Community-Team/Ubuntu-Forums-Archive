---
title: "Divining infinity with Ubuntu"
date: 2008-04-30
forum: General Help
---

### Post by drewcoon on 2008-04-30
Hey, long story short... I tried to copy my desktop folder to my desktop, and got an error like this:

[img]http://i16.photobucket.com/albums/b23/Drewc2k5/Screenshot-nautilus.png[/img]

it still copied, however, so I just deleted the "Desktop" folder off my desktop. Now it's in my recycle bin and I can't delete it:

[img]http://i16.photobucket.com/albums/b23/Drewc2k5/infintyOMG.png[/img]

it says I can't delete because the directory isn't empty... And by looking it it's properties, it's 504 folders, one inside the other.

Help! O_o

---

### Post by ivze on 2008-04-30
try 
```

rm -rf <dir name>

```
from terminal over the faulty directory in trash.
This must be in.
~/.local/share/Trash/files
.

---

### Post by jimmy the saint on 2008-04-30
I've never tried this, but I would imagine it's like putting two mirros facing eachother and looking into infinity, as you implied.  Perhaps, if it's possible, try moving the folder to another location (outside your home direcotry) and then attempt to delete it.  Alternately try rebooting.  I know that rebooting is a windows thing, but It has resolved a few issues for me in the past in Ubuntu.  
Good luck man

---

### Post by drewcoon on 2008-04-30
> **ivze said:**
> try 
```

rm -rf <dir name>

```
from terminal over the faulty directory in trash.
This must be in.
~/.local/share/Trash/files
.

Alright, that worked. Thanks!

My command of terminal with manipulating files isn't too good... And I wasn't sure where my trashed files were kept :)

---

### Post by jocko on 2008-04-30
> **drewcoon said:**
> Hey, long story short... I tried to copy my desktop folder to my desktop
Interesting thing to do. Looking for ways to break things?
So what happens if you do this:
```
rm rf ~/Desktop/Desktop
```**Edit:** I'm too slow, apparently...

---

