---
title: "Changing Ubuntu 12.04 to Lubuntu 12.04"
date: 2013-02-25
forum: General Help
---

### Post by sammy0025 on 2013-02-25
*Skip to 'Current System' if you want to directly answer my question*

Hi guys,
I'm actually looking for a change in the entire OS, not just the desktop environment. My computer is currently a single boot Ubuntu OS, with GRUB boot-loader installed when I first used a live USB stick to install Ubuntu. I've heard that Lubuntu is very good at memory/CPU usage optimization, just what I need for a game server (yes it is a server, but I prefer graphical interface over command-line interface any day). The reason why I'm choosing to reinstall is because of avoiding the 'bloatedness' of Ubuntu. 

Current system:
Ubuntu 12.04
Planned system:
Lubuntu 12.04

Main Question:
How am I supposed to back up all of my preferences, etc. to e.g. an external HDD and then restore it when I clean install another Linux system based on Ubuntu? 

Thanks in advance,
sammy0025

---

### Post by sudodus on 2013-02-25
1. A clean install

A clean install is the simplest way to do it, and then to add whatever preferences you like to have.

2. Change your system

Backup your system (or at least your /home folder or partition. Then install lubuntu-desktop into your present system
```
sudo apt-get install lubuntu-desktop
```
and make it Pure Lubuntu according to these links

[[COLOR="Red"]http://www.psychocats.net/ubuntu/index[/COLOR]]("http://www.psychocats.net/ubuntu/index")

[[COLOR="Red"]http://www.psychocats.net/ubuntu/purelubuntuprecise[/COLOR]]("http://www.psychocats.net/ubuntu/purelubuntuprecise")

*Edit*: But remember that Lubuntu has no long time support. Its end of life is October 2013, so think twice before doing this. Maybe it is better to run Ubuntu Server with the addition of XFCE
```
sudo apt-get install xfce4
```
and enjoy the LTS support of packages belonging to Xubuntu until April 2015.

You can also install
```
sudo apt-get install xubuntu-desktop
```
and make Pure Xubuntu

---

