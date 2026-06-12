---
title: "Broken Dependencies, again..."
date: 2008-01-07
forum: General Help
---

### Post by Dojan5 on 2008-01-07
This time i tried to install libgtk2.0-0 or something...
But, it seem to be a broken dependency.
Well, anyways, i cant reinstall it through synaptic
```
sudo synaptic
```
Synaptic opens up and when re-installing the broken dependency a error comes up:
> E: Kunde inte korrigera problemen, du har hållt tillbaka trasiga paket.
E: Unable to lock the download directory
Sorry for the swedish, it says
> E: Couldnt correct the problems, you have held back broken packages.
E: Unable to lock the download directory

Should i run ```
sudo apt-get install -f
```
instead?
Last time i ran it i kinda messed things up...
Will all the programs that are removed reinstall again, like GNOME-core and so on???
Thanks
/
Joel

---

### Post by Dojan5 on 2008-01-07
Okay, ill run sudo apt-get install -f and if GNOME dont reinstall ill just run :
```
sudo aptitude install gnome-desktop-environment
``` like LoKe siad i should do last time i messed with sudo apt-get install -f
Well, ill post here if any trouble comes up...
Cya

---

### Post by Dojan5 on 2008-01-07
DONE!
Everything went fine...
Didnt seem to need any help at all... Well, thanks anyway and i hope that if anyone get same problem they can solve it the same way...

---

