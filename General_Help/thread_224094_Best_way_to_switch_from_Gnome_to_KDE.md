---
title: "Best way to switch from Gnome to KDE?"
date: 2006-07-27
forum: General Help
---

### Post by xenomorph99 on 2006-07-27
Hi,

I've been using Gnome on my desktop and KDE on a laptop and have decided that I prefer KDE...so I'm afraid Gnome will have to go.

What is the best way to 'swap' over bearing in mind that I don't just want to install KDE to co-exist with Gnome....

When I installed Ubuntu, I used seperate partitions for / and /home so can I simply install Kubuntu over Ubuntu and re-use the partitions (i.e. after gparted, choose to reformat the / mount but not the /home)? 

Or, is it easier to simply download KDE via synaptic then get 'deinstall' Gnome?

I'd prefer to do the latter as I've already downloaded quite a few MB of updates etc but fear that it will all go pear shaped.

Ta,
Xeno

---

### Post by gingermark on 2006-07-27
I'll be honest and say a clean KDE install is probably better.

If you want to install KDE, and then remove GNOME, [this](http://www.ubuntuforums.org/showthread.php?t=96046) might help with the GNOME removal, although make sure you don't remove Grk apps you still want to use in KDE.

---

### Post by aysiu on 2006-07-27
I'm with gingermark--a clean install is the best way to go.

To deinstall Gnome, you can try this:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by xenomorph99 on 2006-07-27
OK, thanks.

When you say 'clean install', do you mean installing to '/' whilst leaving /home as it is or a CLEAN install where I reformat everything?

Ta,
Xeno

---

### Post by aysiu on 2006-07-27
> **xenomorph99 said:**
> OK, thanks.

When you say 'clean install', do you mean installing to '/' whilst leaving /home as it is or a CLEAN install where I reformat everything?

Ta,
Xeno
Installing to / Kubuntu only and then leaving /home alone (assuming /home is on a separate partition--as this is the only way you could do it).

---

### Post by xenomorph99 on 2006-07-27
OK, cheers chaps. Roger Wilco etc.

Ta,
Xeno

---

### Post by Zelut on 2006-07-27
leaving /home alone is going to leave a bunch of gnome specific .hidden config files will it not?  I guess I don't know a great way to clean those out other than manually.

Just for education sake, why is a clean install better than 'aptitude install kubuntu-desktop' followed by 'aptitude remove ubuntu-desktop'?

---

### Post by aysiu on 2006-07-27
> **kuyaedz said:**
> leaving /home alone is going to leave a bunch of gnome specific .hidden config files will it not?  I guess I don't know a great way to clean those out other than manually.

Just for education sake, why is a clean install better than 'aptitude install kubuntu-desktop' followed by 'aptitude remove ubuntu-desktop'?
But if you don't have Gnome installed, then those Gnome-specific hidden config files won't be used. Even if you were able to install Kubuntu and then uninstall Ubuntu, then your Gnome-specific config files would still remain.

Also, *aptitude* works properly only if you _installed_ using *aptitude*. Since you didn't install *ubuntu-desktop* with *aptitude*, you won't be able to remove it fully with that command.

If you want a command to remove it, try this:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

If you want to remove the Gnome configuration files after you remove Gnome: ```
rm -rf ~/.gnome2
rm -rf ~/.gnome
rm -rf ~/.gconf
rm -rf ~/.gconfd
rm -rf ~/.nautilus
rm -rf ~/.metacity
``` But I don't think those config files will interfere with your KDE experience.

---

### Post by xenomorph99 on 2006-07-27
Just a quick question. If I switch to KDE, can I use EasyUbuntu etc to restore MP3 DVD playback etc?

I suppose one way to do this would be to install Ubuntu server then just add the desktop(s) of your choice + the basic items. Then you can swap and change at your leisure using apt(?)

Ta,
Xeno

---

### Post by aysiu on 2006-07-27
> **xenomorph99 said:**
> Just a quick question. If I switch to KDE, can I use EasyUbuntu etc to restore MP3 DVD playback etc?

I suppose one way to do this would be to install Ubuntu server then just add the desktop(s) of your choice + the basic items. Then you can swap and change at your leisure using apt(?)

Ta,
Xeno
According to [the website](http://easyubuntu.freecontrib.org/overview.html): > Runs on Ubuntu, Kubuntu and Xubuntu without installing additional software.

---

### Post by xenomorph99 on 2006-07-27
Cheers and sorry for being lazy - I should have checked the site out myself.

Ta,
Xeno

---

