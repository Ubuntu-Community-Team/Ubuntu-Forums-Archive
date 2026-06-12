---
title: "Root password on Live CD"
date: 2005-10-11
forum: General Help
---

### Post by kuriharu on 2005-10-11
Hello,

I'm using the Live CD and I'd like to know what the default root password is. I want to use it to mount an NTFS hard drive and I can't su to root.

---

### Post by Zelut on 2005-10-11
There isn't actually a default root account or password in Ubuntu.  It uses the first created user (or added users) as having 'access' to root priveledges, but there is no root account by default.

---

### Post by kuriharu on 2005-10-12
Thanks for replying.

So how do I run commands like mount? I tried to mount a hard drive and I got an error "Only root can use mount". When I try to run su I get prompted for a  password (of course) and I don't know it. I tried root, ubuntu, admin, etc.

The Live CD runs Ubuntu without installing it, so I can't add/delete accounts and I never get prompted to set a root password. What I want to do is use the Live CD to boot to laptop with a failing hard drive and use Ubuntu to copy files off the hard drive onto a flash drive. But I can't mount the hard drive since I need access rights.

---

### Post by karuptdata on 2005-10-12
simply tupe in sudo before the command such as sudo mount...

---

### Post by daschl on 2005-10-12
or do it that way:

$ sudo su

:)

---

### Post by kuriharu on 2005-10-12
Thanks, I'll give it a shot. My CD failed an integrity test so I have to reDL it and reburn. I'll post again in about 2 hours....

---

### Post by varsara on 2007-10-04
there is a root password however and i need to know what it is to mount and allow access to my secondary hard disk. i know its an 8 digit password but other than that i have no clue. anyone know it?
also im using a system installed from the live CD if anyone needs to know

---

### Post by varsara on 2007-10-04
i just found a workaround for anyone who may have the same issue


just type the following syntax to reset the root pass

sudo passwd root


hope this helps anyone having my problem

---

