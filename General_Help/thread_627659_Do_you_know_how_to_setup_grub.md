---
title: "Do you know how to setup grub?"
date: 2007-11-30
forum: General Help
---

### Post by elgaza on 2007-11-30
Hi

I have installed Ubuntu 7.10 on my 1st partition, I wanted to add a line to grub to boot to the 2nd

partition but I get error saying "Error 1: Invalid device requested"

this is my partiton setup:

1st partition active 15gig with ubuntu 7.10 installed and grub installed to the mbr

2nd partition 20gig with dos installed (needed for imaging purposes) this partition is extended not primary

3rd partition is the swap partition

and these are the lines that I have added to /boot/grub/menu.lst

title Restore from image
rootnoverify (hd0,4)
makeactive
chainloader +1


and when I choose this to boot from I get this error "Error 1: Invalid device requested"

Where did I go wrong?

thank you all.

---

### Post by elgaza on 2007-11-30
wow I didnt think it that hard!!!

not even one reply!

nodoby does dual booting here?

---

### Post by nick_h on 2007-11-30
You need to fool DOS into thinking it is the first drive using the map command.

I did a quick google and came up with [this](http://orgs.man.ac.uk/documentation/grub/grub_4.html#SEC22).

Also you may have to use a primary partition, but I'm not sure.

---

### Post by meierfra on 2007-11-30
Are you sure that ¨dos¨ is on (hd0,4). That would mean that it is on a  logical partition and you probably won´t be able to boot it. You might try and delete the ¨makeactive¨. (Grub returns an error if  use ¨makeactive¨ for a logical partition)

If deleting ¨makeactive¨ did not help,  post the output of 

```
sudo fdisk -l
```

and your whole menu.lst

---

### Post by Craigus on 2007-11-30
Try supergrub - 

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

