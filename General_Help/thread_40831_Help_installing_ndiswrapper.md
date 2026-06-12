---
title: "Help installing ndiswrapper"
date: 2005-06-10
forum: General Help
---

### Post by FizDev on 2005-06-10
[I]Hi,
I'm trying to install ndiswrapper with apt-get but I get the following error
E: Couldn't find package ndiswrapper
Don't understand why, I have universe in my sources.list....
I also did and apt-get update... still won't find ndiswrapper
Could someone help me?[/I]

Sorry, just saw what was the problem...

---

### Post by Kyral on 2005-06-10
I did a quick look on the Ndiswrapper site and it said to add this line to the sources.list to apt-get it

```
deb http://ndiswrapper.sourceforge.net/debian ./
``` 

then do the normal sudo apt-get update

---

### Post by az on 2005-06-10
Ndiswrapper is alread on the install cd.  the module is included in the kernel you are running and the utility is in the package called ndiswrapper-utils.

---

