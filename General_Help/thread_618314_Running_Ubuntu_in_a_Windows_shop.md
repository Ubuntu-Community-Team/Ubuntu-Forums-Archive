---
title: "Running Ubuntu in a Windows shop"
date: 2007-11-20
forum: General Help
---

### Post by jimzat on 2007-11-20
My company is a completely Windows shop running Active directory, etc.  I have been a Linux user for a few years now and have been running Ubuntu on my (Inspiron 7500) laptop since Dapper and recently installed Gutsy.

A few months ago, I loaded Feisty (via Wubi) on my corporate desktop and have been very pleased with it.  Yesterday I received a voice-mail from our corporate IT department saying that the machine named xxxxx has been giving some interesting information to Active Directory.   I called them back and was told that the desktop machine is announcing itself as a Linux server (something about directory services).

I explained about Wubi and they didn't seem to mind.  But asked that I stop it from announcing itself as a server.  They said that they weren't getting any "bad messages" from my laptop.  I compared the services shown on both machines and the only differences is that the I am running SSH and SAMBA servers on the desktop.

Does anyone know how can I run these two servers without announcing to Active Directory?  Any other suggestions?

jimzat

---

### Post by ephro on 2007-11-20
I'm pretty sure that modifing /etc/samba/smb.conf will do what you need.

Edit the file and make sure that the following is set:


```

domain master = no
local master = no
preferred master = no

domain logons = no

time server = no

```


I believe it won't announce it is a server with these changes.



Ephro

---

### Post by jimzat on 2007-11-20
Thanks, I'll give that a try.

---

