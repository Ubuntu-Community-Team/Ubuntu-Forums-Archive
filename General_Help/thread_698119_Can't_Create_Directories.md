---
title: "Can't Create Directories"
date: 2008-02-15
forum: General Help
---

### Post by ronio on 2008-02-15
How do I create directories?  I'm logged in as the superuser that installed Ubuntu 7.10, yet it says permission denied.

I installed WINE to try and get some of my sons games to play.  I have some EA Sports games that hang during the InstallShield process.  From some other threads they said to install it on my Windows box, then just move the whole installation file structure to the Ubuntu and they would play fine.  How the heck do I get this on the Ubuntu box if I don't have any ability to re-create the structure.

Lost and Struggling.
ron

---

### Post by Sam Lars on 2008-02-15
If you just copy the whole folder, does it give you that permission error?  Where are you copying to?

---

### Post by ronio on 2008-02-15
yes, in the graphical file manager i tried to drag the whole folder from my usb stick to the hd

I tried to create a directory in /usr/

creating it off my home directory is not an option as I will expect my son to be able to login and play the game also.  i do not want to give my son permissions to my directory.  and like wise vice-versa i do not want to have to run it from his home directory either.

it would seem that Ubuntu needs to create an APPS directory off the root that everyone can access / write to

---

### Post by Sam Lars on 2008-02-15
You could try putting it in /usr/share/games
You have to use root to get to stuff like that.  You can do in a command line
```
sudo mkdir /usr/EASports
```
Or wherever you want to put the directory, whatever you want to name it.
Also,
```
sudo nautilus
```
and you can now browse graphically as root.

---

