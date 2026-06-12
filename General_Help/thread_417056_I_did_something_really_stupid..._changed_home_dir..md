---
title: "I did something really stupid... changed home dir. to home"
date: 2007-04-21
forum: General Help
---

### Post by Kdar on 2007-04-21
I made the home directory of my user to "/home"
instead of /home/user"

I restarted X server....

And now I cannot log in..  Sad to X

How do I changed it in "failsave mod" in console?

PS. I have KDE.

---

### Post by acormack on 2007-04-21
If you log in in console mode ctrl-alt-f1 

then sudo su

then edit /etc/passwd

find the line for your username

the home directory is the penultimate value

---

### Post by mhansen on 2007-04-21
> **Kdar said:**
> I made the home directory of my user to "/home"
instead of /home/user"

I restarted X server....

And now I cannot log in..  Sad to X

How do I changed it in "failsave mod" in console?

PS. I have KDE.


You overwrote /home if I read u right?  Just mv /home to /username, mkdir /home, then mv /username to /home/

permissions for /home drwxr-xr-x root root



Regards,
Mike

---

