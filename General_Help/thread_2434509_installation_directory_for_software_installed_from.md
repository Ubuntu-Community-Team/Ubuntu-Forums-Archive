---
title: "installation directory for software installed from .run file"
date: 2020-01-07
forum: General Help
---

### Post by KNAKjao0 on 2020-01-07
I am trying to install the computer algebra system Maple. Maple does not have a package in the repository and so cannot be installed by something like sudo apt install maple. Instead, Maple provides a file Maple2019.2LinuxX64Installer.run. When I run this I am asked by the program
[INDENT]Choose Install Folder
Please specify the directory where Maple will be installed.
[/INDENT]

I have never installed software in Ubuntu from a .run file before. Where should I install Maple?

---

### Post by CatKiller on 2020-01-07
[https://wiki.archlinux.org/index.php/Maple](https://wiki.archlinux.org/index.php/Maple)

> After purchasing your license, download the appropriate Maple release package and unpack it in a location of your choosing. Open a terminal, change to the directory in which you unpacked the files, and run the installer script as a normal user. Installing the program's files inside of a user's home directory is the default option, and allows for easy removal of all components at a later time. 

---

### Post by Impavidus on 2020-01-07
If installing for a single user, its OK to put it somewhere in your home directory. For system-wide installation, use /usr/local/ or /opt/. Those are the directories meant for that.

---

