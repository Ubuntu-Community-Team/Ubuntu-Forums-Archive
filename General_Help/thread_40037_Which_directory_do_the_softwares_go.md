---
title: "Which directory do the softwares go?"
date: 2005-06-07
forum: General Help
---

### Post by duffmckagan on 2005-06-07
I want to back up the softwares which are downloaded from the internet using apt-get

for example, when i try to install xmms, it downloads it from the archives and installs it on my computer.

I would like to know how do i back this up, and later, change the source to my local directory where xmms is placed. How do i do both these things?

---

### Post by mtron on 2005-06-07
see ubuntuguide "How to backup/restore downloaded repositories cache?" [here](http://ubuntuguide.org/index.html#backuprestoredownloadedrepositoriescache) 

or after installing ubuntu , delete all packages in the folder /var/cache/apt/archives, install all extra packages you want, then copy all downloaded packages from this folder to a cd, or somewhere else

to install these packages:
open a terminal, cd to the cdrom and run "sudo dpkg -i *.deb"

this will install all packages on the cd.

---

### Post by duffmckagan on 2005-06-07
Good idea, I will try that.

I had already read the repositories backup point in the Guide, but wasn't knowing which directory do they go to.

Thanks.

---

### Post by duffmckagan on 2005-06-07
I forgot to delete the already present packages in the archives.

I realised this re-reading and re-reading your post.

What if I don't delete it and then paste the stuff right back after a new installation in the archives folder?

---

