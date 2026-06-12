---
title: "effects(cant find a better name ;)"
date: 2008-05-08
forum: General Help
---

### Post by fimman on 2008-05-08
when i try to set visual effects(system-pref-app) to normal-extra or custom the screen turns white and then it goes back to normal but the effects havent changed :/ i have the newest driver installed through restricted drivers manager

i have nvidia geforce 7600 gs and it used to work to put effects on


does anyone know how to fix this :)?

---

### Post by mano cazalet on 2008-05-08
did you install compizconfig-settings-manager?

```
sudo apt-get install compizconfig-settings-manager
```

it installs Advanced Desktop Effect Settings in System - Preferences
and it should work with that

---

### Post by fimman on 2008-05-08
> **mano cazalet said:**
> did you install compizconfig-settings-manager?

```
sudo apt-get install compizconfig-settings-manager
```

it installs Advanced Desktop Effect Settings in System - Preferences
and it should work with that

ive already done that the problem is with visual effects
and advanced dekstop effects setting doesnt work without visual effects

---

### Post by mano cazalet on 2008-05-08
is your compiz running?
what is the output of:
```
ps ax | grep compiz
```

---

### Post by mireson on 2008-05-09
I am having a similar/same issue. Running 8.04 on a compaq evo N610c, i think a rage mobility 7500. ran desktop effects on 7.10
On 8.04, i go to System -> Preferences -> Appearance, visual effects tab, click on "normal" radio button, screen whites out briefly, comes back with: "Desktop effects could not be enabled" and the radio button stays on "none"

I've tried your solution so far, still need help. my output from "ps ax | grep compiz" is:

 7447 pts/0    R+     0:00 grep compiz

---

### Post by fimman on 2008-05-09
> **mano cazalet said:**
> is your compiz running?
what is the output of:
```
ps ax | grep compiz
```
msi@msi-desktop:~$ ps ax | grep compiz
 6147 pts/0    S+     0:00 grep compiz

---

### Post by mireson on 2008-05-25
did you get this working, i still have no idea...

---

### Post by Forlong on 2008-05-25
Try this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
If it fails, post the output here.

---

