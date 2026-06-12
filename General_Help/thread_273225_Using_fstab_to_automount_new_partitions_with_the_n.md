---
title: "Using fstab to automount new partitions with the new Upstart?"
date: 2006-10-07
forum: General Help
---

### Post by NoTiG on 2006-10-07
I am trying to mount some partitions in fstab manually. i noticed now that my root partition for instance is entered thus: 

UUID=68d712be-3173-40fc-8815-44ad5cc6ec3a / ext3    defaults,error
s=remount-ro 0       1


what exactly are the UUID strings and how am i going to auto mount drives on my second hard drive?

got it. 

```
sudo tune2fs -l /dev/sda2
```

---

### Post by kerry_s on 2006-10-07
Yeah, i hate the new mounting system to, except i'm the opposite of yours. I prefer to mount my drives when i need them, i believe that automounting just increases the chances of something happing to my other installs if the one i'm using crashes. For instance if it locks up and and you have to hit the reset button then all the mounted are now unmounted uncleanly.

Anyways on to your problem. Just make the /dev the old way and it should still work.example->
/dev/hda3 /media/hda3     reiserfs defaults,auto        0       0

Make sure you create the folder for it in /media
if that don't work try making a link to the device in the /media folder.

Are you trying to get external media to auto mount? If so make sure you have hal,pmount, and ivman installed. I'm running kde-core so i'm not sure if there included on yours, but it's what i had to install to get auto mounting of external drives to work by plug and play.

---

### Post by NoTiG on 2006-10-07
im not going to auto mount my second drive.... ubuntu actually failed to auto mount it anyway... im just changing the partitions around on the second drive and need to update the fstab to reflect it.

Now however my problem is i cant find the UUID for the swap partition. tune2fs doesnt seem to work for swap.

---

### Post by kerry_s on 2006-10-07
Look in> /dev/disk/by-uuid for the old uuid. But as you will see the new set up is a pain in the butt. There are 4 links for each device so you'll have to redo the links for each device in each folder in /dev/disk/.

I feel for you man, i had to jump through hoops just to get mine not to automount and still be able to mount as non-root.

---

### Post by woekele on 2006-10-09
> **NoTiG said:**
> got it. 

```
sudo tune2fs -l /dev/sda2
```

Sorry, but what exactly does this do?

---

