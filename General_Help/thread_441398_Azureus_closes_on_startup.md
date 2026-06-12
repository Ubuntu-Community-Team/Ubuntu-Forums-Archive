---
title: "Azureus closes on startup"
date: 2007-05-12
forum: General Help
---

### Post by shiznatix on 2007-05-12
Ok so I installed azureus then I was downloading some torrents then my laptop battery died so my computer did a hard shut down. Now when I try to open azureus, as soon as the window opens it closes again. I tried uninstalling it then reinstalling it but that did not change anything. Any help would be appreciated.

---

### Post by taurus on 2007-05-12
What happens if you run it from a terminal?

```
azureus
```
And when you uninstall it, make sure you also remove the config files in your $HOME directory, ~/.azureus.

```
rm -rf ~/.azureus
```

---

### Post by artir on 2007-05-12
Same thing happpened to me.
SOlution:


rm -rf ~/.azureus && sudo apt-get remove  --purge azureus && sudo apt-get install azureus && sudo update-alternatives --config java

Then It will ask you for a number. I tried with 1.4 and 6.0(or sth like that) and didnt work, so i picked option number ONE (enter an 1) and press enter. Then start azureus
Happy downloading!

---

