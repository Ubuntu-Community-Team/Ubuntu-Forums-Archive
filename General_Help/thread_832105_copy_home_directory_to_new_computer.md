---
title: "copy home directory to new computer"
date: 2008-06-17
forum: General Help
---

### Post by sdowney717 on 2008-06-17
I was wondering if you can simply copy your home folder into a new ubuntu system and set up this home folder as a new user.
Would it have to be the same version of ubuntu?
anyone done this?

Or is their a way to export yourself and then import yopurself into a new system.

---

### Post by mempman on 2008-06-17
Your post is ambiguous and not clear.  Try to rephrase what you mean.  

However,if by new system you are implying that you have a complete install on your harddisk, which includes /home/your-dir.  And I am also assuming that you have a seperate partition that you want to make your /home/your-dir then you would have to make changes to your mount point definitions in your /etc/fstab file.

---

### Post by sdowney717 on 2008-06-17
Ok, this is theoretical since I am not moving to another computer

no separate partition for /home
Simply take my '/home/scott' files and folders
copy them to a different computer running ubuntu
make this /home/scott a new user on that machine.

I assume that the menu system of programs would not be the same from one computer to the other.

---

### Post by lswb on 2008-06-17
It would probably work better to add scott as a user first, using the normal adduser facility of the 2nd system, and then copy the files. Copying the regular files from your home directory, such as media, text, word processing files, etc. will work fine.

The problem will come with all the .files (files that begin with a . and are not shown in a normal diectory listing) in you home directory. These are configuration files and unless the 2 systems are identical it will likely lead to problems. You may have config files for programs that are not present on both systems or conflict in some way with the installation on the 2nd system. I'm not sure from your post if you mean to do this or not.

---

