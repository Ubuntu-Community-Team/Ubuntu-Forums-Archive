---
title: "GIMP X11 Cursor Plugin???"
date: 2012-12-24
forum: General Help
---

### Post by ohnonot on 2012-12-24
Hello,
i read it's possible to import, edit and create xcursor themes with the gimp.
I also read it's included in 2.8 (which i'm using now) but i can't find it anywhere!
i also tried downloading & installing it from [here]("http://gimpstuff.org/content/show.php/GIMP-XMC+X11+cursor+plugin+for+amd64?content=95308&PHPSESSID=oaarumzs"), and get this message:
```
dpkg: error processing 95308-gimp-xmc_2.0.4-0ubuntu1_amd64.deb (--install):
 trying to overwrite '/usr/lib/gimp/2.0/plug-ins/file-xmc', which is also in package gimp 2.8.2-2
```can someone help, please? thanks.

ps: my system *is* 64bit.

---

### Post by raja.genupula on 2012-12-24
```
dpkg -r 95308-gimp-xmc_2.0.4-0ubuntu1_amd64.deb

sudo apt-get update

sudo  apt-get install -f
```

---

### Post by ohnonot on 2012-12-27
thanks!
this is what i get:```
sudo dpkg -r 95308-gimp-xmc_2.0.4-0ubuntu1_amd64.deb
[sudo] password for me: 
dpkg: error: you must specify packages by their own names, 
not by quoting the names of the files they come in

me@computer:~$ sudo dpkg -r gimp-xmc
dpkg: warning: ignoring request to remove gimp-xmc which isn't installed
me@computer:~$ sudo dpkg -r file-xmc
dpkg: warning: ignoring request to remove file-xmc which isn't installed
```also i can't find it in synaptic nor anywhere else.

afaik, it's part of the default gimp installation.

it seems to be a plugin to open x11 cursor files.

i was thinking of a more complete solution that allows me to easily open, modify and save complete cursor themes.

unless i'm missing something really obvious in gimp.
also "file-xmc" does not show up in the plugin browser. 
:-k

---

### Post by raja.genupula on 2012-12-27
ok do this 

```
sudo -i
apt-get autoclean
apt-get autoremove
apt-get update
```
then try again .

---

### Post by ohnonot on 2012-12-28
nope, still the same as in post #1.
i guess there's no magic cursor-theme-create-plugin after all, just a plugin to import graphics from cursor files....

wasn't there a standalone prog?
gursorcreate or sth? if so, it's not in the repos...

---

