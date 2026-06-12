---
title: "How Do I Mount my Palm Centro's SDHC Card"
date: 2008-04-22
forum: General Help
---

### Post by vgrisham on 2008-04-22
I just got a Palm Centro smart phone, and I'm trying to figure out how to access its Micro SDHC card. 

I have the phone plugged in via its USB cable, but Ubuntu is not automatically mounting the card. 

My desktop also has bluetooth capability as does the phone, but I'm a complete noob to bluetooth.

Anyone have any tips to get started connecting to this phone's micro sdhc card?

---

### Post by vgrisham on 2008-04-27
I learned that there are two ways to do this. The first is to buy a card reader that specifically states it works with Micro SDHC cards. After doing so, I was able to access the card through the USB port.

The second method is to buy and install [Mobile Stream's Card Reader]("http://software.palm.com/us/html/display_palm_product.jsp?navCategoryId=&id=prod580665") software ($11.95 US). This software installs on the Palm device and allows other operating systems to see and mount its internal card. 

After doing all this, I was able to configure Amarok to sync my playlists and podcasts to the card. Palm is insistent that one must have Windows Media Player in order to sync audio media, but Amarok works just fine when using the above methods.

---

### Post by vgrisham on 2008-04-30
Here's another update for my soliloquy. The Card Reader software eventually corrupted my Palm's ability to sync via USB. I had to do a hard reset. The day I bought the software, it was listed as Centro compatible at the Palm online store. The day after it wasn't. I guess I'm not the only one who had this problem. Palm gave me a refund and I've uninstalled the software from my Centro. I'm hoping they work out whatever bugs they have and that it will soon be Centro compatible. It's a pain working with the tiny microSDHC cards. For now though, that's what works, so I'll be weilding the tweezers until some Palm application comes along that will mount the card directly.

---

### Post by vgrisham on 2008-05-04
To continue my monologue, I found [this]("http://www.softick.com/cardexport2/") software for Palm which works very well mounting my Palm's card in Ubuntu, on my wife's Mac book and in Vista. I'm storing the tweezers for the time being.

---

### Post by Kubureaucrat on 2008-05-23
thanks for the guidance.  seems like this is only if you have a memory card.  i just want to access files on the centro's built in drive.  do you know how to do this?

---

### Post by vgrisham on 2008-05-23
Yes, it only works for the card. As far as I know, it is not possible to mount the Centro's main storage. But with a 4gb card, I have no need to access that memory. There are Palm based utilities that will allow you to move files from your card to main memory however.

---

### Post by danbodoh on 2008-05-27
> **vgrisham said:**
> Yes, it only works for the card. As far as I know, it is not possible to mount the Centro's main storage. 

It is actually possible to see the internal volume through some API trickery.  The internal volume is hidden, but if you know it is there it can be accessed.  Anyone who is interested in libpisock code can look at the my code for the JPilot pics&videos plugin at [http://picsnvideos.cvs.sourceforge.net/picsnvideos/picsnvideos-jpilot/picsnvideos.c?revision=1.8&view=markup](http://picsnvideos.cvs.sourceforge.net/picsnvideos/picsnvideos-jpilot/picsnvideos.c?revision=1.8&view=markup) .  Look at the bottom of the file for vfsVolumeEnumerateIncludeHidden().  I assume the same thing can be done on the palm itself.  Maybe the softick people would be interested in this trick...

---

