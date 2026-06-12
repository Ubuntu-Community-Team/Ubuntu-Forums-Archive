---
title: "HP Photosmart - strangely slow unload from smartcards"
date: 2007-04-29
forum: General Help
---

### Post by bash on 2007-04-29
Well I have an HP Photosmart 2610 printer. Installed hplip. Installation was all easy and went smooth. Everything works peachy. Printing, scanning, faxingg ... EXCEPT! loading photos from the smartcard slots in the printer onto the computer. 

I have on the same windows. There it takes about 10 mins to unload all the photos. The same machine running Ubuntu (everything the same. Same smartcard, same photos on it and so on) it takes about 10 minutes to load 2(!) photos. Which with 300 - 500 photos on the smartcard isn't a realy speed option.

Anyone got similar experience or know what could be wrong? Im guessing it has to be a problem with either Ubuntu or hplip.

---

### Post by bwakkie on 2008-07-12
This is a known problem. The connection via command line tools are VERY slow. (eg. almost pointless to use this way) So connection via a smart card reader or from your device over an usb cable will work normal.

3 years ago there was a topic on the hplip website about it:

[http://sourceforge.net/forum/message.php?msg_id=3186683](http://sourceforge.net/forum/message.php?msg_id=3186683)

---

