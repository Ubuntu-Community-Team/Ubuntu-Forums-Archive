---
title: "(gksu:2010): Theme directory imported-Humanity/192 of theme Lubuntu has no size field"
date: 2017-02-07
forum: General Help
---

### Post by surya.dilip on 2017-02-07
I'm running lubuntu 16.10 Yakkety Yak. I installed VMware Workstation 12.5.2 build-4638234. I want to run VMware Workstation as root so i entered the command "gksu VMware Workstation" and i'm getting the message as "(gksu:2010): Gtk-WARNING **: Theme directory imported-Humanity/192 of theme Lubuntu has no size field". PFA screenshot. Please help.

---

### Post by daffodils on 2017-03-19
I was getting ```
Gtk-[COLOR=yellow]WARNING[/COLOR] **:Theme directory imported-Humanity/192 of theme Lubuntu has no size field
``` when running graphical applications from the terminal in Lubuntu.  I "fixed" it by editing */usr/share/icons/Lubuntu/index.theme* to remove all instances of "imported-Humanity/192".  (remove ",imported-Humanity/192" from the end of the line that starts with "Directories=" and remove the section that begins "[imported-Humanity/192]" near the end of the file.)  It's not exactly elegant but it's easy.  I think you could alternatively use a different theme.

The offending section of index.theme did have a size field though.  Maybe this is a bug?

---

### Post by ghm-in-abq on 2017-03-21
There is a related bug which may come up with a proper solution: [https://bugs.launchpad.net/ubuntu/+source/hardinfo/+bug/1634462](https://bugs.launchpad.net/ubuntu/+source/hardinfo/+bug/1634462)

---

