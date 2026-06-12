---
title: "Trouble reading file from a dvd iso"
date: 2007-09-18
forum: General Help
---

### Post by aquavitae on 2007-09-18
Im having a really weird problem with a dvd iso image I have.  Heres what happens.

I mounted the iso using mount -o loop.  Then I tried to read a plain text file on it (using 'cat' and 'dd'), but I get "Input/Output error".  dd also shows 0 bytes read.  As a check, I tried mounting the image in windows, It mounts fine, but I still get an IO error if I try to read a file.  Naturally, I assumed the iso was corrupt, but then I tried it on three other computers, none of which had any problems opening the data.  The other catch is that I only have the problems with some of the files on the iso, the others open without problems.

Does anyone have any ideas why this would happen?  Its not a software thing cos I have the same problem in windows and linux, and the iso is ok cos it will open on another pc.

---

