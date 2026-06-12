---
title: "Installing Adobe Reader 8"
date: 2007-09-14
forum: General Help
---

### Post by Hashte on 2007-09-14
Hello there!

I've just downloaded the .deb package for Adobe Reader 8.1.1 from the Adobe Site. But, when I'm trying to install it, it gives me the following error.

> Unpacking adobereader-enu (from .../AdobeReader_enu-8.1.1-1.i386.deb) ...
dpkg: error processing /media/sda5/AdobeReader_enu-8.1.1-1.i386.deb (--install):
 trying to overwrite `/usr/bin/acroread', which is also in package acroread

I have currently Adobe Reader 7.0.8 installed and I don't know how to uninstall it :(

Please help me!

---

### Post by orangey on 2007-09-14
try uninstalling the pkg via the synaptics pkg manager.  or use:
sudo apt-get remove acroread

---

### Post by mendieta on 2007-09-15
So, has anyone try 8.1.1 ? Is it working fine ?

Many thanks !

---

### Post by mannheim on 2007-09-15
It works fine for me here, except that sometimes it starts using 75% of my CPU for a long time. (I think this may have to do with searching.) There are other threads in these forums on Acrobat Reader 8. I'm using feisty.

---

### Post by mendieta on 2007-09-15
> **mannheim said:**
> It works fine for me here, except that sometimes it starts using 75% of my CPU for a long time. (I think this may have to do with searching.) There are other threads in these forums on Acrobat Reader 8. I'm using feisty.

Many thanks for the quick reply! I needed to uninstall Adobe 7 first, and then installation went smoothly (with the Kubuntu package installer). It integrates perfectly with Firefox. It is a huge package, but it seems pretty responsive. 

Cheers !

---

### Post by Vuddha on 2007-11-06
I had been using it for a couple of months without problems. Then all of a sudden it wouldn't stay open for more than a few seconds. I just uninstalled it. Not sure what the problem was or if I'll try using it again.

---

### Post by mendieta on 2007-11-06
> **Vuddha said:**
> I had been using it for a couple of months without problems. Then all of a sudden it wouldn't stay open for more than a few seconds. I just uninstalled it. Not sure what the problem was or if I'll try using it again.

It's still running fine here (after updating to Gutsy). Thanks!

---

### Post by adamite on 2007-11-11
Greetings to All,

I'm entirely new to Ubuntu and currently using Feisty-Fawn. Now, I've downloaded Adobe Reader 8.1.1 as a .rpm. I did install alien using Sudo, but when I tried to use to install Adobe Reader using alien. I had a .deb file then it disappeared. 

Am I doing something wrong and what should I do to get Adobe Reader to install. Thanks.

---

### Post by mendieta on 2007-11-11
> **adamite said:**
> Greetings to All,

I'm entirely new to Ubuntu and currently using Feisty-Fawn. Now, I've downloaded Adobe Reader 8.1.1 as a .rpm. I did install alien using Sudo, but when I tried to use to install Adobe Reader using alien. I had a .deb file then it disappeared. 

Am I doing something wrong and what should I do to get Adobe Reader to install. Thanks.

I think it's a lot easier to get the .deb package from the Adobe site. There is a link to "other versions", it brings you here:

[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

From there, choose the deb package in your language, that should do :-)

---

### Post by lawnbowler on 2007-11-13
Thanks Mendieta. 

The deb link was perfect, and after struggling to install Reader via the command line, your link had me finished and running in less than 5 minutes.

:)

---

