---
title: "truecrypt: Failed to assign loopback device for file-hosted volume"
date: 2008-02-06
forum: General Help
---

### Post by Repley on 2008-02-06
Hello, 
when i try to mount all my volumes, at ninth i obtain:

**Failed to assign loopback device for file-hosted volume**

Can i have only 8 lb-dev? No more? how to increase the number of lb-dev? or,  where can i buy? LOL

I'm a newbie on linux. Thank you.

Bye

---

### Post by Repley on 2008-02-13
Solved

create a file (or edit):
sudo gedit /etc/modprobe.d/local

add this line to increase the number of loopback device:

options loop max_loop=255

Alternatively, you can change in /etc/modules tihs line:

loop

with this line:

loop max_loop=255

Thank to Md of irc channel #linux-it on irc.freenode.net

---

### Post by Repley on 2008-02-13
Solved

create a file (or edit):
sudo gedit /etc/modprobe.d/local

add this line to increase the number of loopback device:

options loop max_loop=255

Alternatively, you can change in /etc/modules tihs line:

loop

with this line:

loop max_loop=255

Thank to Md of irc channel #linux-it on irc.freenode.net

---

### Post by Repley on 2008-02-13
Solved

create a file (or edit):
sudo gedit /etc/modprobe.d/local

add this line to increase the number of loopback device:

options loop max_loop=255

Alternatively, you can change in /etc/modules tihs line:

loop

with this line:

loop max_loop=255

Thank to Md of irc channel #linux-it on irc.freenode.net

---

### Post by Repley on 2008-02-13
sorry for clones reply. I don't know why. How to delete a reply? i click edit/delete but i don't find delete option.

---

