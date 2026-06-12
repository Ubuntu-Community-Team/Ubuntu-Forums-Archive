---
title: "unable to mount pendrive/mp3 player"
date: 2007-07-28
forum: General Help
---

### Post by kadafi69 on 2007-07-28
I got a 2gb pen drive / mp3 player, at first it only showed 512mb and worked fine, so I formatted it in windows (as i dont know how to do it in linux), used FAT32, came back to linux and put my music on there, then the drive wouldnt play anything. so i plugged it back in and now it wont mount. i get this error:

mount: /dev/sdc1: cant read superblock
unable to mount: unknown error

I went back to windows and it just hangs everytime i try to click on it.

any ideas?

cheers

---

### Post by p_quarles on 2007-07-28
MP3 players usually require firmware loaded onto the filesystem in order to do anything. When you formatted it, you erased the program that makes it work. 

You should be able to get the firmware back on it (probably have to use Windows) either with the disk that came with the player, or at the manufacturer's web site.

---

### Post by kadafi69 on 2007-07-28
Well the thing is really cheap off ebuyer, theres no manual with it, and the packaging doesnt provide any details just has a spec. the only place i can get any imformation is from ebayer but on the item page it doesnt provide any helpful details and google searching hasnt turned anything over. im screwed!

[http://www.ebuyer.com/customer/products/index.html?rb=0&action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=126068]("http://www.ebuyer.com/customer/products/index.html?rb=0&action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=126068")

---

### Post by nga911 on 2007-07-28
formating it wont flash the firmwire ! try formating it again .

---

### Post by p_quarles on 2007-07-28
That's too bad. At least you didn't spend a fortune on it.

Probably won't work, but if you are completely unable to find the firmware for this thing, you might see if Rockbox will work. It's a Linux-based alternative firmware for MP3 players, but it doesn't work on all devices.

---

### Post by kadafi69 on 2007-07-28
> **nga911 said:**
> formating it wont flash the firmwire ! try formating it again .


everytime you click on it in windows it just crashes.





ive downloaded a couple of bits of firmware which ill try. cheers

---

### Post by zero244 on 2007-10-03
Try This
sudo rmmod ehci_hcd
password:
Then try mounting it.

---

### Post by brianves on 2007-10-13
hey,  I was having a similar issue with a Coby 2gb.  well not quite similar,  but it just simply would not mount.  I tried the above post  "sudo rmmod ehci_hcd"  in terminal...  worked like a charm.  thank you very very much!!!

---

