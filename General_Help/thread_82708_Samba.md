---
title: "Samba"
date: 2005-10-27
forum: General Help
---

### Post by theFUZZYpickle on 2005-10-27
Hello everyone,

I just installed Ubuntu 5.10 and I am trying to get Samba to work on it.  I am trying to create two users, one for me (dan), and another for my roommate (fileserv) that we can both access from a Windows machine to store music.  I only want my roomate to be able to access (fileserv), not (dan).  I can both access (dan) and (fileserv), however my roomate cannot access (fileserv) because Windows asks for a username and password for (fileserv), but when I enter the username and password that I specify, it doesn't work.  I am so confused, what should I do??  Here is what I have in my smb.conf:

[fileserv]
   comment = files
   path = /home/fileserv
   valid users = dan @guest
   guest ok = yes
   public = yes 
   writable = yes
   printable = no
   create mask = 644

Please help!

---

### Post by snowjunkie on 2005-10-27
I'm not able to help you, just want to track this thread to see what the answer is!

---

### Post by myha on 2005-10-27
[QUOTE=snowjunkie]I'm not able to help you, just want to track this thread to see what the answer is![/QUOTE]
You have thread tools above and you can subscribe to it....

---

### Post by mykey on 2005-10-27
[QUOTE=theFUZZYpickle]Hello everyone,

I just installed Ubuntu 5.10 and I am trying to get Samba to work on it.  I am trying to create two users, one for me (dan), and another for my roommate (fileserv) that we can both access from a Windows machine to store music.  I only want my roomate to be able to access (fileserv), not (dan).  I can both access (dan) and (fileserv), however my roomate cannot access (fileserv) because Windows asks for a username and password for (fileserv), but when I enter the username and password that I specify, it doesn't work.  I am so confused, what should I do??  Here is what I have in my smb.conf:

[fileserv]
   comment = files
   path = /home/fileserv
   valid users = dan @guest
   guest ok = yes
   public = yes 
   writable = yes
   printable = no
   create mask = 644

Please help![/QUOTE]
I guess you are a little mixed up here - the definition you posted is for a share NOT a user PLUS the user who wants to access the share has to exist on the system AND it is not really clear who is supposed to access what - samba can be a little picky so maybe you should have a look here first [HOW TO: share files using Samba (the more secure way)]("http://ubuntuforums.org/showthread.php?t=76647")

---

### Post by ipn1nj4 on 2005-10-27
[QUOTE=theFUZZYpickle]



[fileserv]
   comment = files
   path = /home/fileserv
   valid users = dan @guest
   guest ok = yes
   public = yes 
   writable = yes
   printable = no
   create mask = 644

[/QUOTE]


Have you created the samba users?

```
smbpasswd -a dan
```

---

