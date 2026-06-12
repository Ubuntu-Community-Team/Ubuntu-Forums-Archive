---
title: "SSH-RSA Keys"
date: 2013-05-16
forum: General Help
---

### Post by ammontgo on 2013-05-16
I can create RSA keys that work for Ubuntu-Ubuntu or Mac-Ubuntu but when I use puttygen to create keys on windows, I can't get them to work.  I have read several tutorials and know about converting the private key for use with putty and filezilla.  The windows generated keys once catted into authorized_keys do not look exactly like those created on a linux based system.  Does anyone know what I'm doing wrong?  What additional information do I need to provide?

---

### Post by Irihapeti on 2013-05-16
This might be helpful:

[http://superuser.com/questions/232362/how-to-convert-ppk-key-to-openssh-key-under-linux](http://superuser.com/questions/232362/how-to-convert-ppk-key-to-openssh-key-under-linux)

Disclaimer: I've not tried this, though I have done it in the other direction i.e. ssh to putty

---

### Post by steeldriver on 2013-05-16
DON'T save the generated key using the PuTTYgen 'Save public key' button

DO copy it from the 'Public key for pasting into OpenSSH authorized_keys file' pane 

You can open the remote ~/.ssh/authorized_keys file in a terminal-based editor (e.g. nano) via a password-based PuTTY session, and just copy-paste it in

Also make sure the authorized_keys file is mode 600 (-rw------)

---

### Post by ammontgo on 2013-05-16
Thanks very much for your posts.  I will try this soon and let you know how it goes.

---

### Post by ammontgo on 2013-05-17
These step by step instructions did the trick.  Thanks for the help guys.

Generate the keys with ssh-keygen
cat id_rsa.pub >> authorized_keys
Download id_rsa
Open it with puttygen
Click save private key
Open putty
Go to Connection -> SSH -> Auth 
pick the ppk file you just saved (Your private key in putty format)

EDIT: It doesn't matter where you generate the keys, just make sure they're saved in the correct format in the correct places (OpenSSH on the server, PPK on Windows)[COLOR=#CCCCCC][FONT=Verdana]
[/FONT][/COLOR]

---

