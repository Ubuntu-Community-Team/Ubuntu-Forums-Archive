---
title: "Annoying problem."
date: 2008-03-17
forum: General Help
---

### Post by danbrownlow on 2008-03-17
Whenever I go to install some software in terminal. I get the message:

Do you want to continue [Y/n]? y
Media Change: Please insert the disc labelled
 ‘Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)’
in the drive ‘/cdrom/’ and press enter

Does anyone know why this could be?

Dan Brownlow.

---

### Post by NightwishFan on 2008-03-17
Are the repositories enabled? Try:
```
sudo apt-get update
```

---

### Post by jken146 on 2008-03-17
Go to System -> Administration -> Software Sources and remove the CDROM from the list.

---

### Post by prshah on 2008-03-17
> **danbrownlow said:**
> Whenever I go to install some software in terminal. I get the message:

Do you want to continue [Y/n]? y
Media Change: Please insert the disc labelled
 ‘Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)’
in the drive ‘/cdrom/’ and press enter

Does anyone know why this could be?

Dan Brownlow.

Quick way to get rid of it... Applications->Add/Remove->Preferences->Ubuntu Software tab... at the bottom you will find an entry for this cdrom, uncheck it and you will not be asked for the CD in the future.

---

