---
title: "Upgrades for programs installed from synaptic"
date: 2007-08-03
forum: General Help
---

### Post by tc101 on 2007-08-03
If I install a program using synaptic package manager or "Applications/add remove", are upgrades to those programs automatically installed when I run Update Manager and tell it to install all updates?

If not, how do I update these programs?

---

### Post by blingboi on 2007-08-03
i think you can do 

sudo apt-get update program

in the terminal

---

### Post by forestpixie on 2007-08-03
I'm sure update manager does it - at least it has for programs I've installed

if you want to upgrade your programs you can do 

```
sudo apt-get upgrade
```

in a terminal, 

```
sudo apt-get update
```

is used to update your sources.list

---

### Post by floke on 2007-08-03
You need to run the above commands in the reverse order
eg 'sudo apt-get update && sudo apt-get upgrade'
Else - open synaptic and click the 'upgrade' button - then apply
Otherwise - wait for the 'updates available' alert!

---

### Post by tc101 on 2007-08-03
So are you saying that if I just wait for the updates available alert and then do all the updates using Update Manager, I should get all updates for everything installed with synaptic?

---

