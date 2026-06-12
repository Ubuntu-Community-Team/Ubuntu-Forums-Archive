---
title: "Looking for a file in system"
date: 2013-05-15
forum: General Help
---

### Post by Senplanet on 2013-05-15
I made a fortran program that computes large amount of data and it supposed to print out some results on screen. When I run it on background from external mounted hardisk :

./prog >&ww& 

I found out that the ww file is becoming too large because of too many of ascii data. I didn't want to kill the program. so I just deleted the ww while program was running.
After the program ends I found that my system has no free space available. It seems that after deleting the ww file from external hardisk the program continues to write to some other file in some temporal directory in the system.
I tried to check the /tmp and /var/tmp or /lost+found but couldn't find anything larger than 4K bytes .
The du -h command does not help either since it gives me to many results to check for whole system including /home directory. 
Is there any general directory in linux where such a  backup files are automaticaly stored?
Thanks for any ideas

---

### Post by SeijiSensei on 2013-05-15
Try running a filesystem check by booting into recovery mode and choosing the filesystem checking option from the menu.  See if that helps retrieve some space.

---

### Post by Senplanet on 2013-05-15
> **SeijiSensei said:**
> Try running a filesystem check by booting into recovery mode and choosing the filesystem checking option from the menu.  See if that helps retrieve some space.

Thanks for reply. 
Actually, I do not have a problem with a booting. I already make some space ( around 300MB), but I really want to delete the data which used all my space. 
I guess the system decided to store the giga bytes of ascii data to some other file hidden somewhere in the system's directories instead of my working directory. 

So, I'm wondering about how generally linux system deals with the issue, when during running a program in a deamon mode, the storing file is deleted before completion of the program. 
Does it stores the output somewhere else? Where?

Thanks

---

### Post by sanderj on 2013-05-15
I would do this:

Open a terminal, and type
```
cd
ncdu
```

that should give an overview of the disk usage

---

### Post by SeijiSensei on 2013-05-15
> **Senplanet said:**
> Actually, I do not have a problem with a booting.

My response had nothing to do with booting.  It's possible that the filesystem believes some of the inodes are allocated to files when they are not.  Only running fsck will clean that up.  Since you cannot fix a currently-mounted filesystem, you have to do this during boot.  So, again, boot into recovery mode and choose the filesystem checking option.

---

