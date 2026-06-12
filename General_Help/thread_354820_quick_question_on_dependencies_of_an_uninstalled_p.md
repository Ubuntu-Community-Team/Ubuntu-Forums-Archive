---
title: "quick question on dependencies of an uninstalled program.."
date: 2007-02-06
forum: General Help
---

### Post by spotdog14 on 2007-02-06
I manually installed Tomboy on my Edgy Ubuntu install, and it didnt work right and i wanted to uninstall it and reinstall it via the ad/remove application, but when i got to uninstall it in the ad/remove programs app it says that it has dependencies, so i go into the synaptic package manager to see what they are and it turns out that "ubuntu-desktop" is a depend. And it wants me to mark "ubuntu-desktop" to be removed in order to remove Tomboy. 

My question is what do i do? Do i uninstall Tomboy and ubuntu-desktop, then just reinstall both of them? 

Thanks for the help, i have only been on Ubuntu for about a month and a half now. Im running it on an Asus S5n laptop and its great! Keep up the great work guys!

---

### Post by Ramses de Norre on 2007-02-06
Ubuntu-desktop is a metapackage without any real content but with all standard ubuntu apps as dependency (and thus also tomboy). So if you install a ubuntu system, ubuntu-dekstop gets installed and all other apps are installed automatically as dependency.
There is no harm when deleting ubuntu-desktop though, all other apps will remain installed.

---

### Post by lhtown on 2007-02-06
You can safely remove ubuntu-desktop from your system. It is just a meta-package that tells the system which programs it should have installed. The only thing it will affect is your upgrade process to a new version (it is highly recommended to have installed for that).

The simple and painless solution to your problem is to go ahead and remove Tomboy and let it remove ubuntu-desktop and then reinstall ubuntu-desktop whereupon it will install all of the necessary dependencies of which, I seem to recall that Tomboy is indeed one.

If you start removing too many critical dependencies, especially from Ubuntu-base, you could leave your system unbootable or unable to run a desktop environment. (your data would be unaffected)  If you ever must do something like that, make sure to back everything up first and then reinstall the appropriate meta-packages like ubuntu-base or ubuntu-desktop before you do anythig else especially including rebooting.

---

### Post by spotdog14 on 2007-02-06
> **Ramses de Norre said:**
> Ubuntu-desktop is a metapackage without any real content but with all standard ubuntu apps as dependency (and thus also tomboy). So if you install a ubuntu system, ubuntu-dekstop gets installed and all other apps are installed automatically as dependency.
There is no harm when deleting ubuntu-desktop though, all other apps will remain installed.

> **lhtown said:**
> You can safely remove ubuntu-desktop from your system. It is just a meta-package that tells the system which programs it should have installed. The only thing it will affect is your upgrade process to a new version (it is highly recommended to have installed for that).

The simple and painless solution to your problem is to go ahead and remove Tomboy and let it remove ubuntu-desktop and then reinstall ubuntu-desktop whereupon it will install all of the necessary dependencies of which, I seem to recall that Tomboy is indeed one.

If you start removing too many critical dependencies, especially from Ubuntu-base, you could leave your system unbootable or unable to run a desktop environment. (your data would be unaffected)  If you ever must do something like that, make sure to back everything up first and then reinstall the appropriate meta-packages like ubuntu-base or ubuntu-desktop before you do anythig else especially including rebooting.



awesome guys, thank you very much for your prompt responses. i have just one last question. I did uninstall tomboy and ubuntu-desktop, and then reinstalled both. When i reinstalled tomboy it said it created a shortcut in applications, accessories..... but it is no where to be found? Where did it go?

Im new to linux and its file locations, so ill ask a very beginners question. Where would tomboy be stored when it is installed on my laptop? (yes i know its on the hard drive.. lol)

Thanks again!

---

### Post by lhtown on 2007-02-07
Try going to System>Preferences>Menu Preferences to see if you can enable it. By default, it shows up on you system bar at the top of the page. You can add it there by rightclicking on the bar and adding it.

To find Tomboy, try /usr/bin/tomboy

---

