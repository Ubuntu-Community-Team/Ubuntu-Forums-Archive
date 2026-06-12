---
title: "Want to remove all GUI packages..."
date: 2007-07-17
forum: General Help
---

### Post by xavier_r on 2007-07-17
I want to build a UBUNTU stripped of all GUI programs... from my feisty installation...
I have installed it in VMWare Workstation, and I now want a command line environment...
No GUI...

I want to know which Packages should I remove so that the end result is a only command line UBUNTU...

For example: Synaptic must be removed but Aptitude will remain...
In this way all GUI apps...

---

### Post by Sef on 2007-07-17
You can start Ubuntu with just the command line.   At the log in screen, just go to options > (there is one to boot to the command line.)  > Then set it as the default.  Or just install it as a server from menu options for installing.

---

### Post by kevinlyfellow on 2007-07-17
```
sudo apt-get autoremove ubuntu-desktop
``` is a good place to start  I think that should at least get rid of gnome.

---

### Post by pointone on 2007-07-17
You'd be better off installing the server edition and starting from there.

---

### Post by kevinlyfellow on 2007-07-17
> **pointone said:**
> You'd be better off installing the server edition and starting from there.

Perhaps that would be best, it's going to take a lot of apt-get autoremoves...

I just thought of a way to get rid of a lot of programs
```
apt-get autoremove gnome*
```

---

### Post by pointone on 2007-07-17
Another idea would be to use the debfoster package. This tool will go through each package installed on your computer and give you options to keep, remove, remove completely, etc. A really nice tool for cleaning up or stripping down a system.

---

### Post by kevinlyfellow on 2007-07-17
> **pointone said:**
> Another idea would be to use the debfoster package. This tool will go through each package installed on your computer and give you options to keep, remove, remove completely, etc. A really nice tool for cleaning up or stripping down a system.

That's a nice tool.  But here's a suggestion: don't keep synaptic open when using it!  It finishes up unexpectedly and if synaptic's open, it will tell you there is a lock on the package manager and quit.  You will then need to start over... like I just did :-(

---

### Post by xavier_r on 2007-07-18
debfoster is good :)

---

