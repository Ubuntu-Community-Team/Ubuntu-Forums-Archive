---
title: "Authentication failed"
date: 2007-11-20
forum: General Help
---

### Post by alin4lex on 2007-11-20
at the spash screen appears "Authentication failed" and i can't do anything.

what should i do ?

L.E. - i am running gutsy

---

### Post by geirha on 2007-11-20
What splash screen? the one that shows a progress bar during boot? 

Does it display any other text before or after?

Can you boot in recovery mode?

---

### Post by alin4lex on 2007-11-20
the one where i must type the username

how to boot in the recovery mode ?

---

### Post by taurus on 2007-11-20
Press <Ctrl><Alt>F2 and see if you can log in with your username and password.

---

### Post by alin4lex on 2007-11-20
yes, i did that, it works

---

### Post by geirha on 2007-11-20
Ok, so it doesn't recognize your username and password?

To boot recovery mode, you need to restart and hit ESC when it reaches grub. It should display that you can hit ESC to get a menu at that time. When you get that menu, choose the second boot option (not necessarily second but usually is) it should state recovery mode or something behind it.

In recovery mode, you'll get a root-shell. Type ```
passwd **username**
``` to make a new password for your account (change **username** with your username of course). When the password is set, hit CTRL+d

---

### Post by alin4lex on 2007-11-20
the password has been changed, but after ctrl+d it shows the same error "Authent....."

---

### Post by taurus on 2007-11-20
Can you post

```
df -h
ls -la ~
```

---

### Post by alin4lex on 2007-11-20
not really..
i can't acces the browser on that computer

what exactly do you want to know ?

---

### Post by geirha on 2007-11-20
Could be a mismatch between english and your (romanian?) keyboard layout maybe. If you're using any characters specific for your keyboard layout or special symbols, could you set a password with only english letters and/or digits, just to see if that works?

---

### Post by alin4lex on 2007-11-20
i have installed only english keyboard layout, and my password is only (a-z)

---

### Post by icheyne on 2007-12-30
[http://ubuntuforums.org/showthread.php?p=3605925](http://ubuntuforums.org/showthread.php?p=3605925)

---

