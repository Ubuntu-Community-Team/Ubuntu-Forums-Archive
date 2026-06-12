---
title: "format an old SSD with Disks app question"
date: 2021-02-24
forum: General Help
---

### Post by Old Jimma on 2021-02-24
Hi Community:

I have an old SSD that had the UbuntuOS and my home directory. 

I took that SSD out of the old computer and put it in an SSD enclosure and I want to use it as a back up USB drive now.

I tried to remove the old partions using the disks utiity... but it won't do anything. Not sure why. Is it an ownership issue?

How do I used the Disks app on my new computer to format that external SSD??

THanks
Old Jimma

---

### Post by CelticWarrior on 2021-02-24
Maybe you aren't doing it right. maybe is about permissions... I don't know.

You can try GParted > Device > Create partition table (choose GPT). This surely works because it runs as root. Then you may use Disks for creating a new partition - typical for an external drive usage - or more, depending on your needs. Of course, you can do the same in GParted but the advantage of the Disks approach is that you won't have to deal with ownership.

---

### Post by Old Jimma on 2021-02-25
HI CelticWarior:

Thanks for your reply.

I tried gparted. It won't let me umount some of the pariitons on the SSD.... it says they are busy.

How do I fix this?

Old

---

### Post by Impavidus on 2021-02-25
If they are busy, it means that some files on those partitions are open or some application uses a directory on that partition as its present working directory.

---

### Post by Old Jimma on 2021-02-25
Thanks for your reply Impavidus.

THere was a very good reason why those partitions were busy. When I started gparted, I did not choose the USB SSD. It automatically defaults to my home partition... and that's always busy.

When I chose the USB SSD in parted. I could umount all of the files, and reparition and format the SSD.

Thanks for all of your comments.

Sincerely,
OLD

---

