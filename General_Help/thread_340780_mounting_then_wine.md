---
title: "mounting then wine?"
date: 2007-01-17
forum: General Help
---

### Post by haxer on 2007-01-17
Hello i downloaded an .iso file and its an .exe iso "the iso contanes an .exe file" how to mount it then open it up and install in wine? ;) :-k

---

### Post by taurus on 2007-01-17
```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop **filename.iso** /media/iso
```

---

### Post by bodhi.zazen on 2007-01-17
then:

```
wine /media/iso/program.exe
```

---

### Post by haxer on 2007-01-17
Thx:)

---

### Post by haxer on 2007-01-17
But now i have this problem... I use wine then bla bla SETUP.exe is the thing i want to run then it starts then it stops why? :-k its a program for driverslicence in sweden .. i bought my first car yesterday "ford origon 1.6 gl -91" woho and i have this keyring with "puss y waggon" :) like in kill bill 8) 8) [http://www.coolstuff.se/images/produkter/508.jpg](http://www.coolstuff.se/images/produkter/508.jpg)

---

### Post by taurus on 2007-01-17
Not all Windows programs run or install with wine.  ;)

---

### Post by meng on 2007-01-17
The program may not work with wine. Wine is not a perfect replacement for WIndows.

---

### Post by haxer on 2007-01-17
Hmm.. not good at all.. what should i do then? I want to take drivers licence and thats expensive in sweden minimum 2000$ 14000swedish kr so i wanted to read some at home to make it cost less :(

---

