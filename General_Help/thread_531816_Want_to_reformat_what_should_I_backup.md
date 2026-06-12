---
title: "Want to reformat what should I backup?"
date: 2007-08-22
forum: General Help
---

### Post by SnowPunk98 on 2007-08-22
I wanna blow away my Feisty install and take that space and dual boot it with Gutsy and another Linux distro. I have never reformatted Linux before so I don't know what if anything is important to backup. Obviously I know what data to backup but not what system files should be backed up. Should I just backup my whole /home dir and maybe my GRUB menu.lst? or do I just need data?

---

### Post by mayonaise15 on 2007-08-22
If you just backup the contents of your /home directory you should be fine.  There are some hidden files in your home directory that store your settings (like for firefox and other programs).  You can see them if you open up your home directory from the Places menu the pressing "Ctrl+H".

---

### Post by eentonig on 2007-08-22
You might also take the time to backup /etc

This way, you can reinstall programs and then copy their original config files back.

Also, in /home/<username>/, there are a crapload of hidden files that contain your user preferences. You might be interested in saving the ones you care about. I always keep at a minimum .bashrc, .bash_aliases and .profile

---

### Post by ironfistchamp on 2007-08-22
Generally I have just backed up /home and have never had any problems. Sometimes there will be menu items (especially if you are using USP) that are dead and will not have an icon if the icon was from a folder of an installed program. 
 
HTH
 
Ironfistchamp
 
 
PS: w00t on my 600th bean!

---

### Post by notwen on 2007-08-22
I back up /home primarily when wiping my HDD and starting w/ a fresh install.  =]

---

