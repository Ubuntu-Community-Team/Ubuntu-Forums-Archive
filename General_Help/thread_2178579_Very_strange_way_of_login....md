---
title: "Very strange way of login..."
date: 2013-10-04
forum: General Help
---

### Post by LeXav on 2013-10-04
Hi !

I've some trouble with my ubuntu desktop. (13.04 ubuntu). I can't login to my session. My password is correct, not rejected. But when I try to login, the screen become black as if he let me to go, but 2 seconds later he's back to login screen.

The strange fact is : if with my laptop I open a ssh session (same login, same password) on my desktop computer, then I can login 'the normal way'.

Why ????? :)

---

### Post by steeldriver on 2013-10-04
What do you mean by 'in the normal way'? Are you saying that once you are logged in via SSH, you can then log in to regular GUI session on the machine itself? Do you have an encrypted home directory?

If you are just saying that you can log in via an SSH (terminal) session but not start a local desktop (GUI) session, the basic answer is that your login authentication is OK, but your  chosen desktop session can't start for some reason - that reason  may be

[LIST]
[*]your ~/.Xauthority file ownership or permissions are wrong (often happens when people try running 'startx' using sudo)
[*]your whole home directory ownership or permissions are wrong
[*]your home partition (if you have a separate one) is full
[/LIST]
All the above are essentially variations of the same problem i.e. that the X server can't write to your .Xauthority file

Less common causes are things like a corrupted saved session (in your ~/.cache) or some other bad .config setting

---

### Post by enterdavertex on 2013-10-04
Some problem already happened to me with error about the X Server. try to take a look at this one.

---

### Post by whitesmith on 2013-10-04
I think this was one of my first Ubuntu problems. In setting up a separate home partition I accidentally wound up with root being the owner of $HOME. Craziness like this is the usual culprit.

---

