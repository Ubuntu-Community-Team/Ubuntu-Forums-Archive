---
title: "Installing Wine on 7.04?"
date: 2007-05-15
forum: General Help
---

### Post by CarlosinFL on 2007-05-15
Has anyone been able to install Wine on 7.04? I attempted for the 1st time today and it appears I don't have a available .deb file for it in my repo.

```
cwilliams@cwilliams:~$ sudo apt-cache search wine
kftpgrabber - KDE FTP client
libwine - Microsoft Windows Compatibility Layer (Dummy Package)
libwine-dev - Microsoft Windows Compatibility Layer (Dummy Package)
tellico - collection manager for books, videos, music
tellico-data - collection manager for books, videos, music [data]
winefish - LaTeX Editor based on Bluefish

```

---

### Post by LuisGMarine on 2007-05-15
Get the .deb from the [official wine website.]("http://www.winehq.org/")

Or look here to add the extra repos incase you didn't have them, [click here.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by zvacet on 2007-05-15
Open all repositories with **system>administration>software properties<chek all boxes<reload**
After that go to the synaptic and in search box type wine and when you find it mark it for installation

---

### Post by Jordy_U on 2007-05-15
I am just successfully installing wine on 7.04
first you must have Internet connection from your Ubuntu 7.04,
then go to this page
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

the follow this instructions:

Adding the WineHQ APT Repository:
First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Feisty (7.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

Hope this help
:)

---

