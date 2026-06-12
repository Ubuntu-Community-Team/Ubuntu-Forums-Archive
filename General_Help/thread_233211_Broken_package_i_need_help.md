---
title: "Broken package? i need help"
date: 2006-08-09
forum: General Help
---

### Post by Bumblescrump on 2006-08-09
Everytime I try to get libsdl1.2-dev  I get this:

ricky@ricky-desktop:~$ sudo apt-get install libsdl1.2-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages



anyone have any ideas?  I'm trying to get mednafen to work!:confused:

---

### Post by wieman01 on 2006-08-09
Synaptic has a section (left-hand side) "broken packages" where you should be able to remove it. That done the error message should disappear.

---

### Post by RAOF on 2006-08-09
Post your /etc/apt/sources.list.  You probably don't have one of the required repositories enabled, so apt can't find a package to resolve the dependency.

---

