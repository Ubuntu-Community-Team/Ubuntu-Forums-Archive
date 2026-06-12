---
title: "how do you change ubuntu/kubuntu bootup screen?"
date: 2007-02-23
forum: General Help
---

### Post by cisforcojo on 2007-02-23
Hey all,

I'm running Ubuntu 6.10 and installed kubuntu-desktop to see what KDE was like on the dist. Didn't like it so I removed it but the kubuntu bootup screen is still there. How can I change it back to the original ubuntu bootup? Thanks.

Collen

---

### Post by crispy_420 on 2007-02-23
remove kubuntu-artwork-usplash?

just a guess

---

### Post by chggr on 2007-02-23
System -> Administration -> Login Window -> Choose the theme you like!

---

### Post by cisforcojo on 2007-02-24
Nope, says not installed.

---

### Post by cisforcojo on 2007-02-24
chggr, that's the login window, I mean when Ubuntu is loading and the progress bar is sliding, it's a blue kubuntu screen instead of the original Ubuntu one. Thanks for the help though.
The login window is set correctly.

---

### Post by Cobikegeek on 2007-02-24
This worked for me.

HT change the boot splash and shutdown splash to Ubuntu (or kubuntu)

code:

sudo update-alternatives  --config usplash-artword.so   
#that's 2 dashes before config with no space between them but a space after alternatives)

sudo dpkg-reconfigure

---

