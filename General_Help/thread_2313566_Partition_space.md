---
title: "Partition space"
date: 2016-02-13
forum: General Help
---

### Post by Robbyx on 2016-02-13
On Root sda2 I have 2.1GiB free out of a total of 18.1
Home  sda3 16 free out of 34

It is not easy to work out what is taking up so much space on the root and so I am looking to expand it by acquiring the unallocated space on sda4. 

Gparted shows:

sda4 Extended partition with  16GiB unallocated

1. Using Gparted on a live usb stick I am able to move the free space on sda4 to sda2 but I am getting warnings that the system might not boot because I am modifying sda2 which is the boot partition. I can see there is some gparted advice about rebuilding the grub2 but I am uneasy about it and hope I do not need to do it. Is there a way of ensuring the grub is not damaged?

2. Gp is very  slow at moving partitions around. Can you recommend a partition clone tool that would enable me to restore the cloned drives to the reformatted and enlarged partitions sda2 and sda3?

---

### Post by grahammechanical on 2016-02-13
Please run a Ubuntu live session and open GParted and then take a screen shot and attach the image to your post. Then we can see for ourselves. I do not want to guess the true partition layout.

Some general principles.

1) We cannot resize partitions that are in use/mounted. This is why we use GParted from a live session.
2) In GParted a key icon alongside a partition means that the partition is locked/mounted and cannot be resized.
3) It is possible that the swap partition is a logical partition inside the Extended partition and that the live session activated the swap partition. So, in order to resize the extended partition we need to mark the swap partition as swap off. 

18GB for Ubuntu is a reasonable amount provided we do not install many additional applications. Especially large ones. Then 18GB is not so large an amount as we thought. That is where the space of sda2 has gone.

Regards.

---

### Post by Robbyx on 2016-02-13
Thank you for your reply. Could you please look again at my query because I radically changed it when  I realised that I needed to run Gp from a live CD. I appologise for making the changes, but hoped I could do them quick enough to avoid unnecessary replies.

---

### Post by yancek on 2016-02-13
You need to post the image of the GParted screen to get any accurate help.  It is necessary to see this to know what type of partitions you have.  If you are moving partitions which contain data then you are not just modifying the partition but also moving the data which is why you get the warning about boot files and why it takes longer.

---

### Post by Robbyx on 2016-02-13
Would  using a drive/ partition  cloning program to back up the drives, reformating the 2 partitions,  and then restoring the two partitions  greatly speed up the change to the size of sda2 and 3? 
[IMG]http://i.imgur.com/qVw7vd2.jpg[/IMG]

---

