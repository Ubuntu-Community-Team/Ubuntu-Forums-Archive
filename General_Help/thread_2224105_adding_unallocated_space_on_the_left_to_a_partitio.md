---
title: "adding unallocated space on the left to a partition in the right?"
date: 2014-05-14
forum: General Help
---

### Post by rizos on 2014-05-14
i want to add unallocated space to sda5 partition (home folder) but i cant, somehow gparted shows an error message.


how should i add this unallocated space?





[ATTACH=CONFIG]253155[/ATTACH][IMG]http://postimg.org/image/5dkeqoser/[/IMG]

---

### Post by Impavidus on 2014-05-14
You cannot modify a mounted partition and you cannot unmount your home partition while you are logged in. So the solution is to boot from a live disk.

Make sure you have backups of your vital files. Moving the beginning of a partition takes a long time and if anything goes wrong during that time (power failure, for example) you could lose all your files.

There are two other options. You could simply create an extra data partition and mount it somewhere convenient, but this is not very flexible. Another option is to create a new partition in the unallocated space and copy all files from sda5 to the new partition. It should just fit. Maybe you can remove some cache directories first. This takes a long time, but it's safe as you don't write to sda5. Then delete sda5 and expand the new /home partition to the right. This is fast and safe. Don't forget to update /etc/fstab if you do this, or you'll get an error the next time you boot.

---

### Post by rizos on 2014-05-14
i'm using the livecd to create a new partition so that all files from home would fit on, how can i copy all the files from home to the new partition?

---

### Post by Bucky Ball on 2014-05-15
All you needed to do was, as explained, boot from a liveCD and expand sda5 into the unallocated space. It is not as easy as simply copying the files from /home to a new partition. You need to let the system know you are changing the location of /home, if that is what you are doing, and that sounds like your intention. 

There are a lot of how-tos on how to move your /home partition, but really, it seems a bit pointless. You already have a /home and just need to expand it to the left running from a LiveCD ... :-k

---

### Post by rizos on 2014-05-15
well every time i try to expand the home partition to the left where the unallocated space is, after a looong while says it cannot be done. so, im confuse on how to do this.

of course running it fomr a live cd.

---

### Post by Bucky Ball on 2014-05-15
Well, that is odd. It does take quite some time. sda5 is unmounted when attempting this? Guess it must be else you wouldn't be getting the option to resize ... :-k

---

### Post by HermanAB on 2014-05-15
Simple: Don't.

You should never mess with the partition tables of partitions with data that you haven't backed up yet and if you have backed it up, then simply create new partitions the way you want them to be and then restore the backed up data.

---

