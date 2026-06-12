---
title: "Partial Upgrade Error - v14.04 LTS"
date: 2015-07-22
forum: General Help
---

### Post by Rick St. George on 2015-07-22
Software updater showed "Partial Upgrade". Ran it ... System Error - Reported Error.

Now I have two programs listed - "Software Updater" and "Software and Updates". Both bring up what looks like the same window. Am I infected???

Running Xubuntu v14.04 LTS. Pop-up asked to accept "New Grub". Chose to "see side by side comparison". Saw nothing!  Rebooted laptop.

See two listings of "File Manager"; "Network"; "Onboard"; "Software Updater"; and "Window Manager". Furthermore ... I can't find "Synaptics Package Manager".
I have  round red circle with a white line through it (upper right on taskbar) which says to run Pkg. Mgr. because of dependencies etc.

Any suggestions?

Thanks,
Rick

):P

---

### Post by grahammechanical on 2015-07-22
Software Updater and Software & Updates are two different but related utilites. To put it simply, Software Updater will update the OS for us and Software & Updates is where we change the settings used by Software Updater. It is also where we can activate proprietary video drivers. You always did have Software Updater and Software & Updates.

Synaptic Package Manager is not installed by default on Ubuntu anymore. It might be the same for Xubuntu. If I am remembering the Xubuntu menu system correctly I expect there to be more than one listing in the menu system for some utilities because they can be listed under more than one category. The menu item is just a link to the application. It does not mean you have two versions of the application.

I think that you do have a problem with the list of software repositories (software sources). You can run these commands and post in QUOTE tags any error messages.

```
sudo apt-get update
sudo apt-get upgrade
```

This command will fix dependency problems

```
sudo apt-get -f install
```

This command will configure all partially installed packages.

```
sudo dpkg --configure -a
```

Oh, one more thing. There are reasons why we get offered a partial upgrade. The dialog says this

* A previous upgrade which did not complete
* Problems with some of the installed software
* Unofficial software packages not provided by Ubuntu
* Normal changes of a pre-release version of Ubuntu

It cannot be "Normal changes of a pre-release version of Ubuntu" because you are using 14.04 and the present pre-release version is 15.10. So, which of the other three reasons do you think could have caused the offer of a partial upgrade?

Regards.

---

### Post by Rick St. George on 2015-07-27
I believe that solved that problem.

Thanks!
:popcorn:

---

