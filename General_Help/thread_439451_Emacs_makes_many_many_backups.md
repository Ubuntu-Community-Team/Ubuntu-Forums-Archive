---
title: "Emacs makes many many backups"
date: 2007-05-10
forum: General Help
---

### Post by makhand on 2007-05-10
I dont really know how i did whatever it is that i must have done to make emacs make a backup every time i open a file and modify something. The outcome is that when i'm working on certain files which i'm constantly modifying (.cpp, .py, etc), I soon have a full directory of: 

filename.py.~1~
filename.py.~2~
filename.py.~3~
filename.py.~4~
...
filename.py.~16~
filename.py.~17~
...
filename.py.~21~

and so on.  Every time i reopen the file, make a new change, and save it again, i get a new little backup. 

Has anyone run into this problem or know how to fix it? thanks

---

### Post by peter3 on 2007-05-10
Have a look at:
[http://www.cs.cmu.edu/cgi-bin/info2www?(emacs)Backup%20Names](http://www.cs.cmu.edu/cgi-bin/info2www?(emacs)Backup%20Names)
which looks like it is talking about your concern.

Peter

---

### Post by makhand on 2007-05-10
Thanks. Looks like this really is what i'm looking for. now i just need to figure out where to set these values.

---

