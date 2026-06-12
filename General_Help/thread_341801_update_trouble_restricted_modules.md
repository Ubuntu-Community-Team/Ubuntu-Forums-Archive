---
title: "update trouble restricted modules"
date: 2007-01-19
forum: General Help
---

### Post by feest on 2007-01-19
Hi, i'm using edgy for a couple of months now and i really like it, i could easily setup beryl en it boots fast, however i got some trouble with a certain update "linux-restricted-modules". and i can install them, it says that i need to updat my distribution to 6.10 (i'm already running edgy :confused: :confused: :confused:  and when i try to do it it gives an error. 

[http://www.ubuntuforums.org/attachment.php?attachmentid=22675&d=1168439431](http://www.ubuntuforums.org/attachment.php?attachmentid=22675&d=1168439431) 

how do i solve this? is it an idea to install these modules by hand?

---

### Post by Ramses de Norre on 2007-01-19
What's the output of **sudo aptitude update**?
I think it could have to do with packages from the beryl repo...

---

### Post by az on 2007-01-19
> **feest said:**
>  is it an idea to install these modules by hand?

sudo apt-get dist-upgrade

or pick the "smart upgrade" option.

---

### Post by feest on 2007-01-19
> **Ramses de Norre said:**
> What's the output of **sudo aptitude update**?
I think it could have to do with packages from the beryl repo...

sudo apitude update works fine, however, i still can't updat my restricted modules,  distr-upgrade doesn't work since i already have 6.10
beryl repo's are disabled because they gave 404 errors

---

### Post by az on 2007-01-19
> **feest said:**
> distr-upgrade doesn't work since i already have 6.10


Exactly what do you mean by this?

---

### Post by feest on 2007-01-20
that ubuntu says i need to update to edgy eft for this module but i'm already running edgy eft.

---

### Post by az on 2007-01-20
> **feest said:**
> that ubuntu says i need to update to edgy eft for this module but i'm already running edgy eft.

Do you have mixed repositories?  As well, you seem to need to update some packages.  Just dist-upgrade and everything should fix itself - provided you don't have mixed repositories.  

Make sure that the ubuntu-desktop package does not get removed.

---

### Post by feest on 2007-01-21
i don't have mixed repo's *** far as i know but i think i exidantly removed ubuntu desktop, will have a look.

---

### Post by feest on 2007-01-21
well you fixed that problem i guess (no more update icon :):):):)) THX!!!!! but now another minor problem occured,

i removed totem-mozilla plugin to activate mplayer plugin because the totem plugin couldn't play everything, mplayer could. but totem plugin, wanted to remove ubuntu-desktop (wich was the problem) now with ubunt-desktop back installed totem takes mozilla again, how do i uninstall it or deactivate it without removing ubuntu-desktop

---

### Post by az on 2007-01-21
> **feest said:**
> how do i uninstall it or deactivate it without removing ubuntu-desktop

Now that you are up-to-date, it's okay to remove ubuntu-desktop.

---

