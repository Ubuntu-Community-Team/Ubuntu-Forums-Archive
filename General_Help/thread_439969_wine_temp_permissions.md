---
title: "wine: temp permissions"
date: 2007-05-11
forum: General Help
---

### Post by uantuzri on 2007-05-11
Hi,

I'm trying to install womble mpeg video wizard trough wine, which I have never used before. When I try to install it, it displays a message that says 
"the file 'C:\windows\temp\GLF9bba.tmp' could not be opened. Please check that your disk is not full and that you have access to the destination folder. Access denied."

Of course, the disk is not full. I tried some things with the registry and the temp variables, but the problem (I think) is in the file permissions: When I launch the installer, some files are created on the windows\temp folder (placed in ~/.wine/drive_c). Their permissions are -rw-r--r--

I think the the problem has to do with this. How can I make that these files are read/write for all when created. Maybe I'm wrong and the problem is not related with this. 

I would really appreciate your help. I have many files on this program's extension, and I need to edit and export them to mpg.

---

### Post by tCarls on 2007-05-12
Use umask to set the default permissions of new files. If you want new files to be read / writeable and not executable for all users, run "umask 111". I'm not sure if that'll work through wine, but that's how you would normally do it.

---

