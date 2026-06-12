---
title: "Can not Play VCD by vlc"
date: 2013-08-14
forum: General Help
---

### Post by itsankur on 2013-08-14
I am using UBUNTU 12.04 LTS and installed VLC media player but can't play VCD with it.
When I open the **.dat** file from mpegav directory, it gives I/O error.
Choosing SVCD/VCD from Media/Open Disc opens the poster of the movie which stays for about 1 min. then does nothing.
I have also installed vcdimager but it does not help.

Please help...
Regards
-Ankur

---

### Post by GwL3eNC on 2013-08-14
Hi,

some time ago  this question was already asked. It's a known problem, i don't know if it's an ubuntu or
a vlc error. I believe a dat file is just a renamed mpg file. You can try copy it to your hd an rename it.
Also i heard that the xine player can play them without something to do. I hope thats correct and
takes you further.

---

### Post by itsankur on 2013-08-14
I can not copy the file on my HDD. Again I/O error!!

---

### Post by GwL3eNC on 2013-08-14
Crazy, too bad that i got no VCD/SVCD here to test that on my own. How do you try to copy the file?
Have you tried the dd command. I'm not well experienced with that but it must be possible to copy
that file somehow.

dd if=SOURCEFILE of=DESTINATION 

or something in that way. you can get help about dd if you type 

man dd

---

