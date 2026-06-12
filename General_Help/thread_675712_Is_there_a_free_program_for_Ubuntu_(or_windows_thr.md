---
title: "Is there a free program for Ubuntu (or windows through wine) that turns pdf to jpegs?"
date: 2008-01-23
forum: General Help
---

### Post by s3a on 2008-01-23
The title says it...

Thanks in advance!

---

### Post by OlleyK on 2008-01-23
Gimp. You can install it through synaptic.

---

### Post by Casual Fan on 2008-01-23
GIMP comes installed in Ubuntu. Look under Applications>Graphics.

Open your .pdf file in GIMP and then do file>save as>filename.jpg

---

### Post by vanadium on 2008-01-23
The command line is far quicker for this kind of tasks. With imagemagicks convert:

convert my.pdf my.jpg

and if you have thousand of files in one directory:

for f in *.pdf ; do convert "$f" "$f.jpg" ; done

or zillions of files scattered all over you myriads of disks

find / -iname '*.pdf' -execdir convert {} {}.jpg \;

---

### Post by alvinucsk on 2008-01-23
its simple... u can edit it through GIMP.... u just simple rename it to .jpeg(i.e. from picture.png - picture.jpeg)... :)

---

