---
title: "Changing source.list"
date: 2007-03-04
forum: General Help
---

### Post by Deviltongue on 2007-03-04
I'm trying to edit the source.list directory but it said I don't have permissions to edit it. I then went into the properties of the file to change it to "Read and Write" but it said I can't because I'm not root. so THEN I signed out and tried to sign in as root but it said "system administrator can't sign in from here" or something! WHAT'S GOING ON?!?!?

---

### Post by taurus on 2007-03-04
Applications -> Accessories -> Terminal
```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

