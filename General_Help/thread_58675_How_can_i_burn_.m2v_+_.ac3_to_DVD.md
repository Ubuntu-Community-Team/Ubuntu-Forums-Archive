---
title: "How can i burn .m2v + .ac3 to DVD?"
date: 2005-08-21
forum: General Help
---

### Post by drews_blunted on 2005-08-21
I would like to be able to succesfully burn a DVD from both a .m2v and a .ac3 file

The file is names are: 02x02.ac3 02x02.avi x02.m2v

I went ahead and converted the .avi to create the 2 .m2v & .ac3 files.

Now I am stuck. I do not know what to do to get these files into a vob format or somehing that would easily play on a DVD player. If anyone could help guide me in the right direction it would be great.

---

### Post by chiefofthejojos on 2005-08-28
I suggest using the "tovid" scripts.  I've been using tovid very happily for quite some time now.

tovid -dvd -in <filename>.avi -out <filename without extension>
makexml <filename>.mpg <foldername for dvd files>
dvdauthor -x <filename>.xml
mkisofs -dvd-video -udf -o <filename>.iso <foldername with dvd files>

---

