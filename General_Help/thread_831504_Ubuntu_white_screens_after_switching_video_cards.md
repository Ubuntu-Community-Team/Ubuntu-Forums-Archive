---
title: "Ubuntu white screens after switching video cards"
date: 2008-06-15
forum: General Help
---

### Post by alexeix on 2008-06-15
I've got this problem too.  It started after changing my graphics card from an nVidia 5xxx passive card to an ATI 9600 (worked fine) and then back to the nVidia.

Now, using the nVidia again, after logging in, I get a white screen.  If I log in with a lower priviledge user account, I can access the desktop fine.

As a realtive Ubuntu novice (I know how to enter commands and navigate directories, but need instructions...), I'm not exactly sure what to do.

Help?!

---

### Post by PmDematagoda on 2008-06-15
Reconfigure your X-Server using nvidia-settings:-
```
sudo nvidia-xconfig
```
that should fix it.

---

### Post by alexeix on 2008-06-16
Thanks for the suggestion. 

How do I get to a terminal prompt though?  I've tried from the other user account (there are only two), but it doesn't have admin rights.

---

### Post by alexeix on 2008-06-16
Bump!  :confused:

---

### Post by PmDematagoda on 2008-06-16
> **alexeix said:**
> Thanks for the suggestion. 

How do I get to a terminal prompt though?  I've tried from the other user account (there are only two), but it doesn't have admin rights.

Login to the user account with admin rights, switch to a tty by pressing Ctrl+Alt+F1 and execute the command, afterwards do:-
```
sudo /etc/init.d/gdm restart
```

---

### Post by alexeix on 2008-06-17
Thanks!  I haven't checked your advice though, because I found a solution last night.

See this thread:
[http://ubuntuforums.org/showthread.php?t=824744&highlight=metacity+white](http://ubuntuforums.org/showthread.php?t=824744&highlight=metacity+white)

I subsequently re-enabled the nVidia drivers and that fixed the problem.

Cheers.

---

