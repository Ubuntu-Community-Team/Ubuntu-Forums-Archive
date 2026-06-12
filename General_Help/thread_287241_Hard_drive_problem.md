---
title: "Hard drive problem"
date: 2006-10-28
forum: General Help
---

### Post by sticatto on 2006-10-28
Hi, I have just installed ubuntu and I am having a little trouble..I did a partition on a 40gb hard drive and so theres 20gb for ubuntu. My question is,  is there anyway for me to access the other half of the partition with my music/movies/other things, and I also have a 160gb hdd installed also, how can i access this? Any help would be appreciated. :)

---

### Post by kidders on 2006-10-28
Hi there,

What have you tried so far? Can you post any problems/errors?

---

### Post by DaveBorealis on 2006-10-28
Hello,

To get started in the right direction you could do:
sudo fdisk -l
and see what the other drives are called.

Then add them to /etc/fstab to be mounted.

If you need more help post what you get for 'fdisk -l' and what you have in /etc/fstab.

Best regards,
Dave

---

### Post by handy on 2006-10-28
If you have the Dapper or Edgy Live-CD you can boot with that & use the **Gnome Partition Editor** (GParted) from the:

***Menu:* System / Administration / **

You can create delete resize partitions reliably from this piece of software.

---

