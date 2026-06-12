---
title: "CompizFusion Killed my Desktop Effects"
date: 2007-12-03
forum: General Help
---

### Post by reshter on 2007-12-03
I tried installing Compiz Fusion.  It killed my desktop effects.  I uninstalled it, but they are still dead.  I'm stupid, and I can't fix it.  when I click "extra" in the desktop effects, it says "failed to compile compiz" or something like that.  Any idea why?

It's not a huge deal, but it did look nicer, and I like when everything on my computer works.

---

### Post by -grubby on 2007-12-03
the desktop effects are compiz

---

### Post by reshter on 2007-12-03
They didn't work, and are still ****** up.  I know that compiz are the effects, but they ****** up the standard ones.

---

### Post by -grubby on 2007-12-03
using feisty I suppose?

---

### Post by khurrum1990 on 2007-12-04
Hi, did u install a custom compiz fusion version on Gutsy? If so u should have been very careful and there r chances of a breakage in which case u may need to do a complete reinstall to get them to work. If u r using Feisty then just remove every compiz fusion package installed and then reinstall it. You can also use beryl on fiesty, it works better on it then compiz fusion does anyway.
"sudo apt-get install beryl beryl-manager emerald emerald-themes"
Good Luck!

---

### Post by reshter on 2007-12-04
I'm using ubuntu 7.10

If i have to do a reinstall, is there a way I can keep my files?  I'm a Ubuntu noob.

edit- and also on my mom's user, the windows appear under th e top bar and are hard to get to, so you can't move/close them.

---

### Post by pointone on 2007-12-04
Please post the output of running this command in a terminal:

```
compiz --replace
```

---

### Post by reshter on 2007-12-04
```

jim@jimix:~$ compiz --replace
The program 'compiz' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-core
bash: compiz: command not found

```

Should I try installing it using the command it said?

---

### Post by pointone on 2007-12-04
Most definitely.

---

### Post by reshter on 2007-12-04
OK, i reinstalled.  It worked.  When I chose Extra/Normal, all the title bars went away..  Is there more stuff I have to install?

i heard about beryll and emrald, but isn't compiz a hybrid of them?

---

