---
title: "How to extract .ace files?"
date: 2005-05-25
forum: General Help
---

### Post by Nissemand on 2005-05-25
The only thing related to Ubuntu names ace, seems to be some C/C++ optimize archive or something... Where can i get .ace package support?

---

### Post by f.prisson on 2005-05-25
There is a program called unace, but I don't know whether it's available through apt (not in front of my linux box right now)

---

### Post by Nissemand on 2005-05-25
Great :D It works through apt (:

---

### Post by daller on 2006-01-01
I got this:

madsen@ubuntu:~$ unace e /home/madsen/Desktop/SuperFrog.ace
UNACE v1.2    public version

Processing archive: /home/madsen/Desktop/SuperFrog.ace

Authenticity Verification:
created on 22.11.2005 by *UNREGISTERED VERSION*


SuperFrog
    Could not create directory.

 Analyzing
File compressed with unknown method. Decompression not possible.

Error occurred



Any ideas?

---

### Post by daller on 2006-01-01
I installed a newer version of unace:

[ftp://ftp.nerim.net/debian-marillat/pool/main/u/unace/unace_2.20-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/u/unace/unace_2.20-0.0_i386.deb)

That solved the problem!

---

### Post by muted on 2006-01-04
Great Thanks!

Denmark represent :)

---

### Post by muted on 2006-01-04
[QUOTE=daller]I installed a newer version of unace:

[ftp://ftp.nerim.net/debian-marillat/pool/main/u/unace/unace_2.20-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/u/unace/unace_2.20-0.0_i386.deb)

That solved the problem![/QUOTE]
Jeg l&#230;ser p&#229; KU fysik med en fyr som hedder Mads S&#248;rensen... Fra Frederecia!

Kender du ham?

---

### Post by chikko on 2007-02-24
here's an updated link:

[ftp://ftp.nerim.net/debian/pool/main/u/unace/unace_1.2b-4_i386.deb](ftp://ftp.nerim.net/debian/pool/main/u/unace/unace_1.2b-4_i386.deb)

:)

---

### Post by bluej100 on 2007-02-27
unace-nonfree in feisty universe utilities solved this for me. (Age of Empires II: Conquerors, here we come. :D )

---

### Post by bharadwaj on 2008-03-30
I am glad there wasn't any need for updated .deb in gusty gibbon :)

---

