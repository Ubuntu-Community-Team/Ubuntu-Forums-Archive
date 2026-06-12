---
title: "remastersys above 4gigs"
date: 2012-12-15
forum: General Help
---

### Post by verybinary on 2012-12-15
Im trying to configure a ubuntu live using 10.4 but I'm aiming for the complete&#273; ido to weigh in at 8 gigs, and a fs limitation of remastersyd prevents over 4. Any loopholes I could use?
A majority of the space will be in home. If I make it seperate and persistant, it wont be included in casper. And ill need the compression. Its 10 gigs. Casper should drop it down to 8 ish, but I'm still at the 4gig hurdle. Please help

---

### Post by Cheesemill on 2012-12-15
It's not possible.

You can read the explanation on the Remastersys web site here:
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by verybinary on 2012-12-15
Yeah, I went from that page to register on the forum. Are there no similar tools that will do the same concept without the same methods? Or am I just gonna have to get a bigger usb and install full and not have to worry about casper or live

---

### Post by Cheesemill on 2012-12-15
I'd go for the full installation on a bigger USB stick. This way you get around the limitations you have using a Live CD.

[http://ubuntuforums.org/showpost.php?p=10293555&postcount=2](http://ubuntuforums.org/showpost.php?p=10293555&postcount=2)

---

### Post by verybinary on 2012-12-15
I thought about this too late. It was great idea, but a limitation I can't have is a device dependency. Id like to have to be able to plug and play anywhere. Any options to load the live driver config to an install?

---

### Post by Cheesemill on 2012-12-15
A full install isn't device dependant.

I've got a full install of Xubuntu on a USB stick that I've used on hundreds of different machines.

---

### Post by verybinary on 2012-12-15
Thank you cheesemill

---

### Post by SuperFreak on 2012-12-15
I don't think clonezilla has a size restriction and Root and Home directories can be backed up to various media (USB  stick, external drive, CD,DVD,etc)I am about to try this on an external drive

---

### Post by C.S.Cameron on 2012-12-15
With a persistent install you can have a second persistence file named home-rw, (just rename a blank casper-rw file).

This will act like a separate home folder.

---

