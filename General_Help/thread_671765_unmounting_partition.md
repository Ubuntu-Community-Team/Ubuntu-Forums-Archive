---
title: "unmounting partition"
date: 2008-01-18
forum: General Help
---

### Post by mat10000 on 2008-01-18
I'm trying to resize my partition using a live CD, but its locked or something.

I tried sudo umount and that doesn't do anything

[IMG]http://img442.imageshack.us/img442/8109/screenshotvv5.png[/IMG]

---

### Post by wolfen69 on 2008-01-18
try this: (start over)
```
sudo su
```
```
gparted
```
```
umount /dev/sda2
```

---

### Post by mat10000 on 2008-01-18
I already resized the sda2 part to what i need.  Its the Ubuntu one that i can't change.  

Is this the default setup for Ubuntu?  Could i just copy sda6 and then delete sda4, sda5, and sda7?

---

### Post by bodhi.zazen on 2008-01-18
You can not resize a partition if it is mounted.

Thus if you want to resize your Ubuntu partition you need to use a live CD :)

---

### Post by rzrgenesys187 on 2008-01-18
> **bodhi.zazen said:**
> You can not resize a partition if it is mounted.

Thus if you want to resize your Ubuntu partition you need to use a live CD :)

I think he is using the live CD.  What is the error message you are getting?

---

### Post by Zack McCool on 2008-01-18
> **mat10000 said:**
> I already resized the sda2 part to what i need.  Its the Ubuntu one that i can't change.  

Is this the default setup for Ubuntu?  Could i just copy sda6 and then delete sda4, sda5, and sda7?

You cannot just dismount 4.  You'll have to dismount all of the logical partitions in the extended space.  I haven't ever tried it, but I think that should allow you to resize 4.  Then resize 6, and reboot.

---

### Post by mat10000 on 2008-01-18
i think i am using the live CD.  I restarted, loaded from CD first, and then picked that first option.

When i click for the information on sda4 it says busy at least one logical partitionn is mounted?

---

### Post by mat10000 on 2008-01-18
ubuntu@ubuntu:~$  sudo umount /dev/sd4
umount: /dev/sd4: not found
ubuntu@ubuntu:~$  sudo umount /dev/sd5
umount: /dev/sd5: not found
ubuntu@ubuntu:~$  sudo umount /dev/sd6
umount: /dev/sd6: not found
ubuntu@ubuntu:~$  sudo umount /dev/sd7
umount: /dev/sd7: not found


the 2 linux-swap things have an option "swapoff" ?

Do i need those 2 partition?

---

### Post by lespaul_rentals on 2008-01-18
I'm pretty sure running "umount" on the /dev name will not work.  I have had experiences with the 7.10 LiveCD where my existing Ubuntu partitions on the HDD will be recognized and already mounted.

Check in the /mnt and /media directories and see if anything's mounted.  Try the following:

```
sudo -i
```
```
ls /mnt
```
```
ls /media
```

If you see anything in either the /mnt or /media directories that looks suspiciously like a mounted HDD partiion, umount it like so:

```
umount /mnt/<mount name>
```
or
```
umount /media/<mount name>
```

---

### Post by mat10000 on 2008-01-19
no there is nothing in /media or /mnt

---

### Post by mat10000 on 2008-01-19
Alright, i clicked "swapoff" for both Linux swap things and now i can resize everything.  Is that alright, or will my computer explode?

Can i delete those linux swap partitions?

[IMG]http://img259.imageshack.us/img259/8590/screenshot1ig1.png[/IMG]

---

### Post by lespaul_rentals on 2008-01-19
> **mat10000 said:**
> Alright, i clicked "swapoff" for both Linux swap things and now i can resize everything.  Is that alright, or will my computer explode?

Can i delete those linux swap partitions?

I wouldn't delete them both, unless you really feel you need to.  Delete one though, if you have a large amount of RAM (1 GB+) you could keep the smaller one, if you have anything less than 1 GB I'd keep the larger one.

---

