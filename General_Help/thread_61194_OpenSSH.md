---
title: "OpenSSH"
date: 2005-08-30
forum: General Help
---

### Post by Freddie on 2005-08-30
Hi, I have just installed OpenSSH, however I am having some problems with it. It installed fine, and on my iBook I can type in ssh 192.168.0.5 -l freddie and it sit there for about 30 seconds before asking me for my password. However, the first time I connected using my iBook I got a security warning. I then tried to connect using a Java SSH applet however it also warns of a security/hash problem before saying that it does not support the 'password' method. Can anyone help me at all?

---

### Post by ubuntme on 2005-08-30
not sure I understand what the problem is, but if you run ssh -v you get a verbose output. similarily, -vv or -vvv will give you the level 2 and level 3 debug outputs.  This may help you find the problem.

---

### Post by Freddie on 2005-08-31
I am having some problems accssing my server using a java ssh client. I works fine with putty and the linux 'ssh' programs. Does anyone know of a good java ssh applet that works?

---

### Post by WirelessMike on 2005-08-31
try this in the command line:
> ssh username@127.0.0.1  (not that address, exactly, of course, but the address of the server)
You should then be prompted for a password, then a key warning which you can just "ok"

---

### Post by WirelessMike on 2005-08-31
Sorry--  Not familiar with Java SSH clients

---

