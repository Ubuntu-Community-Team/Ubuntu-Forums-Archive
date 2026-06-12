---
title: "Setting SSH key-based certificate logon without knowing password"
date: 2016-02-21
forum: General Help
---

### Post by ofnuts on 2016-02-21
For automation purposes, I need to set a key-based login on an id for which I don't know the password.

- I have the password to a personal id on the same system
- I can sudo to assume that target id (but I enter the password of that personal id...)

On the system where the master scripts will be running, I can:
- create the  key with ssh-keygen
- initialize the personal id with the password with ssh-copy-id
- test that I can indeed login or pass remote commands for that personal id

Logging on the target system with the personal id
- I copy the .ssh/authorized_keys files to some public place
- I sudo to assume the target id
- I create a .ssh directory ("drwx------")
- I copy the authorized_keys in it (with "-rw-------")

Back to the master system, I cannot login to the target id, I'm still asked a password.

What could I be missing? (I also tried to add the known_hosts file from the personal id, without results)

---

### Post by HermanAB on 2016-02-22
Reboot into single user mode and then you can do what you want.

---

### Post by ofnuts on 2016-02-22
Actually just a matter of getting that id allowed to be logged on via SSH.

---

### Post by steeldriver on 2016-02-22
Have you increased the verbosity (ssh -vv or ssh -vvv)? It might be useful to know whether it is finding and rejecting the key or not finding it at all

---

