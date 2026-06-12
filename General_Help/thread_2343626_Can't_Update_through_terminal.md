---
title: "Can't Update through terminal"
date: 2016-11-17
forum: General Help
---

### Post by h1nx on 2016-11-17
So my wife was messing with my computer and now I can't update through the terminal and when I try to use the software updater that doesn't open. I also get system crash notifications when I turn on my computer. They appeared at the same time so I think that they may be related somehow. I have tried to just reinstall Ubuntu over again but my LiveUSB wont boot.

The error i get in the terminal is

E: Line 1 too long in source list /etc/apt/sources.list.d/medibuntu.list.
E: The list of sources could not be read.

---

### Post by oldos2er on 2016-11-17
Medibuntu? Haven't hear that word in awhile. Please tell us which Ubuntu version you're using. ```
sudo rm /etc/apt/sources.list.d/medibuntu*

sudo apt-get update
```

---

### Post by Bucky Ball on 2016-11-17
Welcome. You would need to get rid of this:

/etc/apt/sources.list.d/medibuntu.list

Open a file browser, go to that folder (/etc/apt/source.list.d/) then delete the offending file (medibuntu.list). You may need to open a file manager as root to do this or use the terminal.

Looks like she's tried to add a repo that is [no longer supported and well dead]("https://help.ubuntu.com/community/Medibuntu").

Delete that file 'medibuntu.list' and reboot then open terminal and:

```
sudo apt autoremove
sudo apt update
sudo apt upgrade
```

* Ninja-ed by oldos2er. ;) Their command will work fine to get rid of that file also. :)

PS: Always good to include the release number and flavour of the Ubuntu you are using when posting for support. :)

---

