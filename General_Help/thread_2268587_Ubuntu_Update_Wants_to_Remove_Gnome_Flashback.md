---
title: "Ubuntu Update Wants to Remove Gnome Flashback"
date: 2015-03-09
forum: General Help
---

### Post by bman on 2015-03-09
Hi,

I was using Gnome Flashback on Ubuntu 14.04 and I installed a theme, and ran an update (update was just Firefox).

After reboot, I got to the log in screen (which I normally don't see) and I have Gnome or Gnome Classic only. All of which is not my Gnome Flashback and everything is messed up.

I am assuming my mistake was installing the wrong Gnome theme which is for the newer Gnome setup.

How do I get my setup back?


I ran

sudo add-apt-repository ppa:moka/stable
sudo apt-get update
sudo apt-get install moka-gnome-shell-theme

---

### Post by bman on 2015-03-09
I tried fixing it by running.

sudo apt-get remove moka-gnome-shell-theme

then sudo apt-get autoremove

On reboot I just get black screens now, no nothing.. HELP!

---

### Post by bman on 2015-03-09
I can get to the terminal using CTRL-ALT-F1 but not sure what to do from there.

---

### Post by bman on 2015-03-09
Ok,

I had to install

sudo apt-get install gnome-settings-daemon-schemas=3.8.6.1-0ubuntu11.2

Then re-install gnome-session-flashback and I am back into my system.

I am now worried that if I check updates and run updates or something it will happen again.

---

### Post by bman on 2015-03-09
Side quesiton,

How do I know which themes work for me? I have Gnome Flashback, if I type gnome-shell --version in the terminal it says not installed...

---

### Post by bman on 2015-03-10
Yup,

Ran the Update Manager, and its going to install 40 updates (including Ubuntu Desktop, etc) and removing Gnome-Session-Flashback.

Why is it wanting to do that? How do I stop it from doing that?

---

### Post by ajgreeny on 2015-03-10
Try removing the **ubuntu-desktop** package and then, one by one, the other packages that you don't think you use but are being updated.  Keep an eye on what else is going to be removed at the same time, which may be easiest using synaptic (you may need to install that manually first) as you can ask that to show the "Marked Changes " from the Custom Filters in the left hand pane.

Ubuntu-desktop is a metapackage and does not remove anything except the dependency requirement for the system to install everything that is in the standard Ubuntu unity desktop.

However, I don't think you can blindly remove all packages for unity, ie, those with unity in their name, as some of those are library files and may be needed for packages that you have installed, eg file-roller; I even have four or five "unity" named packages in my Xubuntu 14.04 system, but as I do not use unity they do not have any effect on the system itself.

---

### Post by grahammechanical on 2015-03-10
Gnome shell is not the same as Gnome flashback. Gnome shell is the Gnome user interface that Ubuntu does not use because it has Unity UI. Ubuntu Gnome uses Gnome shell and we can install it on Ubuntu as well.

Gnome classic is an extension to Gnome shell that gives that Gnome 2 panel look. It also is not Gnome Flashback. Installing Gnome Flashback does not install Gnome shell. To get the Gnome 2 panel look on Ubuntu we install Gnome Flashback. To get it on Gnome shell we install Gnome Classic. Mix and matching can create a mess. I have tried it. 

As regards themes, ask, is it for Gnome shell or for Ubuntu? Is it built with the GTK tool kit that matches the GTK libraries that are in the Gnome 3 desktop environment that ubuntu is built on?

Regards.

---

