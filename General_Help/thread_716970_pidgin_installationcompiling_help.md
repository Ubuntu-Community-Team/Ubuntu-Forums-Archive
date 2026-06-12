---
title: "pidgin installation/compiling help"
date: 2008-03-06
forum: General Help
---

### Post by darkthunderfx on 2008-03-06
i want to upgrade my pidgin to 2.4.
(i'm new to kubuntu)
I read [http://ubuntuforums.org/showthread.php?p=4431162](http://ubuntuforums.org/showthread.php?p=4431162) where it says to dl the source and compile.

however, there is obviously a step missing. i know i cannot just dl the source on my desktop and type ./configure in terminal and expect anything. so, what do i need to do?

sorry for the stupidity ><

---

### Post by notwen on 2008-03-06
If you want to avoid CLI and compiling from source, use the deb file linked at the bottom of the first post. 

You will need 3 .deb files:
[pidgin-data]("http://getdeb.net/download/2259/1")
[libpurple]("http://getdeb.net/download/2259/2")
[pidgin]("http://getdeb.net/download/2259/0")

The first 2 packages are needed in order to install/run Pidgin.  .deb files are similar to .exe files for Windows.  Double-click, click 'Install' in the top right and let it install said package.  You can then remove them via Synaptic.  Post back if you do wish to compile from source.  =]

---

### Post by Oldsoldier2003 on 2008-03-06
> **darkthunderfx said:**
> i want to upgrade my pidgin to 2.4.
(i'm new to kubuntu)
I read [http://ubuntuforums.org/showthread.php?p=4431162](http://ubuntuforums.org/showthread.php?p=4431162) where it says to dl the source and compile.

however, there is obviously a step missing. i know i cannot just dl the source on my desktop and type ./configure in terminal and expect anything. so, what do i need to do?

sorry for the stupidity ><
you can download the binaries as suggested above, or you can compile pidgin from source. the tutorial is exactly step by step and works if you follow the directions, line by line.

---

### Post by notwen on 2008-03-06
If you wish to compile the source code, download it and extract it to your Desktop or home folder, where ever you prefer.  Open up a terminal and change to the directory you extracted the Pidgin source to and run the commands give in the other thread:

```
./configure
make
sudo make install
```

---

### Post by Oldsoldier2003 on 2008-03-06
> **notwen said:**
> If you wish to compile the source code, download it and extract it to your Desktop or home folder, where ever you prefer.  Open up a terminal and change to the directory you extracted the Pidgin source to and run the commands give in the other thread:

```
./configure
make
sudo make install
```
i prefer checkinstall makes it easier to uninstall later on...

---

### Post by kevdog on 2008-03-06
Everybody always states that checkinstall is easier to uninstall, however what is wrong with the plain old sudo make uninstall??  That uninstalls the program also, just not in the package management system.

---

