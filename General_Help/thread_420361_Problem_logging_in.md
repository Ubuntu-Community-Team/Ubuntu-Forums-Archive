---
title: "Problem logging in"
date: 2007-04-23
forum: General Help
---

### Post by Aethendar on 2007-04-23
After rebooting as a part of trying to fix a screen resolution issue, I now can't log in to Ubuntu anymore. I type in my username and my password, then I'm taken (very briefly, too fast to even see what it says) to a black screen with some white writing, looks kinda like commands or something...then I'm back to the login screen again. :/ 

Anyone know what might be wrong?

---

### Post by bapoumba on 2007-04-23
From the GDM login screen, hit CTRL-ALT-F2, you get to a tty (not your usual session, this will be a command line session), login (give your username and password), and run **df -H**. You may be running out of space. If so:
```
sudo aptitude clean
```
will make some room on your root (/) partition, and you should be able to login again to your graphic session (CTRL-ALT-F7 to go back).

---

### Post by Aethendar on 2007-04-23
Thanks, but when I get to the tty I also get ported back to the original logon screen :/ Also, there should be just below 50GB free space on my root partition, so I don't think that's the problem...

---

### Post by alinuxfan on 2007-04-25
thanks for the fix.
Man, I thought that partitioning 14G for my root partition would be enough...
I guess not


Thanks again

---

### Post by bapoumba on 2007-04-25
> **alinuxfan said:**
> thanks for the fix.
Man, I thought that partitioning 14G for my root partition would be enough...
I guess not
Thanks again
14Go should be way enough (I have 8.3 Go for the system, both GNOME and xfce barely take 3.6 Go). Have you been installing a lot of things ? Downloading stuff (some torrent temp files are on /) ?

---

