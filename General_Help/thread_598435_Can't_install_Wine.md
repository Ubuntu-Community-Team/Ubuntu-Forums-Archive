---
title: "Can't install Wine"
date: 2007-10-31
forum: General Help
---

### Post by earlgray on 2007-10-31
I've tried installing wine in the following ways:
1. sud apt=get install wine.    This did not work
2. wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine   -   This did not work either. After typing it into the termanil it appeared that it worked but when I went into Synaptice Package Manager and marked the Wine utilities I got the message "Wine depend Lib Audio 2 but it is not installable"
?

---

### Post by Maestro23 on 2007-10-31
Do you have all your Sources enabled?

System>>Admin>>Software Sources.

Universe/Multiverse, Third-Party, etc...

---

### Post by earlgray on 2007-10-31
Enabling the sources fixed the problem. Wine now works and my brokers software installed with no problems.
Thanks

---

### Post by Maestro23 on 2007-10-31
> **earlgray said:**
> Enabling the sources fixed the problem. Wine now works and my brokers software installed with no problems.
Thanks

Glad to hear it man.  Please mark this SOLVED thru the Thread Tools.

Thanks.:)

---

