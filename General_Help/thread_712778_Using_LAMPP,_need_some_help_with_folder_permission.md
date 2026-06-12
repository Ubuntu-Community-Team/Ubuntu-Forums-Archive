---
title: "Using LAMPP, need some help with folder permissions"
date: 2008-03-02
forum: General Help
---

### Post by SandmanXC on 2008-03-02
Hello. I have managed  to install and start LAMPP using sudo in front of every command. But that is really annoying when trying to develop a site. I tried giving permissions for that folder:

```
sudo chmod +x /opt/lampp/htdocs --recursive
sudo chmod +r /opt/lampp/htdocs --recursive
sudo chmod +w /opt/lampp/htdocs --recursive
```

but all it did was let me see the contents in nautilus, without allowing me to write there. 

The only thing that worked was 

```
gksudo nautilus
```

but that is still rather unpleasant. Any suggestions on how to get all the permissions?

---

### Post by Runn3r.cze on 2008-03-02
try this
```
sudo chmod -R 745 /opt/lampp/htdocs
```
i have the same permissiuns and works fine

---

### Post by SandmanXC on 2008-03-02
Thanks, but i still can't paste files there.

---

