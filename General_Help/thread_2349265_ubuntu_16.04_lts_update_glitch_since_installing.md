---
title: "ubuntu 16.04 lts update glitch since installing"
date: 2017-01-12
forum: General Help
---

### Post by jimbean on 2017-01-12
i googled but came up empty


every time the red circle with the line through it, on the top menu bar pops up stating that there are updates pending i click the button and install updates

then reboot :)

but after reboot i have to go to the ubuntu software repository and finish installing updates for the (os) ????

---

### Post by wildmanne39 on 2017-01-12
Open the terminal and run:
```
sudo apt-get update && sudo apt-get upgrade
```
if you get errors post them here between code tags by clicking on the # above this window.
Thanks

---

### Post by ik-0 on 2017-01-14
You need to do a fix install
$ sudo apt-get -f install

Done packages were interrupted during installation while an update/install was happening. The above line will try to fix the missing packages.

---

### Post by jimbean on 2017-03-19
sudo apt-get update && sudo apt-get upgrade
came up nothing
and the repair command would not work
this is happening on my 2 different machines running 16.04 ubuntu
so i dont think it a repair issue but maybe

but thanks for help

---

### Post by jimbean on 2017-03-25
also every time there is an update released 

i have update notification enabled 

i get a system error upon starting machine in ubuntu 16.04

this is happening on both of my ubuntu 16.04 machines

im thinking i am going to look for an automatic update setting and see if that helps

---

### Post by Impavidus on 2017-03-25
> **jimbean said:**
> sudo apt-get update && sudo apt-get upgrade
came up nothing

That isn't much. apt-get is a very verbose command. It tells exactly what it's doing and gives clear error messages when something goes wrong. Clear to us at least, maybe not (yet) to you.

The proper way to do it on 16.04 is actually```
sudo apt update
sudo apt upgrade
```(or put them on one line with && inbetween), which will also install new packages if necessary, usually for kernel upgrades. It may help if you post the complete output.

If it all works, that no entry sign (red disk with bar) should be gone too.

---

