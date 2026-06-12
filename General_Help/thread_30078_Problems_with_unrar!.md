---
title: "Problems with unrar!"
date: 2005-04-27
forum: General Help
---

### Post by Biffy on 2005-04-27
```
larsson@ubuntu:~/dc $ unrar -x RnR.rar 

unrar 0.0.1           Copyright (c) 2004 Ben Asselstine 


Extracting from /home/larsson/dc/RnR.rar 

Extracting  RnR/alld40.dll                                            Failed 
Extracting  RnR/alleg40.dll                                           Failed 
Extracting  RnR/allp40.dll                                            Failed 
Extracting  RnR/anim.dat                                              Failed 
Extracting  RnR/Boffen.pro                                            Failed 
Extracting  RnR/chars.ini                                             Failed 
Extracting  RnR/entities.dat                                          Failed 
Extracting  RnR/gfx.dat                                               Failed 
Extracting  RnR/Maknys.pro                                            Failed 
Extracting  RnR/matti2.ini                                            Failed 
Extracting  RnR/matti2.map                                            Failed 
Extracting  RnR/matti3.ini                                            Failed 
Extracting  RnR/matti3.map                                            Failed 
Extracting  RnR/menu.dat                                              Failed 
Extracting  RnR/misc.dat                                              Failed 
Extracting  RnR/MSVCR70.dll                                           Failed 
Extracting  RnR/msvcrt.dll                                            Failed 
Extracting  RnR/Msvcrtd.dll                                           Failed 
Extracting  RnR/Nee.pro                                               Failed 
Extracting  RnR/rocknrollator.exe                                     Failed 
20 Failed 
larsson@ubuntu:~/dc $
```

As you can see, it fails to extract the files. I am sure that there is nothing wrong with the file.

Help!

---

### Post by Burgundavia on 2005-04-27
Do you have unrar-nonfree?

Corey

---

### Post by syltty on 2005-04-27
looks like you have a really old version of unrar

my unrar gives version 3.30:

$ unrar x *.rar

UNRAR 3.30 freeware      Copyright (c) 1993-2004 Eugene Roshal


Extracting from tcm-tlw210.rar
.
.
.

---

### Post by fng on 2005-04-27
you can also use rar to unrar :
```
rar x archive.rar 
```

I also have the same problems with unrar, but rar just works

---

### Post by bored2k on 2005-04-27
[QUOTE=fng]you can also use rar to unrar :
```
rar x archive.rar 
```

I also have the same problems with unrar, but rar just works[/QUOTE]
 I use WinRAR through Crossover Office Pro 4.2. I'm sure it works on wine.

---

### Post by Biffy on 2005-04-28
I downloaded a new version of Unrar and it works.

But the program is not installed. I cant compile and thereafter install it on my system. Anyone knows if there is a deb package for it?

---

### Post by shakin on 2005-04-28
[QUOTE=Biffy]I downloaded a new version of Unrar and it works.

But the program is not installed. I cant compile and thereafter install it on my system. Anyone knows if there is a deb package for it?[/QUOTE]

I think it's in the multiverse repository under the name, as Burgundavia said, unrar-nonfree.

---

### Post by Biffy on 2005-05-01
[QUOTE=shakin]I think it's in the multiverse repository under the name, as Burgundavia said, unrar-nonfree.[/QUOTE]

What rep should i add to get multiverse? I only got "officially supported" and "Universe" .

---

