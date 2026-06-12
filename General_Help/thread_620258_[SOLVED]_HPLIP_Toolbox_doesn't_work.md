---
title: "[SOLVED] HPLIP Toolbox doesn't work"
date: 2007-11-22
forum: General Help
---

### Post by FuturePilot on 2007-11-22
I installed the hplip-gui package, but it doesn't work. This is what I get when running it from the terminal.
```
error: GUI mode disabled in build. Exiting.
```
Why is the GUI disabled in the hplip-**gui** package:confused:
Any way to get this working?

---

### Post by linuxwizard on 2007-11-22
I never had to install the hplip-gui package to get HPLIP Toolbox to work. In Terminal >  hp-toolbox > it should open telling you to install > python-qt3, python-sip4, libqt3-mt > install these. Than HPLIP Toolbox will work from terminal or add it to your menu. This has worked for me in Ubuntu  Dapper,Edgy,Feisty,Gusty.

---

### Post by FuturePilot on 2007-11-22
Hmmm. I removed hplip-gui and ran hp-toolbox from the terminal but
```
:~$ hp-toolbox 

HP Linux Imaging and Printing System (ver. x.x.x)
HP Device Manager ver. 10.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: GUI mode disabled in build. Exiting.

```
:confused:
This is on a fresh install of Gutsy

---

### Post by linuxwizard on 2007-11-22
Did you install those 3 packages that I posted ?

---

### Post by FuturePilot on 2007-11-22
Yep, those were already installed. This is totally bizarre. Am I the only one getting this?:confused:

---

### Post by FuturePilot on 2007-11-22
Fixed. Purged hplip and reinstalled it. I think I know what happened now. I had tried to install the latest version of HPLIP a while ago and something must have been conflicting.

---

