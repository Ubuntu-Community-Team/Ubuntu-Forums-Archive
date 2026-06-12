---
title: "Remote Access"
date: 2007-03-24
forum: General Help
---

### Post by tictacman on 2007-03-24
I have not had any need to use remote services before, so I would appreciate it if someone could point me in the right direction.

I have xubuntu machine hooked up to my tv to play music and video files.  For a while I've been using samba to transfer files across and this has served me just fine until recently.  Now I would like to administer the box from a linux client box so I don't have to hog the tv :).  Sort of things I have in mind are moving and renaming files, installing updates and shutting the machine off at night.

There seems a number of ways to do this ssh server, xdmcp, vnc.  The host machine is not particularly fast so while visual desktop access would be nice I'm happy to use a shell.  Also if I use one of these remote servers can I use them to transfer files and turn samba off?

---

### Post by jeffathehutt on 2007-03-24
If you are comfortable using the command line, ssh is your best option.  That would allow you to log in from another computer and do things such as shutting it down.  I'm sure you could also turn samba off, but I have no experience with samba so I'm not sure how you would do that.  Also with ssh, you can use sftp to transfer files.  I'm pretty sure konqueror can do this automatically (but I may be wrong, I don't use kde).

If you want a graphical environment, vnc might work, but it could be too slow, not to mention there is no security at all.  NX might be a good alternative, since it is secure and about as fast as vnc.

---

### Post by tictacman on 2007-03-24
Thanks for the reply looks like its going to be ssh then.  Something I forgot to ask, is ssh still the best option even though 'remote' box is on my network rather than out there in 'cyber space'?

---

### Post by jeffathehutt on 2007-03-24
Yes, ssh would still be the best option.  Telnet works similar to ssh, but it offers no encryption and virtually no speed improvement.

---

