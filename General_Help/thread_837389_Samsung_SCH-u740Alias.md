---
title: "Samsung SCH-u740/Alias"
date: 2008-06-22
forum: General Help
---

### Post by JKMcL on 2008-06-22
Hey guys, I am new to linux and I have a question.

What are some good phone managers that will work with the Samsung SCH-u740? (AKA the Alias.) I have paired my phone with the computer over bluetooth and have gotten blueproximity working, but I cannot find a program that works as a file manager/SMS reader and sender. gnome-phone-manager has not worked. Gammu/Wammu has not worked and I cannot get Bitpim to even find my phone. Gnokii/Gnocky didn't work either.

If anyone has gotten their Samsung SCH-u740 to work properly with any of these programs please respond. (Also if anyone could recommend a program I have not yet tried, I would be grateful for that too.)

    Thanks,
           -JKMcL

---

### Post by JKMcL on 2008-06-23
Bump please?

---

### Post by steam_engenius on 2008-06-25
Bump!

---

### Post by JKMcL on 2008-06-26
Last bump from me. Anyone please?

---

### Post by gotmonkey on 2008-08-12
> **JKMcL said:**
> Hey guys, I am new to linux and I have a question.

What are some good phone managers that will work with the Samsung SCH-u740? (AKA the Alias.) I have paired my phone with the computer over bluetooth and have gotten blueproximity working, but I cannot find a program that works as a file manager/SMS reader and sender. gnome-phone-manager has not worked. Gammu/Wammu has not worked and I cannot get Bitpim to even find my phone. Gnokii/Gnocky didn't work either.

If anyone has gotten their Samsung SCH-u740 to work properly with any of these programs please respond. (Also if anyone could recommend a program I have not yet tried, I would be grateful for that too.)

    Thanks,
           -JKMcL
Hey JKMcl

I am able to get the sch-u740 working via a usb cable that I picked up on ebay. The latest version of bitpim is v1.06. Download and install, you should be good. You will need to run ~$ sudo bitpim this will run bitpim under root privelages, which is needed to connect to the usb device. It should auto detect you phone. 

As for Bluetooth, I am still trying to find a way to connect it. I will report back if/when I figure it out. 

gotmonkey

---

### Post by finer recliner on 2008-08-12
hey guys. i have the sch-u740 and I was able to get it to sync with bitpim over bluetooth on ubuntu. with bitpim you can download and upload wallpapers, contact lists, ringtones, etc....pretty much anything you want.

i followed this guide for the most part:
[http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux](http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux)

The biggest thing to note is that this phone does not support the OBEX protocol, but you can do everything you need to do over the address sync protocol instead (i think thats what i used; i can double check when i get home if this turns out to be wrong)

---

### Post by JKMcL on 2008-08-13
Thanks for the advice you two. I'll definately try it out when I get home.

Thanks
-JKMcL

---

