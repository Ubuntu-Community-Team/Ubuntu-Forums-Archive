---
title: "Help Installing Software"
date: 2008-04-03
forum: General Help
---

### Post by nedstrange on 2008-04-03
OK, I am away from home on a trip and trying to get my DVD to play back so i am trying to get the restricted drivers installed but i keep needing the install disk is there away around this or am i stuck until i get the disk 

THx

---

### Post by nedstrange on 2008-04-03
o for got to say that i am using Gusty 7.10

---

### Post by oldos2er on 2008-04-03
Go to System, Administration, Software Sources, uncheck the box next to "Cdrom with Ubuntu 7.10 Gutsy." Make sure all the other boxes are checked. 

 Click the 'Third-Party Software' tab, and add the following lines one at a time:

[http://packages,medibuntu.org/](http://packages,medibuntu.org/) gutsy free non-free

[http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free (Source Code)

 Close Software Sources, and in a terminal type "sudo aptitude update && sudo install ubuntu-restricted-extras libdvdcss2"

---

### Post by zvacet on 2008-04-04
You will probably see message NO PUB KEY XYZZYXXY
[B]
 XYZZYXXY [/B]=number you will see

type in terminal

gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -

**KEY**=XYZZYXXY

---

### Post by nedstrange on 2008-04-04
kool that worked, got the stuff installed  but the only thing is that i could not add those lines to the 3rd party software but every thing is working so im good to go 
thanks for the help

---

