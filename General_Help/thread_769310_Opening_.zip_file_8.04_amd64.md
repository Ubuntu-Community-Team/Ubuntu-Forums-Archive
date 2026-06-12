---
title: "Opening .zip file 8.04 amd64"
date: 2008-04-26
forum: General Help
---

### Post by Deten on 2008-04-26
I got into the Age of Conan beta test, and was trying to see if I can get it running through wine.  

The download is zipped with *.zip and when I try to open it with archive manager I get this error.

> Archive:  /home/deten/Desktop/AgeOfConan_FilePlanet.zip   13527773965   31
warning [/home/deten/Desktop/AgeOfConan_FilePlanet.zip]:  9232804758 extra bytes at beginning or within zipfile
  (attempting to process anyway)
error [/home/deten/Desktop/Desktop/AgeOfConan_FilePlanet.zip]:  start of central directory not found;
  zipfile corrupt.
  (please check that you have transferred or created the zipfile in the
  appropriate BINARY mode and that you have compiled UnZip properly)

So I re downloaded the file (took another 24 hours) and got the EXACT same error.

I also tried opening it with wine, which didnt load.

This is a fresh 8.04 install, could I be missing a zip support application or is it just not working in linux for some reason?

Thanks for the help, ill be checking this so if you need more info just post.

---

### Post by Deten on 2008-04-26
I got a fix for it, though tis not the preferred method.

I installed winRAR through wine, and opened the zip file with winrar, that worked.

---

### Post by _sAm_ on 2008-04-26
> **Deten said:**
> I got a fix for it, though tis not the preferred method.

I installed winRAR through wine, and opened the zip file with winrar, that worked.

You dont need winRAR, just install the package unrar from Synaptic. Then you can use FileRoller(archive manager) for rar files.

---

### Post by joshsmith on 2008-04-26
the package unrar for rars, unzip for zips. install in synaptic,

then use right click>extract

---

### Post by myname on 2008-05-01
I'd like to know if this works, as I am running into the same problem.  I finally resorted to downloading on my work system (windows vista), do all the stuff.

Though, now when I connect to my windows box from my linux (samba client is installed and I can connect), I start to copy the files, then I get popups saying that it can't copy file 10.dat, then 11.dat, etc.

are us Linux folks screwed?

--k

---

### Post by joshsmith on 2008-05-01
it does work just try it. try it before asking
synaptic, install package unzip
right click>extract

---

### Post by myname on 2008-05-01
I did try, twice, and both times got the message saying it was a corrupt download.  

I may just wait the 2 - 3 weeks when preorder people can play. as I'm not going to spend more time downloading the client *again*.

--k

---

