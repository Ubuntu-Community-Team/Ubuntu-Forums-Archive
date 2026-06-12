---
title: "Metadata Filesystem"
date: 2008-05-19
forum: General Help
---

### Post by Xyem on 2008-05-19
This is pretty much a simple request for information, I'm not having any joy finding what I want.

What I am looking for is a file-system that will allow me to tag files and then create folders which populate themselves with files that match certain tags dynamically.

Seeing as this is for a Linux server, I shall not ask if can be done as I am sure it could. My question is.. has it?

Any pointers would be greatly appreciated and explored. I have many things ( wallpapers and such ) that really need sorting :)

Edit: Really should try simple searches first.. [tagsistant]("http://www.tagsistant.net/") looks very promising ( even allowing me to "create" the folders from Samba maybe? :) )

---

### Post by Xyem on 2008-05-19
Upon further investigation, it appears that tagsistant presumes that every file you copy into its file-system will have a unique name.

Many of my images are numbered purely by number ( eg. 01.jpg 02.jpg ) because they are wallpaper gallery rips. If I understand correctly, tagsistant will bork this up if I try to move these files into it.

Are there any other recommendations for a tagging file-system similar to tagsistant? Or will I have to write one using libfuse-perl? :)

---

### Post by Xyem on 2008-06-25
Just a quick bump in case someone has something.

I would just like to tag files, is there nothing out there that does this?
Preferably something where if I search for 'Hellsing' & 'Image' it would let me open a directory that contained all files that matched those tags ( so I can slideshow it for example )

---

### Post by shaggy999 on 2009-07-12
Tagsistant is slowly getting better. The author talked on his forum about adding a unique ID to every file name when copying the file into the file system so that it won't have the problems of multiple files with the same name. It's not implemented yet, but he's thinking about it.

---

