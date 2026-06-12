---
title: "Removing Ubuntu from my flash drive"
date: 2008-02-07
forum: General Help
---

### Post by Oliver1 on 2008-02-07
Hi, I installed ubuntu onto my usb stick using the guide at pendrivelinux. but how do i get my usb pen drive back to exactly how it was before hand - without the partitions and stuff?

---

### Post by taurus on 2008-02-07
Boot from a LiveCD and use gparted from the LiveCD, System -> Administration, and remove all the partitions and format it back to fat32.

---

### Post by Oliver1 on 2008-02-07
Hi, sorry to be a bit newbish.
Im in gparted, but how do i delete the partitions? there are little padlocks next to both of the partition names.

---

### Post by SOULRiDER on 2008-02-07
Make sure hte flash drive isnt mounted.

---

### Post by Oliver1 on 2008-02-07
How do i do that?

---

### Post by SOULRiDER on 2008-02-07
Go to places > Computer and then right click your flash drive and select unmount.

---

### Post by taurus on 2008-02-07
> **Oliver1 said:**
> Hi, sorry to be a bit newbish.
Im in gparted, but how do i delete the partitions? there are little padlocks next to both of the partition names.

If you reread my previous post again, it said that you need to use gparted from the LiveCD.  You cannot delete or resize a partition/drive while you are using it.

---

### Post by Oliver1 on 2008-02-07
Cheers guys! think thats done it.
Thanks alot.

---

### Post by Oliver1 on 2008-02-07
Ok i did that, and i went back to windows but it was still syaing my 7gig usb stic k was only 700mb. so i came back to ubuntu and now my 2 partitions are still there but in 'computer' they show up as 2 folders within 'media' so i cant unmount them and try again?

help?

---

### Post by taurus on 2008-02-07
Can you post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

