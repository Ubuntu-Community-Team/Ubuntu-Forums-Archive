---
title: "convert an .rar to .iso"
date: 2006-12-05
forum: General Help
---

### Post by kelxso on 2006-12-05
how do i convert a .rar file to a .iso 
please help

---

### Post by mgmiller on 2006-12-05
Basically, you will need to unrar the rar file and then create the iso out of the resulting folder.

You can check the edgy starter guide.  It's here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

Look up how to install rar and unrar and read about them.  

The command to created the iso from the unrared folder (also taken from the edgy starter guide)  is:

```
mkisofs -r -o file.iso /location_of_folder/
```

---

### Post by CatKiller on 2006-12-06
Are you sure that you have a .rar file, or is it just that WinRAR has stuck its own icon on the .iso file?

---

### Post by kelxso on 2006-12-06
i dont have winrar but i know thats a way to convert it. and im working on dapper drake :-D

---

### Post by CatKiller on 2006-12-06
> **kelxso said:**
> i dont have winrar but i know thats a way to convert it. and im working on dapper drake :-D

We've just had so many posts lately from people still using XP or whatever who are convinced that they've downloaded a .rar file, rather than the .iso that they both have and need.

But I think that if you enable the Universe repository and then **sudo aptitude install rar**, then file-roller ("Archive Manager") will handle them both. Whether it will convert between them is another matter, of course.

---

### Post by kelxso on 2006-12-06
to be completely spacific ive downloaded an iso file in a .rar form i want to convert it to burn the iso image to a cd.

---

### Post by Henry Rayker on 2006-12-06
The problem is, an iso is an image, a rar is a compressed archive. These aren't the same...you think you're asking something like, "I'd like to turn this beef into ground beef" but instead you're asking, "I'd like to turn this beef into a balloon".

The rar probably has the iso inside it. If not, tell us where you got it so someone can investigate.

---

### Post by kelxso on 2006-12-06
should i just open the rar file with the archive manager:-k

---

### Post by Henry Rayker on 2006-12-06
Yep. Just open the rar with archive manager. There will (probably) be a .iso file in there. If not, you will need to make an iso from the directory(ies)/files inside.

---

### Post by kelxso on 2006-12-07
archive type is not supported by archive manager . is there anything else i can try :-k

---

### Post by CatKiller on 2006-12-07
> **kelxso said:**
> archive type is not supported by archive manager . is there anything else i can try :-k

...

> **CatKiller said:**
> enable the Universe repository and then **sudo aptitude install rar**

---

### Post by hambudge on 2007-09-12
Are you sure your rar file was complete? - I've done that before

---

