---
title: "Backup How to"
date: 2007-10-01
forum: General Help
---

### Post by JawsThemeSwimming428 on 2007-10-01
I have looked through the Backup guides I have found and haven't found one that seems to do exactly  what I want. I want a backup of my Feisty system that I can restore to a new system ( it does not have to be an image, I don't mind installing Feisty clean and then just updating the fresh install). However, I want a complete backup (system state and data). Anyone that can point me in the right direction I would really appreciate it. Thanks!!

---

### Post by jimmy2975 on 2007-10-02
I use fwbackups for my data. Must be able to backup anything !

Jimmy

---

### Post by Rocket2DMn on 2007-10-02
I use Simple Backup - I believe it's called sbackup in the repositories.  It has a nice little GUI interface that you can access from System->Administration.

---

### Post by vinutux on 2007-10-02
install [COLOR="Red"]sbackup[/COLOR] in from synaptic 

it is the best solution for simple backup and restoring ur data from home folder and other places u want and restore it ...............

simple and wonderfull program recomended:lolflag::lolflag::lolflag::

---

### Post by JawsThemeSwimming428 on 2007-10-02
Does any of those back up system state?

---

### Post by Rocket2DMn on 2007-10-02
I'm not sure what you mean by system state, but you can tell it to back up whatever folders you want.  When you backup your home folder, it will backup all your settings for different programs, GUI preferences, etc.  You could potentially backup your /bin and /usr/bin directories, but programs can always be reinstalled if you have to restore your system and your config files will still exist for them.
I backup my /home/username directory, /var, /etc, /usr/local, and my music folder which is on a separate partition.  I think that should be adequate, but feel free to search around and see if other people have different suggestions - my advice is by no means the one and only way to do things.

---

### Post by Rocket2DMn on 2007-10-02
In response to ru0n's private message:

[QUOTE=ru0n]I use Simple Backup - I believe it's called sbackup in the repositories. It has a nice little GUI interface that you can access from System->Administration.


Hey, i'd like to "backup" the current status that i have now. So that i can then put it on a couple other Computers with the same Hardware. Can Simple Backup do that?[/QUOTE]

Theoretically you could, but there are other programs that can take a snapshot of your hard drive and then you can load that image onto another computer.  I don't use any myself, but I've heard of partimage ([HowTo]("http://ubuntuforums.org/showthread.php?t=287522") or [this]("http://www.partimage.org/Partimage-manual_Usage")), as well as a similar program to Norton Ghost called Ghost for linux - sourceforge page [here]("http://sourceforge.net/projects/g4l").  You can easily dig around for some HowTo's on that.
Good luck!

---

