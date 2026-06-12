---
title: "Ubuntu started asking Administrator password"
date: 2016-03-03
forum: General Help
---

### Post by vladimir48 on 2016-03-03
Hi, all

Some time ago my system started asking Administrator password when I need to change system setting or install updates via GUI. 
The strange thing is, that this is not sudo password. For example I could easily run sudo apt update with my login password, but this GUI tells me 'Sorry, that didn't work. Try again'

I'm using UbuntuGnome 15.10

---

### Post by vladimir48 on 2016-03-03
Just in case someone will run into this: 
If your sudo password works from the command line and do not work from the GUI

sudo adduser $(whoami) sudo 

Seems to help.

---

