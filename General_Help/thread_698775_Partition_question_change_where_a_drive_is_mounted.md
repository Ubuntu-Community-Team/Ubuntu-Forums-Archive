---
title: "Partition question: change where a drive is mounted?"
date: 2008-02-16
forum: General Help
---

### Post by NoSmokingBandit on 2008-02-16
I have a 5gb ext3 partition that i use for the OS, and another one that i want to keep my files on but i was stupid and mounted it somewhere that wasnt my home folder. I cant even find the partition on my computer. Is there a way i can change this partition to my home folder now?

---

### Post by pointone on 2008-02-16
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by jan quark on 2008-02-16
run these commands to clarify the mount point of your missing partition 

please post the result and send me a private message when you have answered 

thank you

```

sudo fdisk -l
```

```
mount
```
```

cat /etc/fstab
```

---

### Post by NoSmokingBandit on 2008-02-16
Crap, i restarted and now i have a completely blank screen and cant do anything. I guess ill have to start over anyway... This time ill mount it the right way.

---

### Post by jan quark on 2008-02-16
hey no problem

I had to install gutsy 5 times in a row to get it right

nobody is perfect

good luck it is definitely worth the effort :)

---

### Post by NoSmokingBandit on 2008-02-16
Alright, so im looking at the partition screen right now and im lost again, lol. Can i set a home partition in the installation process or do i have to configure that later?

---

