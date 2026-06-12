---
title: "Can't Delete .Trash-1000 Folder"
date: 2016-04-30
forum: General Help
---

### Post by dannymichel on 2016-04-30
I can't delete this trash-1000 folder on my external
```
# Pastebin QZMleIuD
danny@danny:~$ rm -rf '/media/storage/.Trash-1000' 
rm: cannot remove '/media/storage/.Trash-1000/expunged/2257922320/Issue 1/Indesign files/Links/._MG_7423RE.jpg.vqQA2i': Permission denied
danny@danny:~$ sudo rm -rf '/media/storage/.Trash-1000' 
[sudo] password for danny: 
rm: cannot remove '/media/storage/.Trash-1000/expunged/2257922320/Issue 1/Indesign files/Links/._MG_7768RE.jpg.tlHhiD': Permission denied
danny@danny:~$ sudo -i
root@danny:~# rm -rf '/media/storage/.Trash-1000' 
rm: cannot remove '/media/storage/.Trash-1000/expunged/2257922320/Issue 1/Indesign files/Links/.corradodalco 046.jpg.GfPTf9': Permission denied
root@danny:~# 
```

---

### Post by Impavidus on 2016-05-01
So what are the permissions on that file and directory?```
ls -l '/media/storage/.Trash-1000/expunged/2257922320/Issue 1/Indesign files/Links/.corradodalco 046.jpg.GfPTf9'
ls -ld '/media/storage/.Trash-1000/expunged/2257922320/Issue 1/Indesign files/Links/'
```(If this gives you "Permission denied", try again with **sudo ls ...**)

---

### Post by dannymichel on 2016-05-01
I ended up doing gksudo nautilus and deleting it.
Not sure why that worked

---

### Post by RobGoss on 2016-05-01
Hello if you solved this problem would you mind marking this thread as solved. Thanks so much

---

### Post by dannymichel on 2016-05-01
> **RobGoss said:**
> Hello if you solved this problem would you mind marking this thread as solved. Thanks so much

It was marked as solved a long time ago

---

