---
title: "Apache install error"
date: 2008-03-22
forum: General Help
---

### Post by fruni on 2008-03-22
OK, so I am installing apache, I am at the fourth and final step in the install manual thing and this is what happens:

fruni@fruni-laptop:~/Desktop/APACHE$ bin/apachectl start
httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address [::]:80
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
fruni@fruni-laptop:~/Desktop/APACHE$ 
fruni@fruni-laptop:~/Desktop/APACHE$ 


I am not sure what to do, some help would be nice :D

---

### Post by fruni on 2008-03-22
Can someone help me? Or did i mess ubuntu up :confused::confused:

---

### Post by kalesh7 on 2008-03-22
what it means is that you don't have permission for some stuff.
try sudo ~/Desktop/APACHE$ bin/apachectl start
enter your password when asked, hopefully it'll work or someone else will give better reply.

---

### Post by fruni on 2008-03-23
I get: 
sudo: /home/fruni/Desktop/APACHE$: command not found

, I will try it in root.


EDIT: Never mind i see what i  did wrong.

EDIT2: Nope, dont work

EDIT3: It does not work in root either :*(

---

### Post by fruni on 2008-03-23
Bump

---

### Post by fruni on 2008-03-23
Bump

---

