---
title: "Easy way of reinstalling OpenOffice?"
date: 2007-03-13
forum: General Help
---

### Post by Quillz on 2007-03-13
I was messing around with some of the settings in OOo 2.2 RC3 when one of the options I togged (I think it was selecting an icon pack) suddenly force closed the application. Now, whenever I try to reopen it, I get the splash screen but the application again quickly vanishes and never loads. Is there a simple Terminal command to reset all settings to default, or reinstall the whole program? I'm on Kubuntu Feisty Fawn Herd 5.

---

### Post by zvacet on 2007-03-13
Wiht synaptic you shoud be fine.

---

### Post by Quillz on 2007-03-13
> **zvacet said:**
> Wiht synaptic you shoud be fine.
I'm on Kubuntu, so I'm using Adept instead of Synaptic. Does Adept have an option for reinstalling a package, or at least returning it to the default settings? I'm used to apt-get, so I haven't used Adept in a while.

---

### Post by zvacet on 2007-03-13
Yes it does.Open it,find package you want and by right click on the package you will see reinstall option.

---

### Post by WIndLi on 2007-03-13
You don't need to reinstall OpenOffice. Just remove .openoffice.org2 at your home directory. That's where OpenOffice save the configuration.

---

### Post by Quillz on 2007-03-13
> **zvacet said:**
> Yes it does.Open it,find package you want and by right click on the package you will see reinstall option.
Okay, thanks for the help.
> **WIndLi said:**
> You don't need to reinstall OpenOffice. Just remove .openoffice.org2 at your home directory. That's where OpenOffice save the configuration.
And then upon opening the program again, it sets up a new configuration file?

---

### Post by dppowell on 2007-03-22
I've got the same problem as Quillz, but deleting the config directory and relaunching didn't work.  I get the splash screen...then nada.  Back to the desktop, no errors, etc.

---

### Post by Quillz on 2007-03-23
> **dppowell said:**
> I've got the same problem as Quillz, but deleting the config directory and relaunching didn't work.  I get the splash screen...then nada.  Back to the desktop, no errors, etc.
Deleting the configuration files worked for me. Try reinstalling it via Synaptic, I guess.

---

### Post by dppowell on 2007-03-25
The problem turned out to be with fglrx; I had to manually downgrade a lib file as described in this thread:

[http://ubuntuforums.org/showthread.php?t=185033](http://ubuntuforums.org/showthread.php?t=185033)

---

