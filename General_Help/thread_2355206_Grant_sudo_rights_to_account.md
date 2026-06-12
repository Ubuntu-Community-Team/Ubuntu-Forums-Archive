---
title: "Grant sudo rights to account"
date: 2017-03-10
forum: General Help
---

### Post by jimmy2017 on 2017-03-10
Hi,

I've an issue when trying to give sudo rights to a existing user account, I'm logged in with the root account and not using GUI.
Try to do adduser accountname sudo

This gives me the error 
gpasswd: cannot lock /etc/group; try again later
adduser: `/usr/bin/gpasswd -a (accountname) sudo' returned error code 1. Exiting. 

Even by trying to change the existing account password via command passwd accountname ; it gives me the following error:
Passwd: Authentication token manipulation error
Passwd: password unchanged

Does anyone know why I'm unable to change this as I'm logged in with a root account?

---

### Post by steeldriver on 2017-03-10
"logged in with the root account" how, exactly?

Those types of errors often indicate that the filesystem you're trying to write to is mounted read-only

---

