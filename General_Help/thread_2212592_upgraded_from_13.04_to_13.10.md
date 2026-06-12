---
title: "upgraded from 13.04 to 13.10"
date: 2014-03-21
forum: General Help
---

### Post by addison2 on 2014-03-21
i just upgraded from 13.04 to 13.10 and had a few errors during the upgrade. after it reboot the ubuntu logo doesn't seem to appear and when i start up i get a crash error when update-manager tries to load. also the borders around any of my windows are black and none of the buttons like close, minimize and expand/retract are shown at all. is there any solutions to fix this?

---

### Post by Bashing-om on 2014-03-22
addison2; Maybe (?)

Let's say when you upgraded the system from version 13.04, the repository for 13.04 had been closed down and as such the upgrade process did not complete.
Look at the sources.list file and make sure that all entries are 'suacy', that no 'raring' entries exist:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
Then, Let's try this:
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
All that does is update it again.

```

Now, reboot and let's see where we stand, hopefully all is good now.

[INDENT][INDENT]it is 'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

