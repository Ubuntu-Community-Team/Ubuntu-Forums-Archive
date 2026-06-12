---
title: "Asus USB N13 slow wireless connection in Ubuntu 12.04"
date: 2012-11-17
forum: General Help
---

### Post by PhantomTurtle on 2012-11-17
Hello,

I have a Asus USB-N13 ([http://www.asus.com/Networks/Wireless_Adapters/USBN13/](http://www.asus.com/Networks/Wireless_Adapters/USBN13/)) wireless adapter which only gets me speeds up to 1 MBps on Ubuntu 12.04 (64-bit), however on Windows(dual-boot) I get up to 16 MBps. The N13 is supposed to have Linux support, which it does because it works out-of-box but the speeds are really low. I read [this]("http://askubuntu.com/questions/168627/connecting-asus-usb-n13-wireless-adapter") on askUbuntu installing the drivers did not work. I also read [this thread]("http://ubuntuforums.org/showthread.php?t=1984103"), but I have the Realtek chipset, not the ralink one.

The output from ```
lsmod | grep rt
``` gives me

```
rtl8192cu
rtl8192c_common
rtlwifi

```

Thanks for any help you can offer.

-Phantom

EDIT: This is regarding internet speeds by the way. It loads webpages super slow and speedtest.net gave me that Internet speed result.

---

### Post by BertN45 on 2012-11-17
If the data you transfer is on a local disk with a ntfs file system, the disk io will be slow in Ubuntu. you could compare it with transferring data to and from an ext file system.

---

### Post by PhantomTurtle on 2012-11-17
> **BertN45 said:**
> If the data you transfer is on a local disk with a ntfs file system, the disk io will be slow in Ubuntu. you could compare it with transferring data to and from an ext file system.

Sorry I think I might have been a but unclear about this. It is the internet connection speed itself. Browsing the Internet and downloading stuff is slow. I will update the first post to make it more clear. Sorry about that.

---

### Post by PhantomTurtle on 2012-11-18
Bump. Anyone?

---

### Post by PhantomTurtle on 2012-11-22
I have found the answer to this and I added it to my superuser question. It is a bit lengthy so I wont copy and paste it here. I'll link to the superuser question instead - [http://superuser.com/questions/508511/slower-wireless-speed-in-ubuntu-12-04-64-bit-on-asus-usb-n13/509479#509479](http://superuser.com/questions/508511/slower-wireless-speed-in-ubuntu-12-04-64-bit-on-asus-usb-n13/509479#509479).

---

### Post by kaylus on 2013-01-05
Thank you Phantom Turtle for summarizing the posts together. I've used your set of instructions and aside from the the fact that 12.10 already has the headers installed it all went well. 

I was surprised as I came from Linux Mint 14 just now to Ubuntu 12.10 (LM is based off of this) and the network worked full speed in LM14 but in Ubuntu I was only getting 3MB download test speeds.

After the instructions I'm back up to 45MB speeds. Fantastic!

Thanks again for your work in finding and summarizing this information. 

Kaylus

---

