---
title: "&quot;k&quot; key does not work"
date: 2007-12-11
forum: General Help
---

### Post by UltraDavid on 2007-12-11
I've been trying to figure this out for the past few hours and haven't found anything on the web that speaks to my problem, so sorry about making a new thread.

My "k" key doesn't work (right now I have the letter "k" copied and push ctrl+v every time it comes up).  The key itself works when I modify it with my function, ctrl, alt, and shift keys (so I can type uppercase K still etc), but whenever I push it by itself, I get a little bubble that says, "Text was empty (or contained only whitespace)."  This happens when I have caps lock on too; the only time I don't get that message when pressing the k key is when I'm simultaneously pressing a button that modifies it.  It happens every time I push the button, not only in one program or box or anything.  Also, this is the only key on my whole keyboard that has any problems.

I first noticed this after I tried to get Compiz Fusion working earlier in the day.  I was linked to this [thread]("http://ubuntuforums.org/showthread.php?t=508769&highlight=compiz+fusion") , downloaded the file from the "Download CF Installer-Updater Version 3" link, and then put "bash CF_Installer-Updater_v.X.sh" in a terminal.  Right after that is when the key stopped working. At the time I didn't notice the warning at the top of that page to not use it.

Anyone have any idea what the problem is?

---

### Post by 11hjpphty76lkjj on 2007-12-11
If you boot from the live cd does it still do it?

A

---

### Post by DagMan on 2007-12-11
compiz-fusion has uses a lot of hotkeys and it sounds like something in the settings has decided to use the k key by itself for some sort of function.

Try installing the settings manager, or not if you already have the extra settings thing, and play with turning things on and off and see if one of them allows you to use the key, and if so go to the last tab where 'Actions' are and find the offending function and change it to something else.

Alternatively, to see if that's even the problem worth looking into to begin with, do metacity --replace at the terminal and see if the k key works using metacity.

---

### Post by UltraDavid on 2007-12-11
Yeah, that was the problem!  Compiz-Fusion had assigned the k key to a command (although how that happened in the first place, I'm not sure).  All I had to do was change that command, and the problem was fixed.

Thanks a lot!

---

