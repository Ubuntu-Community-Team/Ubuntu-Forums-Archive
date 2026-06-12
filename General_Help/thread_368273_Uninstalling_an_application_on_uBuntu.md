---
title: "Uninstalling an application on uBuntu"
date: 2007-02-23
forum: General Help
---

### Post by warlock_handler on 2007-02-23
Hi guys,

background: linux newbie


ok guys if I install an new aplpication in uBuntu using the synaptic package manager then if I want to remove it all I need to do is select that application and right-click and remove...
however if I have like a source code so I compile and install it in this way:
1) ./configure
2) make install

how do I remove or uninstall these kinda applications in uBuntu...  I am using Breezy

thnx guys

---

### Post by louis_nichols on 2007-02-23
Usually, that is done by going back to the folder where you ran ./configure and executing

```
sudo make uninstall
```

However, this doesn't always work, bcause not all make scripts are done to have the option. So it's very application dependant. My recommendation is to use checkinstall. This is a package you'll find in synaptic. You install it and then, after running ./configure and make, instead of using

```
sudo make install
```

you use

```
sudo checkinstall
```

this will build a deb package and install it. You can later remove that package from synaptic, as all others.

---

### Post by warlock_handler on 2007-02-23
> **louis_nichols said:**
> Usually, that is done by going back to the folder where you ran ./configure and executing

```
sudo make uninstall
```

However, this doesn't always work, bcause not all make scripts are done to have the option. So it's very application dependant. My recommendation is to use checkinstall. This is a package you'll find in synaptic. You install it and then, after running ./configure and make, instead of using

```
sudo make install
```

you use

```
sudo checkinstall
```

this will build a deb package and install it. You can later remove that package from synaptic, as all others.


ok thats a cool tips.. i'll do that first thing tonight.. as i get access to my PC...  
thnx a million dude..

---

