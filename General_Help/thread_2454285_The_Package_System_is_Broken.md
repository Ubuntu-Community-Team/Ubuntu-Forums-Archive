---
title: "The Package System is Broken"
date: 2020-11-26
forum: General Help
---

### Post by Gordonbp531 on 2020-11-26
Ubuntu Mate 20.04.1 - I run nthe Sodtware Updater, it gives a list of updates to instal.
I click on "Install now" and I get "The Package System is Broken".
How do I repair it?

---

### Post by CelticWarrior on 2020-11-26
Please run ```
sudo apt update
``` followed by ```
sudo apt full-upgrade
``` and post back here the output in code tags.

---

### Post by Gordonbp531 on 2020-11-26
Sudo apt update:```
254 packages can be upgraded. Run 'apt list --upgradeable' to see them
```

Sudo apt full-upgrade: Comes up with ```
try 'apt --fix-broken install"
```

So going to try that and report back.

---

### Post by Gordonbp531 on 2020-11-26
All worked OK - the only thing that went "wrong" is that the initial full-upgrade hung, so I had to restart the machine and issue the command again.
All now updated properly. Thanks for the input.

---

