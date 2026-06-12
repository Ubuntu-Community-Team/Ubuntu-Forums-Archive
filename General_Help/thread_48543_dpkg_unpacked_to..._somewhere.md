---
title: "dpkg unpacked to... somewhere?"
date: 2005-07-12
forum: General Help
---

### Post by Zifnab on 2005-07-12
I downloaded a game from Happypenguin.com called Glest, a 3D RTS. It had a .deb, so I thought, "Sweet, no messy make install that I'll never be able to get rid of."  

So I did (as root):
```
zifbox install # dpkg -i glest-data_1.0.10_all.deb
Selecting previously deselected package glest-data.
(Reading database ... 66717 files and directories currently installed.)
Unpacking glest-data (from glest-data_1.0.10_all.deb) ...
Setting up glest-data (1.0.10) ...
```
That's all it says, but I can't find any actual program installed anywhere. Thankfully I was able to remove it with:```
dpkg -r glest-data
```
Can't find a man page, binary, nothing. Anyone know a way of sniffing down the bugger?

Thx

---

### Post by Xian on 2005-07-12
I guess you tried running it from a term or doing a locate command?
```
$ glest
$ locate glest
```

---

### Post by lakcaj on 2005-07-12
dpkg -L glest-data | grep bin

---

