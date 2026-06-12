---
title: "Where did my kernel go?"
date: 2005-10-27
forum: General Help
---

### Post by N'Jal on 2005-10-27
I need to recompile my kernel under GCC 4 since the kernel i am running was compiled under GCC3.X, but when i goto /usr/src/linux, breezy tells me there's nothing there, so thinking it has a version number after it i cd to /usr/src and type ls to find there is only an RPM directory in there. 

Where has the kernel been moved to and can i put it back into /usr/src/linux?
And yes i really do need to recompile, i don't need to enable anything, i just need to recompile it under GCC4.

---

### Post by TimonVO on 2005-10-27
Try sudo apt-get install linux-headers-2.6.12-9-386 linux-386.
You should have them then. I guess.

---

### Post by N'Jal on 2005-10-27
Ah i should have said that machine does not have a net connection, however, this one does, so i could simply download the header.deb from the software section of the site and install via dpkg and i should have them?

---

