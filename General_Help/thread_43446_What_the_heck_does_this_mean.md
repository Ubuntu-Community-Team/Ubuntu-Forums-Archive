---
title: "What the heck does this mean?"
date: 2005-06-22
forum: General Help
---

### Post by electroglas on 2005-06-22
root@ubuntu:/home/--------- # gedit

(gedit:10355): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by jrev on 2005-06-22
gobbledygook 
gobbledygook 
gobbledygook  ;-)

---

### Post by TravisNewman on 2005-06-22
Did gedit come up afterward? I've seen this a lot but it has yet to stop me from using things.

---

### Post by electroglas on 2005-06-22
Yes, Gedit came up but this message makes you wonder why it occurs and what can can done about it.

---

### Post by NiceGuyUK on 2005-06-22
I'm guessing here, but I heard that Gnome likes the hostname to be in /etc/hosts - not just localhost, but the actual hostname of your machine.  It *might* be related to that

---

### Post by electroglas on 2005-06-22
[QUOTE=NiceGuyUK]I'm guessing here, but I heard that Gnome likes the hostname to be in /etc/hosts - not just localhost, but the actual hostname of your machine.  It *might* be related to that[/QUOTE]
 This is in my /etc/hosts file

127.0.0.1 localhost.localdomain localhost ubuntu

---

### Post by az on 2005-06-22
Are you, perchance, running kdm?

---

### Post by electroglas on 2005-06-22
[QUOTE=azz]Are you, perchance, running kdm?[/QUOTE]
 gdm

---

### Post by art on 2005-06-22
I think that NiceGuyUK is right, since I have a wireless laptop (i.e. localhost.localdomain) and it does the same as described in the question, but  on the machine which is directly connected to internet it does not :???:

---

### Post by NiceGuyUK on 2005-06-23
Ok, so much for my theory then :(

---

