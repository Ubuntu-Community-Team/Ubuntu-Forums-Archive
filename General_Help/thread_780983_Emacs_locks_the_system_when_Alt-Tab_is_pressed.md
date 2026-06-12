---
title: "Emacs locks the system when Alt-Tab is pressed"
date: 2008-05-03
forum: General Help
---

### Post by manzyuk on 2008-05-03
Dear all,

I am experiencing exactly the same problem described here:

[http://ubuntuforums.org/showthread.php?t=679018](http://ubuntuforums.org/showthread.php?t=679018)

Any idea as to what might cause it? :confused: I am using Gutsy and GNU Emacs 22.1.1 from repositories.  I can still run emacs in terminal, but I'd like to use GUI version, too. Any help is appreciated.

---

### Post by ognum on 2008-12-17
I also have the same problem.

---

### Post by studo on 2008-12-19
Hello

I had also the same problem with the GTK+ 2.x support release.
I fixed my problem by removing the emacs22-gtk package and installing the emacs22 one that contains a version of Emacs compiled with support for X.

I still don't know why the GTK+ 2.x freezes on ALT-TAB.

Regards

---

### Post by ljungkvist on 2009-01-31
Just for information:

I've been suffering from this problem a long time and have been forced to recede to the non-windowed version of emacs. Today however, I found the solution (to my great delight!). It seems to be related to this bug: [https://bugzilla.redhat.com/show_bug.cgi?id=224611](https://bugzilla.redhat.com/show_bug.cgi?id=224611)

For what did it was making sure all the assistive technologies were switched off. Then it all worked flawlessly. So if someone else gets the same problem, hopefully they will get some help from this.

---

### Post by ognum on 2009-03-05
Hi all
I used to have the same problem. For me, the problem occurred because I reused my home directory from an older Ubuntu installation, and some properties of my ~/.gconf/desktop directory messed things up. Exactly what it was, I don't know.

One solution to my problem is as follows:
1. Remove ~/.gconf/desktop (or move it)
2. Log out, and log in again.

This creates a new ~/.gconf/desktop directory.

Hope it helps

---

### Post by SjoerdC on 2010-01-11
that worked for me; thank you

---

