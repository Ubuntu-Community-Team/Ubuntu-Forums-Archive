---
title: "Easiest way to delete software"
date: 2023-01-22
forum: General Help
---

### Post by ras00998 on 2023-01-22
Hello all, 

Ubuntu novice here - as will become clear. 

I am running - Ubuntu 22.04 Jammy Jellyfish (x86-64)

I used to run Debian on my older machine, and there was a package manager where you could easily delete unwanted software. 
Package manager is not coming up on a search of my system - 

I seem to have a program called 'snap store' - apparently for updating, removing, adding software. 
When I open snap store, and open installed' tab,  it does not display a full list of software?
There is software on my system which comes up in a search but does not appear in the snap store. 

Any tips? 
Was hoping to do this without using the command line, being a novice and all. 

Many thanks

---

### Post by gezzer2 on 2023-01-22
in the software store search for synaptic this should do as you require ...

---

### Post by guiverc on 2023-01-22
Debian & Ubuntu have many *package manager* choices, and they're almost identical.

Myself, my favorite is probably `aptitude` as it's run from command line; but offers a text-based interactive feature I find very useful.

GUI versions are `synaptic` for GTK desktops, and `muon` for Qt based desktops, but other options exist too.

As I'm using Debian currently; I searched for `software` and GNOME Software was offered; which is something I'd expect to see with Ubuntu (the Ubuntu *Snap Store *I believe is this modified to also offer *snap* packages so is more versatile); but I use neither & thus haven't explored.   If you're using a Qt desktop (GNOME is GTK), 'Discover' is the equivalent to Gnome Software/Snap Store.

Some DEsktops have other alternatives too, eg. I'm rather fond of Ubuntu MATE's *Software Boutique* too, it's far from complete; but it's a curated list of packages that attempts to offer *best in class* for the software it has, which can be a positive or negative as it has fewer options.

Debian & Ubuntu you'll find offer *almost *the same though.

---

### Post by monkeybrain20122 on 2023-01-22
> **ras00998 said:**
> Hello all, 


I seem to have a program called 'snap store' - apparently for updating, removing, adding software. 
When I open snap store, and open installed' tab,  it does not display a full list of software?
There is software on my system which comes up in a search but does not appear in the snap store. 



There are two kinds of packages in Ubuntu by default, the traditional .deb packages from the repositories which can be installed and removed via apt or synaptic or aptitude (the usual debian tools). There are other packages from snap (standalone, sandboxed packages) which are installed and removed through snap and the two systems are unconnected. 

So apt or synaptic won't work for these packages. If you open the software store for some packages you may find both a .deb and a snap version (I don't have a screenshot since I have removed all snap infrastructures)

Snap packages are bigger than the deb equivalent because they are packaged with all their dependencies. The advantage is that they get verson and feature updates regularly unlike the .debs which are frozen (unless you add a ppa) The disadvantage is that is that they take up more disk space and it used to slow down boot time because snap packages have to mount some subvolumes (?) at start up.  As said I have no snap installed so I don't know if it is still the case. (I installed flatpack which has all the advantages of snaps but has a unified gui to control what flatpak apps can access and doesn't impact on boot time) 

There used to be threads on these forums that the snap version of some multimedia apps didn't work correctly because the sandbox feature limited their access to some system resources and there were problems to install addons (e.g Gimp). I don't know if that is still the case.

So to manage the snap packages you can either do it through the software store gui or through command line

to list all snap packages

```
snap list
```

to remove

```
sudo snap remove <package name>


```

to install

```
sudo snap install <package name>
```

Note: I am not sure if sudo is needed, I found these on the web, I use flatpak, it doesn't require sudo to install and remove packages.

You can't remove the snap store this way, to do that you have to get rid of all snap infratstrures.

---

### Post by ras00998 on 2023-01-23
thank you :)

---

### Post by ras00998 on 2023-01-25
Many thanks for all this information :)

---

