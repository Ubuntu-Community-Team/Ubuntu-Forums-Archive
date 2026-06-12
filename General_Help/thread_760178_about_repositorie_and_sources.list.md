---
title: "about repositorie and sources.list"
date: 2008-04-19
forum: General Help
---

### Post by Diabolis on 2008-04-19
I wanted to install emesene and since it appears only in hardy's repositories I added the following line to my sources.list file so I could install it with a simple apt-get install.
```
deb http://mx.archive.ubuntu.com/ubuntu/ hardy main universe
```

This made me wonder. What if I copy a whole sources.list file from hardy and use it in my gutsy installation.
Would typing **sudo apt-get upgrade** be equivalent to make the traditional upgrade from one version to the newer?

---

### Post by LaRoza on 2008-04-19
Please don't do that...

You can enable other repositories in Synaptic and Software Preferences.

---

### Post by Diabolis on 2008-04-19
Ha, I just checked synaptic and the line that I added(hardy's repo) appears as third party software.
As far as I know synaptic is just a gui, so its the same if I use it or if I modify directly my sources.list file. And I do prefer using the terminal and edit files.

So why this wouldn't be recommendable? Doesn't seem to be a harm to my computer, could it affect in some way the repositorie?

---

### Post by talikarng on 2008-04-20
When you use the "upgrade" option it will only upgrade the packages you currently have on your system; in your case from gutsy to hardy. This may result in some broken dependencies as gutsy packages will no longer be present as you have only selected the "main" branch and not "universe" and "non-free".
When upgrading from gutsy to hardy via apt-get or aptitude the option is dist-upgrade which is supposed to bring all packages you have up to the new versions (and may remove old uneeded ones)
(Check out the man pages for apt-get for more info)

If that wasn't confusing enough "apt-get/aptitude" are not the recommended ways of upgrading your distro to a newer version; in the last couple of years the recommended way of upgrading has been to use the gui update manager as some users have been left stranded after using apt-get/aptitude.

---

### Post by Diabolis on 2008-04-20
> What if I copy a whole sources.list file from hardy

That would even update the kernel...
Plus I have always upgraded to the newer version through apt-get with no problems.
I prefer the terminal over the gui.

---

