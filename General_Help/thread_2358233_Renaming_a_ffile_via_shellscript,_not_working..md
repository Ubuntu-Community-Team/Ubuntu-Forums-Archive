---
title: "Renaming a ffile via shellscript, not working."
date: 2017-04-11
forum: General Help
---

### Post by bask185 on 2017-04-11
I am working in how to update my rpi, updating means in this case, moving a new executable from the plugged in USB stick to the folder and replace the old executable which has the same name. Right now I am trying to rename a file on the USB stick using the shellscript but it is not working. 

I have an empty file yolo which I want to rename to swag
The shellscript looks like:
mv /media/user/"UBUNTU 16_0"/ yolo  /media/user/"UBUNTU 16_0"/ swag

error is:
user@user:~/Desktop$ ./update.sh 
mv: target 'swag' is not a directory

user@user:/media/user/UBUNTU 16_0$ ls

yolo

What am I doing wrong?

---

### Post by vanadium on 2017-04-11
You are having a space before yolo and swag. Thus, the command sees four different items ('/media/user/"UBUNTU 16_0"/', 'yolo', '/media/user/"UBUNTU 16_0"/' and 'swag', and attempts to move the tree first items to the last item, 'swag'. "yolo' is the first item that is not recognised. Details matter when working with commands.

---

### Post by bask185 on 2017-04-11
tnx

---

