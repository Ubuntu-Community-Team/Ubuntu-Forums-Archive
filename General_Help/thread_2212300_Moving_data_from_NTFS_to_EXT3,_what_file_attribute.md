---
title: "Moving data from NTFS to EXT3, what file attributes will be lost?"
date: 2014-03-20
forum: General Help
---

### Post by cable_guy on 2014-03-20
Hi all,

I have a rare opportunity to grab all of the files from my NTFS storage drive and keep it temporarily somewhere else, so I want to reformat my storage to EXT3 however I am worried when I move my data from NTFS to EXT3 that I will lose certain file attributes, e.g. date modified, tags, etc.  Does anyone know what definitively is lost when copying something from NTFS to EXT3?

To be clear my plan is

1) Copy all my data from my old NTFS drive to my new EXT3 drive
2) Reformat the old NTFS drive as EXT3

---

### Post by sgage on 2014-03-20
I just copied a file from my NTFS partition to my EXT4 partition, and back again, and the date modified was not changed. Permissions will be set depending on how you mounted the NTFS partition (what options you used).

---

### Post by ajgreeny on 2014-03-20
From man cp:-
```
--preserve[=ATTR_LIST]
              preserve  the  specified  attributes  (default:  mode,ownership,timestamps),  if  possible   additional
              attributes: context, links, xattr, all
```
so you could use **cp --preserve=all** to add an extra layer of hope, but any problems are most likely to come from ntfs not enabling all linux file attributes.

---

### Post by cable_guy on 2014-03-20
thanks for the responses, I just attempted the same test as you with --preserve=all and it managed to retain the data I wanted (the EXIF tags on photos) so all is good, thanks again :)

---

### Post by Impavidus on 2014-03-21
The exif tags of photos are stored inside the image file, not as part of the file system metadata, so they would have been kept automatically.

---

