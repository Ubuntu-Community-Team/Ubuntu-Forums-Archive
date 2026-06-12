---
title: "Steam updates won't work!"
date: 2014-07-16
forum: General Help
---

### Post by Kyle_Undercofler on 2014-07-16
After rebooting my computer from update manager forcing a reboot, (i had clicked on the install button next to some text saying something about hardware, I can't remember exactly) a terminal popped up saying:
"Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386
[sudo] password for kyle:" I entered my sudo password, being used to these kinds of terminals popping up from time to time. Then, the terminal spat this out at me: ".........................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 8.0.4-0ubuntu0.7)
E: Unable to correct problems, you have held broken packages.
Press return to continue: " Can someone please tell me what to do to fix this? (I'm sure it's possible, because this is freaking Ubuntu after all).

---

### Post by ibjsb4 on 2014-07-17
```
sudo apt-get -f install
```
or 
```
sudo dpkg --configure -a
```
Do any good?

Also, what kind of ppa's you have installed?
```
ls /etc/apt/sources.list.d/*.list
```

---

### Post by Kyle_Undercofler on 2014-07-17
Tried the first code in it's own terminal. I also put libglapi-mesa:i386 (the dependancy) at the end of said code, and it worked fine. Also tried the Steam update again, which worked, but when steam opened, it was extremely glitched. It worked as normal, but the gui was completely bugged. It looked like my computer had taken an 8-bit crap.

---

