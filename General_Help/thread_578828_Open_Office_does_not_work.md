---
title: "Open Office does not work"
date: 2007-10-17
forum: General Help
---

### Post by tugh on 2007-10-17
This might (hopefully) be an easy fix since I had never had this problem before. About couple weeks ago the open office (spreadsheet, word processor, etc.) has stopped working, which means neither when I click on the shortcut under Applications>Office, nor when I double-click on an office file make the software open.  I removed and re-installed them through the synaptic mgr, but nothing has changed.
Any help would be greatly appreciated.

---

### Post by Billy the Kid on 2007-10-17
Do you receive an error message after running it from the terminal? ie Applications > Accessories > Terminal  type: openoffice

---

### Post by LanDan on 2007-10-18
i always get the same thing when i use the quickstarter 

try to open a terminal and type "oowriter" if it starts then there is no biggie

not sure if its the same for you but i always modify the /usr/share/applications/ desktop file and change it to look like this
Exec=oowriter %U

---

### Post by tugh on 2007-11-07
Ok, when I type "openoffice", it says it's not installed. when I try to install it (apt-get install openoffice.org-common), it says the newest version is already installed???
When I type oowriter, it says "/usr/bin/oowriter: 3: /usr/lib/openoffice/program/ooqstart: not found"
Any ideas?

---

### Post by tugh on 2007-12-16
Anybody?

---

