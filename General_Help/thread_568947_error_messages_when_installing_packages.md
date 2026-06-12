---
title: "error messages when installing packages"
date: 2007-10-06
forum: General Help
---

### Post by bengoerzen712 on 2007-10-06
i find that every time i try to install a package, either through the terminal, synaptic or when i even download a package that will install itself, it comes up with some kinda of error message, either a dependancy issue or it just was not able to download certain files 
any help would be appreciated as i really like how linux works either than this issue

---

### Post by taurus on 2007-10-06
It would be nice if you could include the whole error message.  Otherwise, nobody knows what's wrong with it.

What are the outputs of these commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by bengoerzen712 on 2007-10-08
here is the error message if i try to install ubuntu-restricted-extras from the terminal;

The following packages have unmet dependencies:
  ubuntu-restricted-extras: Depends: gstreamer0.10-plugins-ugly but it is not going to be installed
                            Depends: sun-java6-plugin but it is not going to be installed
E: Broken packages

and when i try to install actual programs (ie xmms)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

i do not understand how the second one could noy be available as i have already downloaded the package

any help would once again be appreciated

---

### Post by zvacet on 2007-10-08
**synaptic>edit>fix broken packages**

---

### Post by bengoerzen712 on 2007-10-08
Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

i do not understand what this means
it just says switch to it, it does not tell me what to do

---

