---
title: "Eye toy in ubuntu help"
date: 2007-02-11
forum: General Help
---

### Post by 21_adam_12 on 2007-02-11
hello, 

i have followed a few tutorials posted on ubuntu forums on how to run the Eye Toy as a webcam in ubuntu and they worked fine. however, after system restart my webcam software keeps saying "could not connect to video device (/dev/video0. please check conection.".
 if any one has any suggestions they would be greatly apreciated, thanx

---

### Post by weaponx69 on 2008-02-24
Your having the same problem I am having.  I used sudo when I ran all the commands and now I think that it will not run because the file is locked and only the sudo user can use it.  I say this because I tried a couple of video4linux devices like tv time and it gave me a better explaination.  It told me that I don't have permission to open the device video 0.  I'm not sure what file to change permissions on to unlock the file for everyone.  It's a pain in the butt.  I'm going to try to reinstall everything without using sudo.

---

### Post by 3rdalbum on 2008-02-24
```
sudo chmod a+rw /dev/video0
```

An explanation:

chmod changes the permissions.
The "a" is who you want the permissions to be changed for (a = all)
The "+" is telling chmod that you want to (a)dd the following permissions
The "rw" is for giving it read/write permission.

---

