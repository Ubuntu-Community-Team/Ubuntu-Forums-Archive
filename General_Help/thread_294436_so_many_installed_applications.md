---
title: "so many installed applications"
date: 2006-11-06
forum: General Help
---

### Post by bschuteker on 2006-11-06
My question is this. With so many apps, or packages installed how do you find them. Most do not show up in the graphical menu's. You can start them in terminal if you know they are there and know the right command. Is there a list published somewhere that says what apps are installed, what they do and how to run them? It would also be nice if you could sort Synaptic by applications not all individual files and libraries. I would love to try out more things and keep the ones I like and ditch the ones I dont.

Thanks,

Bill

---

### Post by Najand on 2006-11-06
I am sure you have the search ability in Synaptic. In terminal you can search for packages using the command:
```

apt-cache search <SEARCH-PHRASE>

```
or
```

aptitude search <SEARCH-PHRASE>

```
and changing the <SEARCH-PHRASE> with your favorite keyword.

There is also another gui package manager in terminal (actually it is a part of aptitude.) You can use it using:
```

sudo aptitude

```
But getting used to it takes a little time and care.

---

### Post by philipgm on 2006-11-06
You could installDebian Menu using Automatix. This will give you all the applications available on your machine in a tree menu structure from the applications menu.

---

### Post by Najand on 2006-11-06
Hahahaha, the old Debian Menu....
Well, actually there is no need for installing it though (for sure not going to the  difficult process of installing Automatix), becuase it is already available. Just active it by 
1. ***RIGHT CLICK ***on ***APPLICATION***
2. Select ***EDIT MENUS***
3. After the new window opens, Check ***DEBIAN*** on the right screen
4. Click ***CLOSE***

---

### Post by philipgm on 2006-11-06
do you mean right click?

---

### Post by Najand on 2006-11-06
Sorry, yep, right click.

---

