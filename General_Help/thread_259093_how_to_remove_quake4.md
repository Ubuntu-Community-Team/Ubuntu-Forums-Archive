---
title: "how to remove quake4"
date: 2006-09-16
forum: General Help
---

### Post by ezek on 2006-09-16
Hey, i need to reinstall quake 4 becasue i messed it up and i can remove it. i type in sudo rm <file place> and it cant for some reason. I cant even right click the folder and remove it. can i get some help pls?

---

### Post by Anduu on 2006-09-16
Try gksudo nautilus in a terminal and navigate to the Quake4 directory and delete it.

---

### Post by th3t1nm4n on 2006-09-16
sudo rm -rf /usr/local/games/quake4
sudo rm -rf /usr/local/bin/quake4*
rm -rf ~/.quake4

That should do it if you ran the installer with sudo.

---

### Post by kuja on 2006-09-17
Probably didn't make much sense to install it as root in /usr/local/games anyway if you ask me. I'd just install it somewhere in the home directory (and I have). Less hassle, and also, seeing as I keep my home directory seperate, It also gets to be lucky and survive reinstalls :)

---

### Post by th3t1nm4n on 2006-09-19
I'm not one to uninstall games, I like the seperation of user files being in ~/.quake4/, that way I can back up just my configs/files and reinstall the game from DVD. I also have multiple users on my box though, so the root install was necessary. (Put the .pk4's, the linux client installer, and a little shell script that copies the .pk4's to where they belong and then downloads punkbuster to ~/.pb/ because I was bored and decided that I needed a Linux version of my Quake 4 DVD :razz: )

---

