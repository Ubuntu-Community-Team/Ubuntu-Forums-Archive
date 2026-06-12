---
title: "T or F: Ubuntu can be stripped down to a kernel and a shell"
date: 2005-05-18
forum: General Help
---

### Post by snairofilac on 2005-05-18
True or False:

Starting with a default Ubuntu installation:

If enough packages are uninstalled, Ubuntu can be transformed into a box that boots to a simple bash prompt with a narrow, definable set of commands.

---

### Post by Burgundavia on 2005-05-18
Absolutely, just like any linux install.

Corey

---

### Post by UbuWu on 2005-05-18
It is also possible to do a base install (don't ask me how), which will give you exactly that. No need to uninstall anything.

---

### Post by snairofilac on 2005-05-18
wow that's good to hear.

what's the best resources to learn how to do just that, leaving only bash, the smallest desktop environment, possibly synaptic or apt.

want to build from zero vs. other way around.

---

### Post by snairofilac on 2005-05-18
if i just go on an uninstalling  bonanza (with respect only to prompted dependencies) will i run into problems?

are there boot scripts i must edit to tell ubuntu to load just the needed drivers on my computer and a bash script?

please point to the best resources you have found regarding above

---

### Post by fng on 2005-05-18
[QUOTE=UbuWu]It is also possible to do a base install (don't ask me how), which will give you exactly that. No need to uninstall anything.[/QUOTE]

Insert the install cd
The cd boots
At the prompt typ "custom" or "server" (can't remember which 1) instead of just pressing enter
The custom base-install begins

---

### Post by snairofilac on 2005-05-18
that's what i'm talkin bout

thanks

---

### Post by az on 2005-05-18
"are there boot scripts i must edit to tell ubuntu to load just the needed drivers on my computer and a bash script"

If you remove packages, all that is taken care of for you.


The server install (Hoary) gives you a faily base system with a lot of tools.  The next release of Ubuntu (breezy) will have a changed definition of a base system.  Basically, you get a kernel, a bootloader and apt.  You will need to install anything else by yourself.  I do not know if there is the equivalent of the Hoary base system available for installation by a metapackage.  So that would give you three levels:  Absolute minimum, base system and ubuntu-desktop system.

---

### Post by snairofilac on 2005-05-18
nice.

is there a way to get a list of all packages available via apt and have it available post-base install?

---

### Post by az on 2005-05-18
Aptitude does what synaptic does, just in a console as opposed to a graphical window.  From the Hoary base system install do

sudo aptitude


You can also use the host of command line tools
apt-cache search 


man apt
man dpkg

---

### Post by fng on 2005-05-18
are you can search in apt with the command (loose the quotes): ```
apt-cache search 'searchsting'
```

---

### Post by poofyhairguy on 2005-05-19
No offense, but anyone that knows what a kernel is (and more importantly wants a stripped down OS) does not belong in the beginer forums. Sorry the forum was not clear before today.

---

