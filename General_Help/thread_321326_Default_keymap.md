---
title: "Default keymap"
date: 2006-12-18
forum: General Help
---

### Post by Blippe on 2006-12-18
To start off: I am NOT looking for the keymap in gnome, nor the keymap in dapper or older, nor loading a keymap in the startup script, after the one active in edgy. 

I got two screwy keyboards, and want to make them work for me. Before dapper it was easy, i just changed the /etc/console/boottime.kmap.gz to my hearts content, but in edgy no such luck. I've been tampering with /etc/console-setup/boottime.kmap.gz, trying to read the /etc/init.d and /etc/rcX.d directrories, trying to figure out what is what, but no dice. 

Where is the edgy startup-script for the keyboard?

---

### Post by cilynx on 2006-12-20
The official *buntu solution used to be
```

sudo dpkg-reconfigure console-data

```
but that's been superceeded by
```

sudo dpkg-reconfigure console-setup

```
console-data is still around, but updating the configurating won't fix anything anymore.

---

