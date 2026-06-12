---
title: "Gnome Software auto update?"
date: 2016-05-19
forum: General Help
---

### Post by VE6EFR on 2016-05-19
Is there a way to have Gnome software automatically apply updates that are available in a similar way that software updater works? It seems as if every time I open the laptop Gnome software tells me there are updates available instead of just doing the updates behind the scenes like software updater does.

---

### Post by goofprog on 2016-05-19
It should update all together.  Maybe a PPA needs to be included to get the bleeding edge version of gnome software.

---

### Post by Linuxisfast on 2016-05-19
The Software updater does its job, the gnome software database is not updated so no issues.

---

### Post by jim_deadlock on 2016-05-20
I have to say, my 50unattended-upgrades file is set to upgrade everything automatically, but Gnome Software still insists on popping up now and then despite "Automatically check for updates - Never".

---

### Post by jim_deadlock on 2016-05-20
And why do apt and Gnome Software report 2 different lists of upgrades?

```
# sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  appstream libappstream3
2 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 129 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
```

[ATTACH=CONFIG]269180[/ATTACH]

...and why is Gnome Software reporting upgrades for packages that are already the latest versions?

```
# sudo apt install fonts-noto-cjk language-selector-common python-urllib3 python3-urllib3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fonts-noto-cjk is already the newest version (1:1.004+repack2-1~ubuntu1).
language-selector-common is already the newest version (0.165.2).
python-urllib3 is already the newest version (1.13.1-2ubuntu0.16.04.1).
python3-urllib3 is already the newest version (1.13.1-2ubuntu0.16.04.1).
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.
```

---

