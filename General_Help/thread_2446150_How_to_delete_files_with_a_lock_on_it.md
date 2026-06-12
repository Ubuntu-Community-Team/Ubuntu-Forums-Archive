---
title: "How to delete files with a lock on it"
date: 2020-06-25
forum: General Help
---

### Post by geovino on 2020-06-25
How to delete files with a lock on it?

[ATTACH=CONFIG]286318[/ATTACH]

---

### Post by ActionParsnip on 2020-06-25
Its owned by root, you probably extracted the files with a command prefixed by sudo so the files created are root owned. You can also use:
```

sudo chown -R $USER $HOME/ovpn_tcp/*
sudo chown -R $USER $HOME/ovpn_udp/*

```
To change the ownership to your user, then do what you need with them.

---

### Post by VMC on 2020-06-25
Those are folders. Are you sure you want to delete them? Have you tried:
```
sudo rm -r <foldername>
```

---

### Post by ActionParsnip on 2020-06-25
Either extracted using sudo or moved/copied as root/using sudo

---

### Post by geovino on 2020-06-25
Thank you

---

