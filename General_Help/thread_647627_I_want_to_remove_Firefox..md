---
title: "I want to remove Firefox."
date: 2007-12-22
forum: General Help
---

### Post by beatme101 on 2007-12-22
Hello everyone. I am interested in switching to Linux some time in the future, and I'll probably be testing it out sooner than that on another computer, but one of the things that has been keeping me away from that is Firefox. From what I hear there is no way to remove Firefox without removing several components of the operating system -- one of which, I first heard was the desktop, but then I learned it's something else, possibly more important: A "meta package", supposedly required to be able to update the operating system.

Firefox has become the Internet Explorer of Linux, integrated with the operating system in a way that you cannot remove it without disabling key functions of the system. What were they smoking when they did this? Seriously! I don't want Firefox, anything else would be better, if someone has a way to get rid of Firefox without getting rid of the ability to update the system, I'd love to hear it.


I'm a fairly new user to the whole world of Linux so I don't know any command line stuff or even how to get to the command line, if that will be a requirement in my quest to have a crapware-free Linux experience.

---

### Post by santiagoward2000 on 2007-12-22
> **beatme101 said:**
> Hello everyone. I am interested in switching to Linux some time in the future, and I'll probably be testing it out sooner than that on another computer, but one of the things that has been keeping me away from that is Firefox. From what I hear there is no way to remove Firefox without removing several components of the operating system -- one of which, I first heard was the desktop, but then I learned it's something else, possibly more important: A "meta package", supposedly required to be able to update the operating system.

Firefox has become the Internet Explorer of Linux, integrated with the operating system in a way that you cannot remove it without disabling key functions of the system. What were they smoking when they did this? Seriously! I don't want Firefox, anything else would be better, if someone has a way to get rid of Firefox without getting rid of the ability to update the system, I'd love to hear it.


I'm a fairly new user to the whole world of Linux so I don't know any command line stuff or even how to get to the command line, if that will be a requirement in my quest to have a crapware-free Linux experience.

Hi and welcome!
No, there's no problem removing Firefox. There are some distros that don't even come with Firefox pre-installed, like Kubuntu for example.
If you want to use Ubuntu, you can just go to Synaptic, remove Firefox and try to install something else, like Epiphany, Opera, etc.

---

### Post by jfinkels on 2007-12-22
It is possible to remove firefox. The only situation in which removing the ubuntu-desktop meta-package *might* present a problem would be when doing a dist-upgrade (an upgrade to the next version of Ubuntu; even then, it probably won't cause any problem you'd need to fret over).

Try out Ubuntu on the Live CD if you are not ready to install it.

---

### Post by jespdj on 2007-12-22
If you remove Firefox, for example with
```
sudo apt-get remove firefox
```
then it might tell you that it's going to remove the pacakge **ubuntu-desktop** as well. But that does NOT mean that it is going to remove part of the operating system.

The package **ubuntu-desktop** is a "meta-package", i.e. it is a package that doesn't contain anything; it only depends on a lot of other packages. The idea with this is that by installing ubuntu-desktop, you can install all those other packages in one go.

ubuntu-desktop also depends on firefox, and so removing firefox also removes the ubuntu-desktop meta-package. But that doesn't mean that all the other packages that ubuntu-desktop depends on are also removed.

So, you can safely remove FIrefox without any other ill effects.

---

### Post by PeterJS on 2007-12-22
> **beatme101 said:**
>  A "meta package", supposedly required to be able to update the operating system.


Yes and no. Firefox is a dependancy of the Ubuntu Desktop Metapackage. But meta packages aren't critical in fact they don't do anything, all a meta package does is specify a bunch of related dependencies. The point of this is so you can bundle an entire suite of packages under one name.

All that will happen if you remove the ubuntu desktop meta package is that it will mark a bunch of the desktop components as candidates for auto removal clean up. Just don't run clean up right then, mark them all as manually installed, and go  on your merry way firefox free.

---

### Post by beatme101 on 2007-12-22
> **jespdj said:**
> If you remove Firefox, for example with
```
sudo apt-get remove firefox
```
then it might tell you that it's going to remove the pacakge **ubuntu-desktop** as well. But that does NOT mean that it is going to remove part of the operating system.

The package **ubuntu-desktop** is a "meta-package", i.e. it is a package that doesn't contain anything; it only depends on a lot of other packages. The idea with this is that by installing ubuntu-desktop, you can install all those other packages in one go.

ubuntu-desktop also depends on firefox, and so removing firefox also removes the ubuntu-desktop meta-package. But that doesn't mean that all the other packages that ubuntu-desktop depends on are also removed.

So, you can safely remove FIrefox without any other ill effects.

So then, does that mean that I will not be able to update whatever else is related to ubuntu-desktop? Or does it mean that whenever I update, I will have Firefox forced upon me again? Or is ubuntu-desktop not related to updates, and it's just for the initial installation? Or.. Something else?

---

### Post by PeterJS on 2007-12-22
> **beatme101 said:**
> So then, does that mean that I will not be able to update whatever else is related to ubuntu-desktop? Or does it mean that whenever I update, I will have Firefox forced upon me again? Or is ubuntu-desktop not related to updates, and it's just for the initial installation? Or.. Something else?


Meta packages have nothing to do with updating, they're only used for the initial install. Once things are installed each individual packages tracks the need to update it self. And since the ubuntu-desktop meta package has been removed it won't be updated, and won't try to reinstall it's dependencies.

---

### Post by beatme101 on 2007-12-22
Ah. Thanks everyone, I feel better about the safety of removing Firefox now. :)

---

### Post by Clintonostra on 2007-12-25
When you try to remove Firefox it will remove Epiphany, Yelp,etc.
Installing Epiphany will also install Firefox.

---

