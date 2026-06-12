---
title: "Hsitory Function in Terminal went..."
date: 2007-03-08
forum: General Help
---

### Post by Soma1975 on 2007-03-08
Hello,

i have the problem that the History Function (arrow up key) and the other shortcut keys in the terminal window under gnome do not work any more.
And also the prompt looks different.
Normal something like this:
dud@shadowplay:~ $
and mine is just
$
or
#
with sudo -s command
I think it might be a configuration problem with the Shell or something like that....
Has anybody a tip where to look for the settings?

Thank you
Soma

---

### Post by yopnono on 2007-03-08
Check the permisson on the .bash* files in your home folder (they are hidden).

---

### Post by Soma1975 on 2007-03-08
Hello,
with ls -a -l i get those .bash* files:
-rwxrwxrwx  1 user user     10916 2007-03-07 21:02 .bash_history
-rw-r--r--  1 user user       220 2007-02-20 20:38 .bash_logout
-rw-r--r--  1 user user       414 2007-02-20 20:38 .bash_profile
-rw-r--r--  1 user user      2227 2007-02-20 20:38 .bashrc

i made chown with rwx to .bash_history but doesn´t work.
Maybe something with my keyboard layout is wrong,
because if i press the "arrow_up" key in the Terminal i get
^[[A
hmm...
Cheers
Soma

---

