---
title: "Desktop seems to be broken"
date: 2006-11-22
forum: General Help
---

### Post by RjBanker18 on 2006-11-22
Hey, I recently started up my computer after I did a complete reinstall (did a complete uninstall too) of the package control-center.  I now realize that was a big mistake.  I did it because one of my repos messed up something to do with the control center, so I figured I need to get rid of the package and configs, then install it again.  On the next boot, I got my login screen but after I signed in it just sits there with its tan-ish background.  I did reinstall the control-center before I restarted the computer.  If anyone would help it would be much appreciated.  Thanks!

---

### Post by bigken on 2006-11-22
give this a try boot in safe mode (single user mode) and at the terminal type sudo aptitude install ubuntu-desktop 

also try sudo apt-get update and sudo apt-get upgrade

---

### Post by RjBanker18 on 2006-11-22
I dont know if this will show you anything but...
(I'm not at home I can only SSH, so I cannot "see" if it works :( )

```
The following packages are BROKEN:
  gamin
The following NEW packages will be automatically installed:
  desktop-base fam gnome-applets gnome-panel gnome-session gnome-terminal
  menu menu-xdg nautilus nautilus-cd-burner portmap
The following packages have been kept back:
  amule automatix2
The following NEW packages will be installed:
  desktop-base fam gnome-applets gnome-panel gnome-session gnome-terminal
  menu menu-xdg nautilus nautilus-cd-burner portmap ubuntu-desktop
0 packages upgraded, 12 newly installed, 0 to remove and 2 not upgraded.
Need to get 4322kB of archives. After unpacking 13.4MB will be used.
The following packages have unmet dependencies:
  gamin: Conflicts: fam but 2.7.0-10ubuntu1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
fam [Not Installed]

Leave the following dependencies unresolved:
nautilus recommends fam
Score is -141

Accept this solution? [Y/n/q/?]

```
Also did update/upgrade, no problems there.

---

### Post by bigken on 2006-11-22
I would accept see how it go's

If you have just done a complete install you have nothing to lose

---

### Post by RjBanker18 on 2006-11-22
Thanks bigken for the help!

---

