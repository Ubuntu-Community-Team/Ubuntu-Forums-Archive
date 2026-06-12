---
title: "[SOLVED]LibreOffice Base is not in the installation of Lubuntu 18.10 (Desktop 32 bit)"
date: 2018-11-27
forum: General Help
---

### Post by ubtnk on 2018-11-27
I've installed Lubuntu 18.10 (Desktop 32 bit) on Compaq Presario V3000( Intel Core 2 Duo+RAM 2 GB+11 year-old) notebook.

Why is LibreOffice Base missing ?

If I have to install by myself, what should I do ?

[ATTACH=CONFIG]281789[/ATTACH]

---

### Post by deadflowr on 2018-11-27
Base is never pre-installed. (Or at least I have not seen it installed on any flavor of Ubuntu ever)
You have to install that yourself.
Open a terminal and run
```
sudo apt update
sudo apt install libreoffice-base
```

Or if you have a gui package manager installed such as synaptic do a search for the libreoffice-base package.
I think Ubuntu Software can search for just the word *base* and it should show up there in the search results.

---

### Post by ubtnk on 2018-11-27
Thank you so much for your help.

---

