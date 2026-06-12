---
title: "GNUstep folder in home directory, how do I remove it?"
date: 2007-01-07
forum: General Help
---

### Post by Gen2ly on 2007-01-07
hmm, I must have installed something but I can't remember what it was.  Now I keep having this GNUstep folder in my home directory, and it's making me angry. grrr.  I can't delete it because when I do it pops right back, almost immediately.

Is there a way I can find out whats doing this?

---

### Post by Koybe on 2007-01-07
I don't know if it's a dependance of something else you installed but you can still remove it.

> sudo aptitude remove gnustep

And you can check which gnustep package you have installed et remove everything after using the previous command.

> dpkg -l gnustep*

---

### Post by Gen2ly on 2007-01-07
appreciate the help koybe, don't know how I did that.  I erased the folder and now it's not coming back.  Just one more question:  if I removed this  and something required it, I'm usually told about it, yes?

---

### Post by po0f on 2007-01-07
Dirk.R.Gently,

So you had a ~/.GNUstep directory (or something of the like)?  Most of the time these are just configuration files/directories with configuration files.  If a program required anything in there, it would just recreate that folder and save its settings again, it's not an 'error' if you never have run a program and it can't find your preferences or anything.

---

### Post by Gen2ly on 2007-01-08
po0f, actually it was not hidden.  That's why is was a tad annoying. :)

---

### Post by regeya on 2007-02-25
> **Dirk.R.Gently said:**
> po0f, actually it was not hidden.  That's why is was a tad annoying. :)

More than likely you had Window Maker installed at some point.  GNUstep and GNUstep-wannabe apps store user data in ~/GNUstep.  Apple users in the audience will be vaguely familiar with the layout of the GNUstep folder.

The *STEP* way is apparently to keep everything visible to the user, yet organized.  Hey, I'm all for it; looking at ls -a ~ is a bit dismaying.

ls ~ | wc -l 
43
ls -a ~ | wc -l
233

:shock:

---

