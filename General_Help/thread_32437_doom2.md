---
title: "doom2"
date: 2005-05-07
forum: General Help
---

### Post by tommytomthms5 on 2005-05-07
im looking to play doom2 on linux but i dont know what programs/files i need

---

### Post by crane on 2005-05-07
[QUOTE=tommytomthms5]im looking to play doom2 on linux but i dont know what programs/files i need[/QUOTE]

Not real sure what other programs/files are needed. I know you need the original doom2 game cd (or the files from it).

Try searching [linux google ](http://www.google.com/linux) with something like installing doom2 or something. Good Luck!

---

### Post by Sam on 2005-05-08
[QUOTE=tommytomthms5]im looking to play doom2 on linux but i dont know what programs/files i need[/QUOTE]
The best way is to install dosbox (universe repository). You need the doom2 files.
Here's a quick help:
[list]
[*]Install dosbox
```
$ sudo apt-get install dosbox
```
[*]Create a fake C:\
```
$ mkdir -p ~/usr/games/dosbox/c
```
[*]Automount your fake C:\ when starting dosbox
```
$ vi ~/usr/games/dosbox/dosbox.conf
```Add these lines:```
[autoexec]
# Lines in this section will be run at startup.
@echo off
echo Mounting harddisk drive C.
mount c /home/<your username>/usr/games/dosbox/c/
echo Mounting CD-ROM drive D.
mount d /media/cdrom/ -t cdrom
C:
```
[*]Unzip your Doom2 files
```
$ unzip doom2.zip -d ~/usr/games/dosbox/c/doom2
```
[*]Run dosbox with your conf
```
$ dosbox -conf ~/usr/games/dosbox/dosbox.conf
```
[*]Run Doom2 from dosbox
```
C:\> cd doom2
C:\DOOM2> doom2
```
[*]Enjoy !
[/list]

---

### Post by tommytomthms5 on 2005-05-08
](*,)  ](*,) 

that just seemed to *screw*(dam it i cant curse here) every thing up and it didnt work


edit: i login as root so i can do more

---

### Post by Sam on 2005-05-08
[QUOTE=tommytomthms5]](*,)  ](*,) 

that just seemed to *screw*(dam it i cant curse here) every thing up and it didnt work


edit: i login as root so i can do more[/QUOTE]
First of all, NEVER log in as root in gnome !!!! Use sudo instead it's intended to do that.

Please explain more your problem and the way you took !

---

### Post by tommytomthms5 on 2005-05-08
why do i "NEVER" lon in as root??? its the same as administrator right? like all it does is lets me do more

---

### Post by Sam on 2005-05-08
As root, everything you do can be lethal for you system. The programs you run have also full access to everything on your system, which is a big security hole.

As I said, use the sudo command instead. This way you have full control on what is done on the system.

This is the way the *nix security concept is made. Don't allow processes to run with privileges if they don't need to.

---

