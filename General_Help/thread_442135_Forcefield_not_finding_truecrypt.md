---
title: "Forcefield not finding truecrypt"
date: 2007-05-13
forum: General Help
---

### Post by priegog on 2007-05-13
Hi.
The problem I have, is I want to use forcefield to use truecrypt graphically (I thought it was great under windows), So I installed both programs with automatix2 for feisty (I am using Ubuntu Feisty).
But when I either click on the menu icon for forcefield, or type "forcefield" in the console, a window appears (presumably the forcefield one) with an incorrectly showing error message. When I close the error message (clicking on the x), a message comes up asking me to either wait or kill the process. Said message says (no editing, it appears exactly as random aligned as you are seeing it):
 
"Forcefield need truecrypt to be installed with suid bit set.
                          Sorry for that.
" is not responding.

Since then, I've tried uninstalling and reinstalling everything with various methods, including automatix, apt and synaptic. 
Any ideas? I really like this encryption program

---

### Post by cgrahge on 2007-05-13
> **priegog said:**
> Hi.
The problem I have, is I want to use forcefield to use truecrypt graphically (I thought it was great under windows), So I installed both programs with automatix2 for feisty (I am using Ubuntu Feisty).
But when I either click on the menu icon for forcefield, or type "forcefield" in the console, a window appears (presumably the forcefield one) with an incorrectly showing error message. When I close the error message (clicking on the x), a message comes up asking me to either wait or kill the process. Said message says (no editing, it appears exactly as random aligned as you are seeing it):
 
"Forcefield need truecrypt to be installed with suid bit set.
                          Sorry for that.
" is not responding.

Since then, I've tried uninstalling and reinstalling everything with various methods, including automatix, apt and synaptic. 
Any ideas? I really like this encryption program
truecrypt can be used easily from the command line. Forcefield is a little unstable and is not maintained by the truecrypt devs. It's an independent project. From what I understand, Automatix hosts these packages in its repositories.
```
truecrypt
```

The message on Forcefield is not incorrect. It actually wants SUID bit added to truecrypt. So just click on "Fix SUID bit" and then it will work just fine.

---

### Post by bushwacker on 2007-05-17
On the truecrypt binary or the forcefield .py file(s)?

---

### Post by priegog on 2007-05-17
Hi. A few days ago an update for forcefield came and that fixed it. So thanks a lot for the help :)

---

### Post by oldtappan on 2007-05-21
> **priegog said:**
> Hi. A few days ago an update for forcefield came and that fixed it. So thanks a lot for the help :)

Where did you get the forcefield bits from?

I tried to build [from source]("http://bockcay.de/forcefield/wiki") but it didn't work for me.

---

### Post by priegog on 2007-05-21
Hum... I installed forcefield and truecrypt with automatix and it must've added some repos through which came the update.

---

### Post by ahbart on 2008-04-28
Maybe you already know, but truecrypt has a GUI now!
Same as in windows:
[http://www.truecrypt.org/](http://www.truecrypt.org/)
Works great
Bart

---

