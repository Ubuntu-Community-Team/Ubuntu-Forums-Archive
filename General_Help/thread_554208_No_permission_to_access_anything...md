---
title: "No permission to access anything..?"
date: 2007-09-18
forum: General Help
---

### Post by Phelan on 2007-09-18
Sorry to bother you with complete newbieness, I just got 7.04 installed today.  I am trying to move some files around a do a bunch of stuff, but ubuntu wont let me touch any files on my windows partition...it says its protected.  As far as the ubuntu partition, i cant make folders or do anything on it either, it's the same way.

I was trying to install urbanterror, but I can't even make a folder to untar the game into??  Please help an idiot.

---

### Post by Lacrimstein on 2007-09-18
Simple - you can't write to an NTFS drive (NTFS is a proprietary file system). To be able to do it, just install ntfs-3g

---

### Post by Lacrimstein on 2007-09-18
Oh, and exactly were in the Ubuntu partition are you trying to move those files? As a user, you only have rights to create/edit files in your home directory and up. If you really feel like putting someting in /, type

sudo nautilus

then enter your password, and you will be able to create files there, but I don't recommend that

---

### Post by Phelan on 2007-09-18
Thanks. The ubuntu partition is 55% of my drive, why shouldn't I put stuff there??  How would I go about installing a game like UrbanTerror without untar'ing the files somewhere?  Sorry for being an idiot and thanks!!!

---

### Post by Nem1976 on 2007-09-18
I found it's best to untar it in your home directory.  Create a folder called installs or something and untar the file there then run the install.

---

### Post by Phelan on 2007-09-18
The home is obviously part of the "/" root, but where is it located?  Obviously I can just click on the home shortcut, but where is home actually located?  Thanks so much.

---

### Post by Lacrimstein on 2007-09-18
the location of your home folder is in /home/yourname

---

### Post by Phelan on 2007-09-18
Wow that was sure obvious...i am so intimidated by linux.

---

