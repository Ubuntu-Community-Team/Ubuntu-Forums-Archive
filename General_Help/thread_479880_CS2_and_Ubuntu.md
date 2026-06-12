---
title: "CS2 and Ubuntu"
date: 2007-06-20
forum: General Help
---

### Post by tsav87 on 2007-06-20
I have used and loved Ubuntu in the past, but I was never able to get Adobe Photoshop CS2 working on it.  Is there now a way to run CS2 on Ubuntu?

---

### Post by bronze on 2007-06-20
Should be possible using CrossOver Office 2.0. For more information about this, use google, or click my link:
[http://www.desktoplinux.com/articles/AT7770280571.html]("http://www.desktoplinux.com/articles/AT7770280571.html").

Other than that, I might mention that I always keep a small partition (40GB, reserved for games and apps) just in case. I'm a decent counter-strike player, so I really need windows anyhow.

***EDIT***: Just saw that the link I provided is outdated. So sorry for that... Hmm, instead, let me reccomend gimpshop:
[http://gimpshopdotnet.blogspot.com/]("http://gimpshopdotnet.blogspot.com/").
Basically, it's gimp, but modified to be more user-friendly to ex-photoshoppers.

---

### Post by PhatStreet on 2007-06-20
> **bronze said:**
> Should be possible using CrossOver Office 2.0. For more information about this, use google, or click my link:
[http://www.desktoplinux.com/articles/AT7770280571.html]("http://www.desktoplinux.com/articles/AT7770280571.html").

Photoshop 7, the one in the article, works fine under WINE already...

---

### Post by tsav87 on 2007-06-20
Yeah, I know that, but CS2 has features that I use that PS7 does not have.

---

### Post by brainsaw on 2007-06-26
you could try this
[http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

---

### Post by ElemonGW on 2007-07-11
> **bronze said:**
> I'm a decent counter-strike player, so I really need windows anyhow.

btw. I am too and I can tell you that you don't have to have windows for that. You can also easily play it under Linux (what I do :) ).

---

### Post by proxess on 2007-07-19
I wrote this somewhere on the forum:


Well its not worth trying to install directly through wine.

First you should install in windows then copy paste it to your wine drive_c folder, OR use a partition accessible by both systems. What I do is use a 40gb partition in EXT2 and user drivers for it in Linux, and give wine the same drive letter.
In wineconf, put the OS as winXP (your OS has to be winXP as well i guess).
DON'T run the applications as sudo like its said in the tutorials mentioned above, its not necessary.
The flash 8 tutorial should work fine, i've made it work. Don't have screenshots tho.
For photoshop CS2, you also need to copy the uninstall registry key from windows. Just search for EPIC_SERIAL and you'll find it.
Then in linux, copy the C://Documents and Settings/<Username>/Application Data/Adobe folder into <wine drive_c>//windows/profiles/<Username>/Application Data/.

[Heres a screenshot of Photoshop CS2 on Feisty]("http://myte.zyns.com/Screenshot-12.png")

Tho for some reason it only worked once. I keep getting the admin error. Don't ask me, its just weird.

---

### Post by go_beep_yourself on 2007-10-26
> **proxess said:**
> I wrote this somewhere on the forum:


Well its not worth trying to install directly through wine.

First you should install in windows then copy paste it to your wine drive_c folder, OR use a partition accessible by both systems. What I do is use a 40gb partition in EXT2 and user drivers for it in Linux, and give wine the same drive letter.
In wineconf, put the OS as winXP (your OS has to be winXP as well i guess).
DON'T run the applications as sudo like its said in the tutorials mentioned above, its not necessary.
The flash 8 tutorial should work fine, i've made it work. Don't have screenshots tho.
For photoshop CS2, you also need to copy the uninstall registry key from windows. Just search for EPIC_SERIAL and you'll find it.
Then in linux, copy the C://Documents and Settings/<Username>/Application Data/Adobe folder into <wine drive_c>//windows/profiles/<Username>/Application Data/.

[Heres a screenshot of Photoshop CS2 on Feisty]("http://myte.zyns.com/Screenshot-12.png")

Tho for some reason it only worked once. I keep getting the admin error. Don't ask me, its just weird.

That link does not work. Why don't you upload the image to the forum?

---

