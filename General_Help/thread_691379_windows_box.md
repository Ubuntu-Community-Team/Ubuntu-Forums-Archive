---
title: "windows box"
date: 2008-02-08
forum: General Help
---

### Post by maphco on 2008-02-08
What is a Windows Box?  and how do I install one on my ubuntu desktop?  I'm trying to get the Adobe & Macromedia 8 collections on my computer, but the tutorial I'm using says to copy files from my windows box.

[http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper](http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper)

[http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps](http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps)

---

### Post by kellemes on 2008-02-08
By this they mean you need to have a working Windows install somewhere.

---

### Post by hallbrian on 2008-02-08
just install wine on you ubuntu box (computer with ubuntu installed)

```
sudo apt-get install wine
```

Then download your windows apps (adobe, Dreamweaver) exe files, then install them.

```
sudo wine locationoffile/file.exe
```

---

### Post by kellemes on 2008-02-08
As a general advice.. When you're really depending on some app. like Dreamweaver you better get a "Windows box", either dual boot or installed on it's own rig. If possible obviously.

---

### Post by maphco on 2008-02-08
Alright, thanks for the advice.

---

