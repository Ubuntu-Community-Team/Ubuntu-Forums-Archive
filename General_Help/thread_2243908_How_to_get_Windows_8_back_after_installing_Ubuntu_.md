---
title: "How to get Windows 8 back after installing Ubuntu over it"
date: 2014-09-11
forum: General Help
---

### Post by Maheriano on 2014-09-11
I bought an Asus Zenbook UX303 and it had Windows 8 on it. I completely formatted the hard drive and installed Ubuntu 14.04 but now I've decided I don't like the laptop so I want to return it. The store is telling me they can't take it back since the Windows key is gone now and they can't reinstall it. Is there any way to get Windows back on the computer after deleting the recovery partition?

---

### Post by uRock on 2014-09-11
Did you do a backup or did it come with the recovery disk by any chance? If not, then you may want to contact Asus and get them to send you an OEM install disk.

---

### Post by Bucky Ball on 2014-09-12
> **uRock said:**
> Did you do a backup or did it come with the recovery disk by any chance? If not, then you may want to contact Asus and get them to send you an OEM install disk.

^^^
This.

As a rule of thumb, when I install Ubuntu only on a new computer I first create the recovery DVDs (generally twice) then wipe the HDD and install Ubuntu. If you ever need to go back to the factory state, simply install from the recovery DVDs.

Bit late now though, but something for next time ...

---

### Post by oldfred on 2014-09-12
The product key is built into the UEFI, but only works with the OEM version from ASUS. 

Actually if the store still sells the same model Asus they can make the recovery DVD set and restore that to your system. But that may take a while and they legitimately can charge you for their time. Best to follow uRock's suggestion and do it your self.

---

### Post by Maheriano on 2014-09-12
> **uRock said:**
> Did you do a backup or did it come with the recovery disk by any chance? If not, then you may want to contact Asus and get them to send you an OEM install disk.
No optical drive in this laptop.

> **oldfred said:**
> The product key is built into the UEFI, but only works with the OEM version from ASUS. 

Actually if the store still sells the same model Asus they can make the recovery DVD set and restore that to your system. But that may take a while and they legitimately can charge you for their time. Best to follow uRock's suggestion and do it your self.
This laptop is so new and highly sought after that they ell out instantly, I was lucky to get one when I did. They have no more in store and aren't sure when they'll be getting more. They had mentioned they could do that if they had another.

---

### Post by Bucky Ball on 2014-09-12
Things don't look great, then. Call or email Asus and see what they can do for you.

(PS: That's a sweet laptop. What's not to like? :-k)

---

### Post by Maheriano on 2014-09-12
> **Bucky Ball said:**
> Things don't look great, then. Call or email Asus and see what they can do for you.

(PS: That's a sweet laptop. What's not to like? :-k)

Thanks, I'll try that! I'm also looking at my co-worker's laptop and it's a 17 inch Asus Zenbook. I could pull the image off of that one but he's only in the province for another 4 hours, then he's flying out for 2 weeks. Can I use an image from a 17 inch on my 13 inch?

I just don't like this laptop overall, it looks EXACTLY like a Mac. My girlfriend has the Macbook and they're identical, the case is almost the same, the keyboard is identical, even the plug unit is identical. Also even though it's only a centimetre thick, it's about double the thickness of my old Samsung, that 9 Series I had was really thin and light. And it's 2 years old. So I went from a thin / light laptop to not as thin / not as light laptop. Plus the trackpad doesn't support multi-finger gestures (yet) and the tactile feedback on the trackpad is the loudest trackpad I've ever heard. It sounds like a gun going off KA-CHUNK-A! Every time you click it, and when working in a quiet working environment, that's not going to work for me. We were trying to watch a movie at home last night and my girlfriend was getting annoyed with how much noise I was making with every click of the mouse.....KA-CHUNK-A! So I'm going back to my Samsung instead.

---

### Post by uRock on 2014-09-12
> **Maheriano said:**
> No optical drive in this laptop.


This laptop is so new and highly sought after that they ell out instantly, I was lucky to get one when I did. They have no more in store and aren't sure when they'll be getting more. They had mentioned they could do that if they had another.

If you manage to get an install disk from Asus and have access to another ubuntu machine, then you can use WinUSB to put the install image on a USB. I recently tested it and it worked with my copy of 8.1 Professional.
```
sudo add-apt-repository ppa:colingille/freshlight
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/colingille-freshlight-trusty.list"
sudo apt-get update
sudo apt-get install winusb
```

---

