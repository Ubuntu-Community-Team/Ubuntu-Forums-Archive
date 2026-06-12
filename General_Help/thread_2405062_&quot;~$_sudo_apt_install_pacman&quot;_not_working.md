---
title: "&quot;~$ sudo apt install pacman&quot; not working."
date: 2018-10-31
forum: General Help
---

### Post by jademdasseine on 2018-10-31
&#304; need help. 

```
okan@okan-HP-Pavilion-15-Notebook-PC:~$ sudo apt install pacmanReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 apt : Breaks: aptitude:i386 (< 0.8.10) but 0.6.6-1ubuntu1 is to be installed
 aptitude:i386 : Depends: libapt-pkg4.12:i386 (>= 0.8.16~exp12ubuntu6) but it is not installable
                 Depends: libboost-iostreams1.46.1:i386 (>= 1.46.1-1) but it is not installable
                 Depends: libc6:i386 (>= 2.4) but it is not installable
                 Depends: libcwidget3:i386 but it is not installable
                 Depends: libept1.4.12:i386 but it is not installable
                 Depends: libgcc1:i386 (>= 1:4.1.1) but it is not going to be installed
                 Depends: libncursesw5:i386 (>= 5.6+20070908) but it is not going to be installed
                 Depends: libsigc++-2.0-0c2a:i386 (>= 2.0.2) but it is not installable
                 Depends: libsqlite3-0:i386 (>= 3.6.5) but it is not installable
                 Depends: libstdc++6:i386 (>= 4.6) but it is not going to be installed
                 Depends: libtinfo5:i386 but it is not going to be installed
                 Depends: libxapian22:i386 but it is not installable
                 Recommends: apt-xapian-index:i386 but it is not installable
                 Recommends: libparse-debianchangelog-perl:i386 but it is not installable
 ppa-purge : Depends: aptitude but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```

---

### Post by TheFu on 2018-10-31
Isn't pacman the package manager for Arch?  I don't think you can use it on Ubuntu/Debian. APT is the package management on Debian-based systems.

You can use apt, apt-get, aptitude, synaptic, and a few others to do package management.
[https://askubuntu.com/questions/955309/pacmans-equivalent-in-ubuntu](https://askubuntu.com/questions/955309/pacmans-equivalent-in-ubuntu) shows the translation.

But if you are trying to install a proprietary game named "pacman", I cannot help. Sorry.

---

### Post by deadflowr on 2018-11-01
Not the package manager.
pacman is pacman the game
> Description-en: Chase Monsters in a Labyrinth
 You are Pacman, and you are supposed to eat all the small dots to get to
 the next level. You are also supposed to keep away from the ghosts,
 if they take you, you lose one life, unless you have eaten a large dot,
 then you can, for a limited amount of time, chase and eat the ghosts.
 There is also bonus available, for a limited amount of time.
 An X gives just points, but a little pacman gives an extra life.

It's in the repos.

The output seems to say your running Ubuntu 12.04.
If you are utilizing Ubuntu's paid Ubuntu Advantage support then best to get Ubuntu Advantage support help for this.
If you are not using*Ubuntu Advantage then it's best to say that 12.04 is end of life and no longer supported.
In that case your best course of action is to install a fresh clean version of a supported release such as Ubuntu 16.04 or 18.04.
(And if your want a really new version Ubuntu 18.10, or else the oldest currently supported version 14.04, but that support ends soon, so mind you not install that one)

---

