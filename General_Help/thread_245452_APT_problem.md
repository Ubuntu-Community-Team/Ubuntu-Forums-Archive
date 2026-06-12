---
title: "APT problem"
date: 2006-08-27
forum: General Help
---

### Post by Anonii on 2006-08-27
This is a problem I'm having some times, when I'm trying to install something using APT.

> #
$ sudo apt-get install libqt3-mt-dev Reading package lists... Done
#
Building dependency tree... Done
#
Some packages could not be installed. This may mean that you have
#
requested an impossible situation or if you are using the unstable
#
distribution that some required packages have not yet been created
#
or been moved out of Incoming.
#
 
#
Since you only requested a single operation it is extremely likely that
#
the package is simply not installable and a bug report against
#
that package should be filed.
#
The following information may help to resolve the situation:
#
 
#
The following packages have unmet dependencies:
#
  libqt3-mt-dev: Depends: libqt3-mt (= 3:3.3.6-1ubuntu3) but 3:3.3.6-1ubuntu6 is to be installed
#
E: Broken packages

Any ideas, on how to fix this?
Tried to install libqt3-mt, and its already installed.
Also sudo apt-get -finstall , says that everything is installed.

---

### Post by Anonii on 2006-08-28
:/
Please, dont tell me its that serious...

---

### Post by Ramses de Norre on 2006-08-28
What's your sources.list like? And did you install third party packages?

---

