---
title: "proper way to remove applications"
date: 2007-04-18
forum: General Help
---

### Post by zanjabeel5 on 2007-04-18
Hi

when i try to remove gimp using synaptic it also removes extra packages one of them being gnome !! (the whole desktop)   so before rebooting I try to reinstall gnome but it brings gimp back with it.

apt-get does that also

I can live with gimp, but I face this problem when removing other software I don't want.
what am I doing wrong ?

------------------------------------------------------------
( I have one month experience in ubuntu )

---

### Post by aysiu on 2007-04-18
*ubuntu-desktop* isn't Gnome. It's just a pointer to all the default applications. Remove a default application, and you remove the pointer.

Read [here](https://help.ubuntu.com/community/CommonQuestions#head-957d1f0d9534d9e9a43a1ade8e3622bc04a8d812) more about removing *ubuntu-desktop*.

---

### Post by zanjabeel5 on 2007-04-18
when I remove gimp it also removes **gnome** not **ubuntu desktop**
is this Ok ?

------------------------------------------------------

sudo apt-get remove gimp
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  planner libgsf-gnome-1-114 gnome-desktop-environment libgoffice-0-common abiword-gnome dia-libs industrial-cursor-theme
  gnome-office abiword-common gnumeric-common upstart-compat-sysv gnome-themes-extras gdm-themes fast-user-switch-applet
  dia-gnome gdm gnome-backgrounds startup-tasks libgoffice-0-3 system-services gimp upstart-logd gnome-core dia-common
  gnumeric upstart gtk2-engines-spherecrystal gnome inkscape
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gimp gnome gnome-office
0 upgraded, 0 newly installed, 3 to remove and 29 not upgraded.
-------------------------------------------------------------------------------------------

---

### Post by aysiu on 2007-04-18
*gnome* is also a metapackage that depends on *gnome-office[/], which is itself a metapackage that depends on [i]gimp* and a bunch of other applications (*abiword, dia-gnome, gnumeric,* etc.).

---

