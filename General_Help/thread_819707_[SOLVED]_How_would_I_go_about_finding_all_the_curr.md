---
title: "[SOLVED] How would I go about finding all the currently install packages on my machin"
date: 2008-06-05
forum: General Help
---

### Post by Lord Xeb on 2008-06-05
When and if I reformat and reinstall (which seems to be a habit of mine) I want to be be able to just go into terminal, type in:

```
sudo apt-get install <all my previous packages>
```

and be able to install of the packages I had before hand. Is there anyway to put in a command in terminal to find all currently installed packages so I can make a list of them?

---

### Post by drs305 on 2008-06-05
To create a list of installed apps:
```
sudo dpkg --get-selections >~/Desktop/installed-pkgs
```

To restore them:
```
sudo dpkg --clear-selections
dpkg --set-selections <~/Desktop/installed-pkgs 
sudo apt-get dselect-upgrade

```

---

### Post by Lord Xeb on 2008-06-05
Thanks for the help! ^_^

---

