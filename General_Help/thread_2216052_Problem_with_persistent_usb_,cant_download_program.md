---
title: "Problem with persistent usb ,cant download programs via terminal"
date: 2014-04-09
forum: General Help
---

### Post by 7h364m3 on 2014-04-09
Hi guys i made a presistent usb with unetbootin with 1024mb persistent space.
The problem is i cant download anything via terminal or maybe at all.
I also tried with universal usb installer the same thing happens i cant download programs :(

Here is what happens :
> ubuntu@ubuntu:~$ sudo apt-get install gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-panel is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.4%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140204)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Package 'gnome-panel' has no installation candidate

---

### Post by grahammechanical on 2014-04-09
Is it any application that you cannot install or just gnome-panel? You may need to go into Software Sources and enable the Universe repository. Then update after which you may find that you can install gnome-panel. While there you can also remove one or both of the entries that have the cdrom as a sources list/software source/repository. Then that other error message should go away.

Regards.

---

### Post by 7h364m3 on 2014-04-09
Where i can find Software Sources it seems i cant find this :(

pp: nvm i found it :D

---

