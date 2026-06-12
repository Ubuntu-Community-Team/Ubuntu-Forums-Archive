---
title: "SSH - Public Key being used when not needed"
date: 2007-04-14
forum: General Help
---

### Post by ninocass on 2007-04-14
I have my local server set up with Public Key auth to make it a bit more secure.

On my laptop i have the key in my ~/.ssh/ folder and everything works great.

However when i join SSH into another host for some reason the PublicKey is being used.  I can still join the other host i just need to enter the password for the key which is a bit of a pain when the other host doesn't need it 

cheers

Nino

---

### Post by kidders on 2007-04-15
Hi there,

This is probably because SSH naturally tries key-based authentication first. You could try setting the **PubkeyAuthentication** option to "no" on a per-host basis (see **ssh**'s & **ssh_config**'s man pages). That might work.

---

