---
title: "Konqueror Shell Script"
date: 2007-04-16
forum: General Help
---

### Post by disturbedite on 2007-04-16
here is what i would like to do:
i would like a shell script for use with konqueror's context menu (i'm on kubuntu feisty).  i want it to rename files of a certain type (cbr) to a different file type (rar).  i.e.  right click on a cbr file (i want this shell script to show up only with cbr files, obviously) --> Actions --> Rename to CBR.

here is my problem:
1.  i'm not sure how to write shell scripts even tho i am familiar with unix command line.
2.  i don't know how to get anything to show up in konqueror's context menu.  (i don't know where to put to the shell script in this case).

since this sounds fairly easy to me for ppl that are familiar with bash and shell scripting, i was hoping someone might already have a similar shell script that they could post here and i could just modify the file type, and then of course someone would have to point out where to put it...

i'd greatly appreciate any help.

---

### Post by Brucevdk on 2007-04-16
I don't use KDE so I haven't actually personally tried this. However, there's a tutorial which describes in depth exactly how to do this, it's called [ Creating Konqueror Service Menus]("http://developer.kde.org/documentation/tutorials/dot/servicemenus.html").

The tutorial is very easy to follow, so good luck.

---

### Post by disturbedite on 2007-04-16
thanks for the link, i will definitely read it, hopefully it will be helpful.

UPDATE:
i've read the article, i knew most of what it had to say, but it a helpful resource.  here is what i have so far:

[Desktop Entry]
ServiceTypes=application/Comic Book Archive
Actions=rename

[Desktop Action rename]
Name=Rename CBR to RAR
Exec= mv %U

i assume that i have to use mv to rename file(s) (extensions), is that correct?  i'm not sure cuz mv can't rename files of a certain type afaik.  (it doesn't support wildcards before file extensions).

---

### Post by disturbedite on 2007-04-16
on a separate, but related note...

i created a shell script to compress rar files with the same options i always use.  i think its correct, but it doesn't create any rar files and i can confirm that rar doesn't run when the script is executed...

[Desktop Entry]
ServiceTypes=all/all
Actions=compress

[Desktop Action compress]
Name=Compress as RAR
Icon=/usr/share/icons/winrarcrystal
Exec=/usr/bin/rar a -s -m0g -ep -rr10 U%

---

