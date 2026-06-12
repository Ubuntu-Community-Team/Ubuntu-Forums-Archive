---
title: "PCManFM can't open PDF with double click"
date: 2013-10-27
forum: General Help
---

### Post by ubunet on 2013-10-27
Hi,

My Lubuntu 13.04 x32 can't open PDF when I double click a pdf file in PCManFM, but Evince works in LXTerminal or if started in menu and I open the file in the program.

---

### Post by Dennis N on 2013-10-27
Right click on a pdf and check the properties for : **open with > document viewer**

---

### Post by ubunet on 2013-10-27
> **Dennis N said:**
> Right click on a pdf and check the properties for : **open with > document viewer**

Doesn't work.

---

### Post by Dennis N on 2013-10-27
Be sure you are not using "open with" that you see on the first right click. Instead, select "properties" then "open with". then "document viewer". This will set the default application to open that file type with doulble clicking.

---

### Post by ubunet on 2013-10-27
> **Dennis N said:**
> Be sure you are not using "open with" that you see on the first right click. Instead, select "properties" then "open with". then "document viewer". This will set the default application to open that file type with doulble clicking.

Does'nt work.

---

### Post by ubunet on 2013-10-27
**I solved.** The PCManFM has a bug. It can't find the executable of evince. I needed to write the complete path to it (/usr/bin/evince %U). 

Thank you for your help!

---

