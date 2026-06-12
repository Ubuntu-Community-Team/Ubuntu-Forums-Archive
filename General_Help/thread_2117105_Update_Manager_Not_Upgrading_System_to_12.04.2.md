---
title: "Update Manager Not Upgrading System to 12.04.2"
date: 2013-02-17
forum: General Help
---

### Post by mfucci on 2013-02-17
Hello,

I have two laptops running Precise. I successfully upgraded one from 12.04.1 to 12.04.2 through Update Manager this morning. The other one is not being given the option for some reason. Are upgrades like these rolled out slowly or is there a possibly that some setting is preventing the upgrade? Thanks in advance.

---

### Post by philinux on 2013-02-17
On the laptop in question. Open a terminal. 

sudo apt-get update && sudo apt-get upgrade

Once done you'll have 12.04.2

---

### Post by mfucci on 2013-02-17
> **philinux said:**
> On the laptop in question. Open a terminal. 

sudo apt-get update && sudo apt-get upgrade

Once done you'll have 12.04.2

Thanks, but unfortunately that did not work :( Any other ideas?

---

### Post by mfucci on 2013-02-17
Nevermind, figured it out. Had to change some settings in Software Sources --> Install Updates From.

---

