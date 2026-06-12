---
title: "Package Manager Hangup"
date: 2006-11-30
forum: General Help
---

### Post by The-Wizard-of-the-Lake on 2006-11-30
Tried to download google earth from The Penquin Liberation Front, download got to the loading point then it just hung there. Now I've lost use of Synaptic Package Manager and Add/Remove function of Applications. System: Amd 64, Abit Kn8 Sli mainboard,  Asus PCI GF6600](*,) Any ideas?

---

### Post by Dr. Nick on 2006-11-30
try and use apt-get from the command line, use

sudo apt-get *package name*

using the terminal gives better error messages then synaptic which may help fix it easier

---

### Post by The-Wizard-of-the-Lake on 2006-12-01
I've tried apt-get install -f and apt-get googleearth; Nothing happening with either command in terminal.  But thanks anyway.

---

### Post by The-Wizard-of-the-Lake on 2006-12-01
I keep getting unable to lock administration directory and unable to lock file.

---

### Post by Dr. Nick on 2006-12-01
make sure synaptic is closed before trying it,

also try 
sudo apt-get install googleearth

looks like you forgot the install part, if it cant find google earth then just pick any package and it will give you a error most likely

---

