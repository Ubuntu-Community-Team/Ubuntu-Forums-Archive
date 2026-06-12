---
title: "how do I use ufraw without gimp?"
date: 2005-07-08
forum: General Help
---

### Post by jasplund on 2005-07-08
I want to use ufraw and then saving the pic to tiff without using gimp. The thing is that I want to open the tiff in cinepaint so that I can change levels and curves with 16 bit.

---

### Post by coolclassic on 2005-07-08
As I understand ufraw is writtten as a gimp plugin and wouldn't work by itself.
  
Using ufraw and saving as tiff has very little gimp input:
you open the file in gimp which launches the ufraw process this is then loaded into gimp where you save as tiff. No further gimp input needed.

---

### Post by jasplund on 2005-07-08
It says here [http://ufraw.sourceforge.net/](http://ufraw.sourceforge.net/) that it works on it own. I guess the package in the repositories is only a gimp plug-in.

It's no big deal though. The only thing is that I have to convert it to 8 bit when I save it in gimp

---

### Post by coolclassic on 2005-07-08
Just follow the instructions on the web sight you gave.I will be trying it myself soon.

---

### Post by jasplund on 2005-07-08
[QUOTE=coolclassic]Just follow the instructions on the web sight you gave.I will be trying it myself soon.[/QUOTE]

Sorry I forgot to mention that I tried that already, it doesn't work

---

### Post by Totzo on 2005-09-05
try using the cvs version (you have to compile it from source and use an earlier version of libtiff (3.7.1 I think) then you will get exif support. I have a D100 and it works, I think you even get auto orientation with the D70 files. Good luck!

---

