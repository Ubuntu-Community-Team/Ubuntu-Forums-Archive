---
title: "Nokia N95"
date: 2007-08-11
forum: General Help
---

### Post by Freddy on 2007-08-11
I just bought myself a Nokia N95 today and I was wondering how to transfer music/picture/video files to it through USB, if anyone can point me in the direction of a decent howto I would be a happy boy.

/Freddy

---

### Post by bettlebrox on 2007-08-11
Do you have a data cable?

U can probably plug it in, set it to "USB Mass Storage" and should be automounted:

[http://www.n95users.com/forum/general-95/1393-linux-nokia-n95.html](http://www.n95users.com/forum/general-95/1393-linux-nokia-n95.html)

---

### Post by jcopperman on 2007-08-11
Hi guys, I've got a Nokia 9500 that I'm trying to connect to Feisty with a USB cable but I get nothing, mainly, I need it for GPRS internet, so I'd like to follow to c if u guys come up with anything. Don't think WINE could help much with Nokia PC Suite.

---

### Post by Freddy on 2007-08-11
> **bettlebrox said:**
> Do you have a data cable?

U can probably plug it in, set it to "USB Mass Storage" and should be automounted:

[http://www.n95users.com/forum/general-95/1393-linux-nokia-n95.html](http://www.n95users.com/forum/general-95/1393-linux-nokia-n95.html)
Hmm, haven't seen anything like "USB Mass Storage" in my phone. Is there a application for mounting that, cause I don't use KDE or Gnome, and I don't have access to all their default installed utility's.

---

### Post by bettlebrox on 2007-08-11
Connect the phone to your computer and see what happens.

If it's like my N73, the phone will *ask* which mode to want to connect with.

---

### Post by bagguley on 2007-08-19
Transferring data accross is easy. SImply attach your phone to your machine via the usb cable. Select usb mass storage and then ok on your phone. Finally look in /media and it'll be there.

Now, has anyone managed to get this syncing with a  mail client yet?

---

### Post by iamkrazee on 2008-06-12
> **Freddy said:**
> Hmm, haven't seen anything like "USB Mass Storage" in my phone. Is there a application for mounting that, cause I don't use KDE or Gnome, and I don't have access to all their default installed utility's.

The Mass storage thing is for you to choose from the PHONE. Once you do that, you can see your phone's memory (Either bundled 2gb mem card or 8gb flash memory) which will then be detected as an unmounted vfat drive. 

It's rather simple to mount it on either of GNOME/KDE but even if you're on text mode, this should work for you..:


Step 0 : Root access ```
sudo su
```

Step 1 : See device location
```
fdisk -l
```

Step 2 : Mount (assuming /dev/sdc is your drive)
```

mkdir /mnt/n95mem
mount /dev/sdc1 /mnt/n95mem -o gid=users
```

Now you can browse through that folder "n95mem" using whichever browser that you may want to use.

-a

P.S. : It doesn't work on internal memory. I'm trying to figure out a way for that though.

---

### Post by iamkrazee on 2008-06-12
> **bagguley said:**
> Transferring data accross is easy. SImply attach your phone to your machine via the usb cable. Select usb mass storage and then ok on your phone. Finally look in /media and it'll be there.

Now, has anyone managed to get this syncing with a  mail client yet?


Nope.. wammu keeps on crashing on my n82. Functionally everything in my n82 and friend's n95 are very much the same. But had luck on neither. Sync is not an option on linux I'm guessing.

---

