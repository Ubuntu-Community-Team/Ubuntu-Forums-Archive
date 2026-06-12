---
title: "kio_trash"
date: 2007-01-04
forum: General Help
---

### Post by t1m on 2007-01-04
Hi all,
For some strange reason I can't empty my trash can. (Maby it has glue in it?!)
When I do it says "Could not start process Unable to create io-slave:
klauncher said: Error loading 'kio_trash'.". :( Does anyone know what I should do? I've tried looking on the forums/web and couldn't seem to find an answer.
Tnx ;)

---

### Post by scrooge_74 on 2007-01-05
did you try from a terminal window cd /.Trash and then rm *

maybe you have a file in it with the wrong permits and it does not let you clean the trash.  

You are in KDE right? This happen to me in Gnome so I am not sure is the same problem

---

### Post by Lord Illidan on 2007-01-05
> **scrooge_74 said:**
> did you try from a terminal window cd /.Trash and then rm *

maybe you have a file in it with the wrong permits and it does not let you clean the trash.  

You are in KDE right? This happen to me in Gnome so I am not sure is the same problem

That is the Gnome Trash.

The KDE Trash is in ~/.local/share/Trash

---

### Post by scrooge_74 on 2007-01-05
Thank you for correcting me, I really have 0% experience with KDE

:D

---

### Post by Lord Illidan on 2007-01-05
> **scrooge_74 said:**
> Thank you for correcting me, I really have 0% experience with KDE

:D

No problem, I learned that 2 days ago.

---

### Post by t1m on 2007-01-06
Thank you for your replys. I found out that when I went on our home network that some network kio wasn't working either. So I went to Adept and searched for "kio" and reinstalled most of them.... FIXED! :KS  The trash is emptying right now :)
:biggrin:

---

