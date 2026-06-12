---
title: "[SOLVED] How do you install google earth?"
date: 2008-03-22
forum: General Help
---

### Post by m4mb4 24 on 2008-03-22
im running Ubunty 7.10 is there anyway to install google earth.. please help..thanks..

---

### Post by munkyeetr on 2008-03-22
> **m4mb4 24 said:**
> im running Ubunty 7.10 is there anyway to install google earth.. please help..thanks..
1) **System** => **Administration** =>** Synaptic Package Manager**
2) Click the **Search** button and search for "**google earth**"
3) Install it

**EDIT**: You may need to enable the medibuntu repository:
1) Open **Synaptic Package Manager** as above
2) **Settings** => **Repositories**
3) On the **Third-Party Software** tab check the **medibuntu** repository

---

### Post by m4mb4 24 on 2008-03-22
thanks!

---

### Post by forestpixie on 2008-03-22
Medibuntu isn't there by default. Do these seperately in a terminal 

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by munkyeetr on 2008-03-22
np :)

---

### Post by munkyeetr on 2008-03-22
> **forestpixie said:**
> Medibuntu isn't there by default.

Good call. I don't remember having to add it, but it appears to not be there with the default install.

---

### Post by forestpixie on 2008-03-22
Only remember myself cos I've just done hardy twice - installed pclinuxos over the top of the hardy install I did 3 days ago - which was a bit of a mistake :D

---

### Post by m4mb4 24 on 2008-03-22
ok.. i installed..where would google earth show up..?

---

### Post by munkyeetr on 2008-03-22
> **m4mb4 24 said:**
> ok.. i installed..where would google earth show up..?
**Applications** => **Internet** => **Google Earth**

---

### Post by m4mb4 24 on 2008-03-22
ok thanks

---

### Post by m4mb4 24 on 2008-03-22
sorry ..where do i unpack google earth... it wont show up in the internet menu...

---

### Post by forestpixie on 2008-03-22
you don'ty unpack it - have you actually installed it ?

```
sudo apt-get install googleearth
```

---

### Post by m4mb4 24 on 2008-03-22
it says i did in the package manager... but i dont see it on the internet...menu

---

### Post by forestpixie on 2008-03-22
right click the menu bar and edit menu - go to internet and see if it's there byt without a tick 
to check that you have installed it open aterminal and use googleearth as a command it should open

---

### Post by m4mb4 24 on 2008-03-22
its not there...right click edit menu not there..

---

### Post by m4mb4 24 on 2008-03-22
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

thats what i get when i try to update...

---

### Post by forestpixie on 2008-03-22
try running this in a terminal - not too sure if it's the right one but think so -  I don't use wine

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - &&sudo apt-get update
```

---

### Post by m4mb4 24 on 2008-03-22
ok thanks..its done

---

### Post by miki81 on 2008-03-26
Thanks !
Google Earth works perfect !

---

