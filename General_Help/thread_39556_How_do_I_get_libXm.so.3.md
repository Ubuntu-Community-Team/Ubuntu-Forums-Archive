---
title: "How do I get libXm.so.3 ?"
date: 2005-06-05
forum: General Help
---

### Post by Roscoe on 2005-06-05
I'm trying to use the Citrix client. When I start it I get:

wfcmgr: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

Can anyone help me with this library?

Thanks

---

### Post by clb137 on 2005-06-05
[QUOTE=Roscoe]I'm trying to use the Citrix client. When I start it I get:

wfcmgr: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

Can anyone help me with this library?

Thanks[/QUOTE]
hi,

open 'synaptic' and search for libxm,  then install the files also install the'dev' files

You have to ensure that you have installled the extra repos  see 
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)  

clinton

---

### Post by Buelldozer on 2005-06-15
With all respect to the above poster his method did NOT work for me. I was unable to find a "libxm" package to install, even with every repository enabled that I know of.

However, in other place on this forum there were some people having difficulties with libxm.so.3 while trying to install the IBM 5250 client and one of them suggested installing libmotif3 from Multiverse.

THAT worked for me, across all three of my Ubuntu boxes.

Also, one word of caution: At least on Ubuntu the Citrix ICA Client V9 will ONLY connect with Windows 2003 based Terminal Servers. If you need to connect to a Windows 2000  based terminal server find and install Version *8* of the ICA Client.

I hope that helps, and if it doesn't then at the very least I've created an "information holder" post for myself for future reference.  :)

---

### Post by clb137 on 2005-06-16
[QUOTE=Buelldozer]With all respect to the above poster his method did NOT work for me. I was unable to find a "libxm" package to install, even with every repository enabled that I know of.

However, in other place on this forum there were some people having difficulties with libxm.so.3 while trying to install the IBM 5250 client and one of them suggested installing libmotif3 from Multiverse.

THAT worked for me, across all three of my Ubuntu boxes.

Also, one word of caution: At least on Ubuntu the Citrix ICA Client V9 will ONLY connect with Windows 2003 based Terminal Servers. If you need to connect to a Windows 2000  based terminal server find and install Version *8* of the ICA Client.

I hope that helps, and if it doesn't then at the very least I've created an "information holder" post for myself for future reference.  :)[/QUOTE]


Any problems finding files the best way is to download them from 'debians own site'

---

### Post by Buelldozer on 2005-06-23
If I knew what that meant I'd surely be farther ahead of the game.

---

### Post by clb137 on 2005-06-23
[QUOTE=Buelldozer]If I knew what that meant I'd surely be farther ahead of the game.[/QUOTE]


hi there,

if you go to this site [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)    you can search and download whatever file u need,  on you have downloaded the file it will end with .deb

to install this file type 'sudo dpkg -i *.deb'  (* indicates the name of the file you have downloaded) you will be asked for your passwrod enter it and watch it install, if there is nay error that refer to a dependancy then you will have to download them and install them as well,  you will have to install them in order if there is more than one missing file.  Hope this helps


clinton

---

### Post by cpw on 2007-11-14
apt-get install libmotif3

---

### Post by vixensjlin on 2008-03-16
I am running AMD64 on a Core2Duo, and installing libmotif3 does not work for me, the application response:  "error while loading shared libraries: libXm.so.3: wrong ELF class: ELFCLASS64"

Is there's version for 64 bit?

---

### Post by stubi on 2008-03-29
Workaround is to download the 32 bit libmotif3 manually from:
http://<mirror>/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb

Then install it with sudo dpkg --force-architecture libmotif3_2.2.3-2_i386.deb
And then sudo ln -s /usr/lib/libXm.so.3 /usr/lib32/libXm.so.3

Please note that this method conflicts with _any_ packages which require 64bit libmotif3 and only should be used for closed source coded applications like the Citrix client.

---

### Post by jeffp711 on 2008-04-29
> **stubi said:**
> Workaround is to download the 32 bit libmotif3 manually from:
http://<mirror>/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb

Then install it with sudo dpkg --force-architecture libmotif3_2.2.3-2_i386.deb
And then sudo ln -s /usr/lib/libXm.so.3 /usr/lib32/libXm.so.3

Please note that this method conflicts with _any_ packages which require 64bit libmotif3 and only should be used for closed source coded applications like the Citrix client.

Thanks Stubi.  This worked perfectly on my fresh Hardy AMD64 install.  Sadly, now I have to work from home.

---

### Post by fmpfmpf on 2008-05-09
i am trying to get libmotif3 using synaptics but i keep getting 0search results.
am i doing anything wrong?
tq

---

