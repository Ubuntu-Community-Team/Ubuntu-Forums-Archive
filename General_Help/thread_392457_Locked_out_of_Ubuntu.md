---
title: "Locked out of Ubuntu"
date: 2007-03-24
forum: General Help
---

### Post by holmb101 on 2007-03-24
Recently I made some changes while trying to get the multimedia keys on my dell laptop working.
I was following this tutorial.  [http://ubuntuforums.org/showthread.php?t=12159&highlight=multimedia+keys+dell ]("http://ubuntuforums.org/showthread.php?t=12159&highlight=multimedia+keys+dell")

The problem arose when I restarted my computer and tried logging back into ubuntu.  Entering my username and password just makes a sound, but doesn't say the username password is wrong.  I am then asked for my username / password again.  

I am able to log into my user account after pressing Ctrl-Alt-F1, so I know my password is correct. 
How can I get back into my ubuntu??? Newbie:(

---

### Post by Cappy on 2007-03-24
Doing
```

sudo cp /etc/X11/gdm/PostLogin/Default /etc/X11/gdm/PostLogin/Default.sample

```
should undo anything the tutorial did.

---

### Post by holmb101 on 2007-03-24
It's working again. I had to delete the /PostLogin/Default file.  Thanks for the help.

---

### Post by Cappy on 2007-03-24
oops that should have been a "mv" =*(

---

