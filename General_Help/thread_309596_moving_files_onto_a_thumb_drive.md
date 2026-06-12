---
title: "moving files onto a thumb drive"
date: 2006-11-29
forum: General Help
---

### Post by jhlk219 on 2006-11-29
hey all, when windows stopped working a few days ago i installed ubuntu on a second hard drive. i managed to mount the old hard drive and get the files I needed off of there and onto the root desktop. however, from there i'd like to be able to get them onto my dad's computer (these are important files, tax returns, etc) but when I try to drag-and-drop the folder from the root desktop onto the USB drive (which shows up on the desktop and everything) it says I don't have permission to do that. the thing is, I don't have the option to change permission and ownership of the files when I try to from the root desktop.

so basically, i've got a folder on the root desktop called "dad stuff" which has about five other folders in it. I can change permissions on the actual "dad stuff" folder from root, but if I go into the folders and try to edit permissions/ownership of them I can't change ownership to my user. is there a way I can do this through the terminal? being able to access the "dad stuff"
 folder from my username won't help me if I can't do anything to the actual files themselves and get them on the flash drive. thanks in advance

---

### Post by Peepsalot on 2006-11-29
What do you mean root desktop?

---

### Post by strabes on 2006-11-29
can you do a ```
sudo nautilus /root/Desktop
``` Then drag the files from there onto the drive?

you can change permissions with the terminal: ```
sudo chmod 777 /path/to/file
``` You might want to research about chmodding in linux though. You probably don't want 777.

---

### Post by jhlk219 on 2006-11-30
thanks guys, i figured it out and everything's working. thanks for your help

---

### Post by lsutiger on 2007-03-05
jhlk219, How did you do it..I am roaming the forum looking for an answer to the same exact problem.
Thanx

---

