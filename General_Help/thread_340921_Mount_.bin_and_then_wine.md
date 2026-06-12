---
title: "Mount .bin and then wine?"
date: 2007-01-17
forum: General Help
---

### Post by haxer on 2007-01-17
Hello i wounder if its possible to mount an .bin file and start it in wine :) and please how to do it :) :-k

---

### Post by taurus on 2007-01-17
You need to use bin2iso to convert your bin/cue to .iso first.  Then mount it like I already showed you before.

---

### Post by haxer on 2007-01-17
is the name of the app bin2iso? :-k

---

### Post by taurus on 2007-01-17
[http://wiki.linuxquestions.org/wiki/CD_Image_Conversion#bin2iso](http://wiki.linuxquestions.org/wiki/CD_Image_Conversion#bin2iso)

---

### Post by haxer on 2007-01-17
cant download it :( ?

---

### Post by taurus on 2007-01-17
If you click the bin2iso, it will show you the actual C program for it.  From a terminal, type

```
nano -w bin2iso.c
```
Now, use the mouse and cut the text from your browser (the actual program) and paste it to the terminal with nano running.

Save it and then run

```
gcc -o bin2iso bin2iso.c
sudo cp bin2iso /usr/bin
```
Now, you can use it to convert your bin/cue to iso...

---

### Post by haxer on 2007-01-17
the gcc command couldnt be found it says?

---

### Post by taurus on 2007-01-17
```
sudo aptitude update
sudo aptitude install build-essential
gcc -o bin2iso bin2iso.c
sudo cp bin2iso /usr/bin
```

---

### Post by haxer on 2007-01-17
Thx learned me something new today :KS and how to use? np i worked it out :)

---

### Post by taurus on 2007-01-17
```
bin2iso **filename.bin**
```

---

### Post by haxer on 2007-01-17
Noticed that and i also noticed that the program i was trying to install didnt work with wine either :( so today in 10 hours im going to driving school :(

---

### Post by taurus on 2007-01-17
Again, not all Windows programs run with wine!  You can also try to CrossOver Office by codeweavers, [http://www.codeweavers.com/](http://www.codeweavers.com/).

---

