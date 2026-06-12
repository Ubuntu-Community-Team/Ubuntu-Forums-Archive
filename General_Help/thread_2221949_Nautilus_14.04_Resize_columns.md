---
title: "Nautilus 14.04 Resize columns"
date: 2014-05-04
forum: General Help
---

### Post by caver12 on 2014-05-04
How do I resize the columns in Nautilus 14.04?
I have tried setting the zoom under prefences to 33%, the lowest setting, but there was no change. I could find no option to chage the column size. Also tried putting my cursor on the column seperator(?) and drag it, both as user and root, and it wont do anything.

---

### Post by Vaphell on 2014-05-04
looks like all the columns except the first one have fixed sizes, which is kinda ridiculous because if you right click the header and enable a bunch of other columns, you literally lose the ability to see anything in the cannibalized main column.
That's gnome devs in their full glory for you. Forking of the file manager can't happen soon enough.

---

### Post by mcduck on 2014-05-04
They don't have fixed sizes (only minimum sizes), but the way the resizing works is not quite as intuitive as it could be. 

Basically,  you can only resize a filed when it's next to a filed that has extra space. And in some situations the resizing works by dragging to the opposite direction than where the field with extra space is (Actually it's resizing both two fields, to both directions, which is probably why it feels a bit strange especially if one of them happens to be the first or last filed and therefore suddenly doesn't resize both ways)

Anyway, if you have a large "Name" field and everything else is packed to minimum space, the only field border you can drag around at that point is the one between Name and the next one. Once you've moved that a bit, the rest of the fields should now have more extra space and you can continue tweaking their sizes.

---

### Post by caver12 on 2014-05-04
Basically,  you can only resize a filed when it's next to a filed that has extra space. And in some situations the resizing works by dragging to the opposite direction than where the field with extra space is (Actually it's resizing both two fields, to both directions, which is probably why it feels a bit strange especially if one of them happens to be the first or last filed and therefore suddenly doesn't resize both ways)

Anyway, if you have a large "Name" field and everything else is packed to minimum space, the only field border you can drag around at that point is the one between Name and the next one. Once you've moved that a bit, the rest of the fields should now have more extra space and you can continue tweaking their sizes.[/QUOTE]

 Thanks that worked fine.

---

### Post by prantor.bora@gmail.com on 2014-06-05
This is very annoying, I should be able to adjust how much of a column width I want to see. My file names are long and it does not allow me to adjust the column width where I can see the full file name. It taking space to show full directory path (which is not as important as the file name) and not allowing me to resize the filename column.

---

### Post by mc4man on 2014-06-05
> **prantor.bora@gmail.com said:**
> This is very annoying, I should be able to adjust how much of a column width I want to see. My file names are long and it does not allow me to adjust the column width where I can see the full file name. It taking space to show full directory path (which is not as important as the file name) and not allowing me to resize the filename column.
Well it is what it is in 3.10 & while there may be some changes it not likely to be applied to nautilus 3.10
So if using maybe remove location from the displayed columns, not really that useful in nautilus when browsing as the location is shown in pathbar or in properties of any file

---

### Post by marava1 on 2014-07-14
Try to find documents with similar names in more than one folder and read the name like so ....odt, ....doc, ...odf.
Funny and useful, isn'it?
It is what actually does Nautilus (sorry - now is called "File"- to increase the confusion) if you have long name of folders and you need to know the position. I often need to know tne position

---

### Post by vanadium on 2014-07-14
(One of the) bug reports here: [https://bugzilla.gnome.org/show_bug.cgi?id=693459](https://bugzilla.gnome.org/show_bug.cgi?id=693459)
Apparently, gnome software does not anymore undergo useability testing.

---

### Post by Jim_Taller on 2014-08-20
So yes, I tried to google: " Cant resize columns in File" and you would not believe what I got. Count 1,930,000 hits.
Note to developers. Since we are in the age of web wher we search by words, you need to name things differently from other existing words.
Fo example searching for Apple, will tell you about local farm market.
If you like the word File, you can still rename it as:  FileMgr or FilezMgr or many other things, but not File and not File Manager and not even FileManager because google will report hist for "file manager".
Anyway the problem is still with us in Ubuntu 14.04.
The solution by mcduck above did not work for me. Can't make my path-column smaller even though it has plenty of space.

---

### Post by gebbione on 2014-09-06
> **vanadium said:**
> (One of the) bug reports here: [https://bugzilla.gnome.org/show_bug.cgi?id=693459](https://bugzilla.gnome.org/show_bug.cgi?id=693459)
Apparently, gnome software does not anymore undergo useability testing.

The current functionality is really bad (also dont see the point of restricting resizing) and who was the UX dev that made this happen? These are the little things that give a reason for other platforms to exist and have more users than linux. :mad::mad::mad:

---

### Post by mat14 on 2014-09-27
Have the same annoying bug, so I installed Thunar - but it hasn't the search function easily at hand. Also File or Nautilus is the standard file-browser that opens when i insert a Usb, so I would have to open Thunar separately. But I found a way to expand the file-name column: I disable the other columns by right-click temporarily until the column is large enough. But I must say 14.4 is much slower (almost as slow on boot as MS Waitows 7)  and more buggy than the 12 I updated from - probably I'll reinstall 12. where is the advantage using 14?

---

