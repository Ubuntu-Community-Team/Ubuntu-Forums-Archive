---
title: "Adding a launcher to pannel!"
date: 2005-07-08
forum: General Help
---

### Post by Shinitenshi on 2005-07-08
Ok i installed ie using wine and when i try to add somthing to my top panel were firefox icon is located i browse to the executible but when i click it it doesnt execute? 

but gives an error saying there isnt such folder! odd thing is that i browsed to it...

home/shinitenshi/.wine/fake_windows/Program Files/Internet Explorer/IEXPLORE.EXE

is it like terminal where u have to put the \ on every pace? cuz when i do a:

home/shinitenshi/.wine/fake_windows/Program\ Files/Internet\ Explorer/IEXPLORE.EXE

it wont give me the the original error but wont run ie

Yes ie works because i can execute it by clicking it on ie dir >.<

---

### Post by sethmahoney on 2005-07-08
Not sure, but try changing the link to:

```
wine "home/shinitenshi/.wine/fake_windows/Program Files/Internet Explorer/IEXPLORE.EXE"
```

Make sure to use the quotation marks.

---

### Post by Shinitenshi on 2005-07-08
[QUOTE=sethmahoney]Not sure, but try changing the link to:

```
wine "home/shinitenshi/.wine/fake_windows/Program Files/Internet Explorer/IEXPLORE.EXE"
```

Make sure to use the quotation marks.[/QUOTE]


Nope that dint work >.< hmmmm

---

### Post by jwalch on 2005-10-25
I suspected that Linux does not like the MS syntax for naming folders, ie "Program Files" for ex., with the space. So I put my MS appöication directly under "drive_c" and could launch the wine <application> from the panel.

---

