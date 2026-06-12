---
title: "Script to list the contents of a folder?"
date: 2007-01-15
forum: General Help
---

### Post by uncreative on 2007-01-15
Hi I have a folder containing various other folders with over 7500 pictures in there.  I need to write a script to list all the contents of the folder like this:

Example: Folder > Horse Images > pack1 > image.jpg image2.jpg

All the way through the 7500th result Example: Folder > Cat Images > 1.jpg 2.jpg

(1, Horse Images, /Folder/Horse Images/image.jpg)
(2, Horse Images, Folder/Horse Images/image2.jpg)

. . .

(7499, Cat Images, Folder/Cat Images/1.jpg)
(7500, Cat Images, Folder/Cat Images/2.jpg)

PS Some of the second folders (ie Horse Images) contain even more folders...

Any help? ](*,)

---

### Post by bodhi.zazen on 2007-01-15
ls -R /directory > picture.list

This should put the list in a file picture.list

Where do you want to go from there ?

---

### Post by uncreative on 2007-01-15
> **bodhi.zazen said:**
> ls -R /directory > picture.list

This should put the list in a file picture.list

Where do you want to go from there ?

Ah I see what you have done, very nice.

My ultimate goal it to get a huge mysql database of all these pictures with category, picture url

Thats why I asked how to do it like (1, category, url) etc

Thanks!

---

