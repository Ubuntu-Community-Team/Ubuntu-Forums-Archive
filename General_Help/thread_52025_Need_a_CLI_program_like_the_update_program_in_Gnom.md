---
title: "Need a CLI program like the update program in Gnome"
date: 2005-07-26
forum: General Help
---

### Post by lozzd on 2005-07-26
Hello,

I'm running a Ubuntu webserver remotely. Before, I could upgrade packages using the upgrade manager (the funny red exclamation mark) where I could stop it from installing the linux-headers package, as that scares me too much. However, I would like to select the other packages to update. Is there such a program/way to do it in a standard remote terminal? 
I read the manual of apt-get, etc, and couldn't work out if it was possible.

Thanks

Laurie

---

### Post by rmjokers on 2005-07-26
The gui application you were using to update is synaptic, which is just a front end to APT.  You can and should use apt to update from the command line.  The most common commands are:

sudo apt-get update

Gets all updated info from repositories.

sudo apt-get upgrade

Upgrades all available packages

---

### Post by lozzd on 2005-07-26
Sorry, let me explain, I DO NOT want to install SOME of the packages that need upgrading. 
I need some way of de-selecting some packages for upgrading. 

Thanks

Laurie

---

### Post by charlieg on 2005-07-26
Still, apt-get should be able to do it for you.  Just 'man apt-get' to get an overview of the options.

I would look at the man page for you but my Ubuntu machine is in another room atm and my legs feel heavy. ;)

---

### Post by heimo on 2005-07-26
If you have static list of packages not to upgrade, you could put them in apt.conf hold-section. I haven't used it, don't know if this is good solution. It's also possible that dselect (which is in my mind very confusing piece of software) could do what you want.

---

### Post by lozzd on 2005-07-26
Thanks for all your suggestions, in the end I found "aptitude" and used that instead and all is well.

Thanks very much!

---

### Post by az on 2005-07-26
sudo dselect update
sudo dselect



Dselect is a cousin of aptitude which will update you list and mark packages for update.  You can then go in and "de-selct" unwanted packages.  Then you make it go.

---

