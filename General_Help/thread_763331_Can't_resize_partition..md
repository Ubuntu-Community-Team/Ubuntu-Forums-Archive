---
title: "Can't resize partition."
date: 2008-04-22
forum: General Help
---

### Post by Mateo on 2008-04-22
Hi.  I resized my windows partition to make it smaller (using gparted).  i want to take the new unallocated space and apply it to my ubuntu partition.  however, when i choose to resize the ubuntu partition, it doesn't allow me to increase the size, only make it smaller.

By the way, I know to do this from a livecd with the drives unmounted.  that's what i'm doing.

gparted 0.2.5

---

### Post by em3raldxiii on 2008-04-23
... I am not 100% sure, but I am fairly certain that if you cut space off the END of a partition, you cannot add that chunk to the BEGINNING of the other partition.  AFAIK, you can only add space to the END of a partition.

Now, I have actually read somewhere (perhaps on this forum), that this is no longer true with the new version(s) of gparted.

Is it entirely necessary to add your new partition to your existing partition?  I often just change the mount point of a new partition to be incorporated into my installation - such as making the new drive into the /home directory.  So what I would do there is copy all the info you have in your existing /home and paste it into the new partition (which can be mounted as something like /media/hdb3 or something).  Once the copy is done, you can change the name of the original /home to /home_backup, and then change the mountpoint of your /media/hdb3 to /home.

I am not sure if that same procedure works for other directories (like /etc or /opt) but it might.

---

### Post by bingoUV on 2008-04-23
Move the start of ubuntu partition to the end of windows partition. Then you will be able to increase its size.

---

### Post by Mateo on 2008-04-23
> **em3raldxiii said:**
> ... I am not 100% sure, but I am fairly certain that if you cut space off the END of a partition, you cannot add that chunk to the BEGINNING of the other partition.  AFAIK, you can only add space to the END of a partition.

Now, I have actually read somewhere (perhaps on this forum), that this is no longer true with the new version(s) of gparted.

Is it entirely necessary to add your new partition to your existing partition?  I often just change the mount point of a new partition to be incorporated into my installation - such as making the new drive into the /home directory.  So what I would do there is copy all the info you have in your existing /home and paste it into the new partition (which can be mounted as something like /media/hdb3 or something).  Once the copy is done, you can change the name of the original /home to /home_backup, and then change the mountpoint of your /media/hdb3 to /home.

I am not sure if that same procedure works for other directories (like /etc or /opt) but it might.

that solution, IMO is a waste of space.  but thanks anyways.

---

