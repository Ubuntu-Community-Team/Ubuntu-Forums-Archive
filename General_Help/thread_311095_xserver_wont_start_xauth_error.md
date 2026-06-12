---
title: "xserver wont start :xauth error"
date: 2006-12-02
forum: General Help
---

### Post by vikrant_me on 2006-12-02
My xwindows wont start, this is the error i get at bootup:

xauth:timeout in locking authority file /home/vicky.Xauthority

(EE)xf86OpenSerial:Cannot open device/dev/wacon
No such file or directory
Waiting for Xserver to shutdown FreeFontPath:fpf"usr/share/X11/fonts/misc"
ref count is 2,should be 1;fixed

1:Tried:

ubuntu@ubuntu:~/Desktop/1/home/vicky$ sudo chmod -R 777 /home/ubuntu/Desktop/1/home/vicky -which worked 

ubuntu@ubuntu:~/Desktop/1/home/vicky$ sudo chown -R vicky:vicky /home/ubuntu/Desktop/1/home/vicky -which gave me chown: `vicky:vicky': invalid user


I am using a live cd and have mounted "/" on my desktop in folder "1"

2:Tried deleting Xauthority( a suggestion in one of the posts here) which gave me a "No such file or dir"

---

### Post by vikrant_me on 2006-12-02
bump:

---

