---
title: "[SOLVED] program &amp;quot;blast&amp;quot; problems"
date: 2007-08-25
forum: General Help
---

### Post by steveneddy on 2007-08-25
EDIT: solved
Solution below


I installed a program I found in the repo's called Blast.

It's a silly little program that will make holes in windows when you press a mouse key over the window.

Problem is:

I was playing with it and I guess I "shot" the desktop two times. When I start Compiz, I can see the holes. I can't seem to be able to get rid of them.

I am using the newest repos from Trevinio for Compiz-Fusion, Ubuntu with Gnome Desktop, on a System76 Serval Performance Type 1 laptop.

I'm sure it is something simple, but if anyone could tell me how to reset this on my desktop, I would be most grateful.

Thanks in advance.

-SE

EDIT:

Attached is photo of desktop with two "holes" showing in the middle of the desktop.

[B]EDIT:

I went to my /home folder and found a folder named 

.metacity

Knowing that was my window manager, I opened it and in it was a folder named

sessions

and it that was a file containing all of my Metacity sessions.

The last three were a little different than the rest. I deleted the last three, restarted and now the problem no longer exists.

[/B]

---

### Post by ajgreeny on 2007-08-25
Don't know the program, but look in your home folder for a subfolder (probably hidden) called .blast and trash it for now.  This may contain config files for blast that remember the holes you made.  If that doesn't work, try uninstalling blast completely with synaptic or apt-get and see if that does the trick, you can always reinstall - just don't blast holes in anything important next time

---

### Post by steveneddy on 2007-08-26
> **ajgreeny said:**
> Don't know the program, but look in your home folder for a subfolder (probably hidden) called .blast and trash it for now. 

Did that already. That was the first thing I looked for.

>  This may contain config files for blast that remember the holes you made.  If that doesn't work, try uninstalling blast completely with synaptic or apt-get and see if that does the trick, you can always reinstall - just don't blast holes in anything important next time

And I uninstalled and reinstalled and uninstalled.

Now I have it installed just to find the crazy config file. 

I've tried 

```
locate  blast
```

in terminal, but nothing significant comes up.

Anyone have an idea about this?

:popcorn:

---

