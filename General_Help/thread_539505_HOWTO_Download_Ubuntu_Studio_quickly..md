---
title: "HOWTO: Download Ubuntu Studio quickly."
date: 2007-08-31
forum: General Help
---

### Post by mark_lar on 2007-08-31
Right, if you're having the trouble I had, as in the Ubuntu Studio file was downloading miserably slow (30kB/s here) download it from any other site offering the latest version, drag and drop the ISO into the install folder in Wubi, removing the old one. NOTE: before you do this, make sure they have the same name! Now that is done, open wubi and setup as normal, the program will be fooled into thinking that the installation was aborted last time and think the OS had fully downloaded from within Wubi. 

Thats it, done!!

Mark

---

### Post by tuxcantfly on 2007-08-31
there's no need to "fool" the installer, you can simply place the ubuntustudio alternate iso file in the same directory as the Wubi installer .exe file, and run the installer (and select the ubuntustudio option), it'll use the iso automatically.

---

### Post by adinugro on 2007-09-12
can i put ubuntu, edubuntu, ubuntustudio, xubuntu and kubuntu alternate iso in the dvd and run wub from the dvd directly?

thanks,

Daniel

---

### Post by ago on 2007-09-12
> **adinugro said:**
> can i put ubuntu, edubuntu, ubuntustudio, xubuntu and kubuntu alternate iso in the dvd and run wub from the dvd directly?

thanks,

Daniel

Not as it is, we might need to edit wubi code for that, so that the DVD is also one of the places which is searched when looking for the ISO files. Is this some sort of official DVD?

---

### Post by ago on 2007-09-12
For a manual workaround, simply copy the iso and wubi.exe off the DVD and onto the same folder. Then run wubi.

---

### Post by adinugro on 2007-09-16
Thanks for the quick reply

It would be great if we can have one dvd which contains, wubi-installer and iso's for ubuntu, kubuntu and xubuntu, we can install it anywhere as we like without copying over to local hard disk first. or even using local network so we can store all of the iso's in local server.

I have suggestion:

1. we can choose where to download iso from (dvd/flash disk/local server/local mirror).
2. timezone can also be put as option before installation.

many thanks to all of you.

---

### Post by ago on 2007-09-17
> **adinugro said:**
> 
1. we can choose where to download iso from (dvd/flash disk/local server/local mirror).

In the new version the order is: local disk (in some specific locations), physical CD, remote mirror

The downloader will be much improved so that download speeds will no longer be an issue.

As per creating the DVD, it should be quite straightforward to put all the ISOs you are interested in within on DVD with wubi.

> 2. timezone can also be put as option before installation.
Current code tries to detect the windows timezone and use the same one. Arguable the detection code could be improved, but is okish, also because it is relatively easy to change the timezone within Ubuntu.

If you want to do any advanced preconfiguration you can always edit preseed.cfg before rebooting

---

### Post by adinugro on 2007-09-17
> **ago said:**
> In the new version the order is: local disk (in some specific locations), physical CD, remote mirror

The downloader will be much improved so that download speeds will no longer be an issue.

As per creating the DVD, it should be quite straightforward to put all the ISOs you are interested in within on DVD with wubi.


I have tried it before on wubi-7.04.04, and it failed :) it was trying to connect to the internet. I put wubi and iso's on the same folder called wubi, do I need to put it on the dvd's root folder?

Internet connection is very-very slow in my country, we are relying on dvd :(

many thanks,

Daniel

---

### Post by ago on 2007-09-17
> **adinugro said:**
> I have tried it before on wubi-7.04.04, and it failed :) it was trying to connect to the internet. I put wubi and iso's on the same folder called wubi, do I need to put it on the dvd's root folder?

That should work, note that Wubi-7.04 requires the ALTERNATE ISO (do a checksum to make sure the file is correct). 
Wubi 7.10 will require the DESKTOP ISO.

---

