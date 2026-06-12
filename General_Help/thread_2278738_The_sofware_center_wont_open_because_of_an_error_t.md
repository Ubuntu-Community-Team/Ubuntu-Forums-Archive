---
title: "The sofware center wont open because of an error that I cant solve"
date: 2015-05-18
forum: General Help
---

### Post by Chris_Bell on 2015-05-18
[ATTACH=CONFIG]262057[/ATTACH] "E: the package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it"

---

### Post by Chris_Bell on 2015-05-18
*I've also tried "gksudo software-center"*

---

### Post by coffeecat on 2015-05-18
> **Chris_Bell said:**
> [ATTACH=CONFIG]262057[/ATTACH] "E: the package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it"

You probably tried to install mscorefonts or ubuntu-restricted-extras (which includes the mscorefonts) but didn't notice the EULA that needed to be agreed to. Try this. Open a terminal and run this command:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

Don't leave the terminal unattended while this operation proceeds. After a few minutes you will be presented with the Microsoft EULA which you must agree to otherwise the installation fails. Press the TAB key to highlight OK, and then press ENTER.

> **Chris_Bell said:**
> *I've also tried "gksudo software-center"*

Ouch!!

A few releases ago, running software-center with root privileges caused permissions problems in the user's home directory. There is no need to run software-centre with gksudo. When and if software-center needs admin authorisation it will prompt you for it. Let's hope you haven't created more problems with this.

---

