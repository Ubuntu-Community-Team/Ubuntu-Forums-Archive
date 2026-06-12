---
title: "GParted question"
date: 2012-10-17
forum: General Help
---

### Post by Deucalion29710 on 2012-10-17
I have a 250 GB sata hard drive as my primary system drive.  (I know not too glam)  I would like to partition it WITHOUT compromising my Xubuntu installation so that the primary OS partition is about 100GB and the rest could appear as additional or mounted storage.  I have GParted.  How can I achieve this?

---

### Post by sienile on 2012-10-17
How is it partitioned now?

Depending on how it's set up you might need to have boot-repair handy to fix everything afterwards.

---

### Post by Deucalion29710 on 2012-10-17
It is showing as: 
boot=228.89 GB
Extended=4 GB
Swap=4 GB

I'm only using just over 8GB with the OS and extras, so I could probable get away with about 50 GB for boot.

---

### Post by sienile on 2012-10-17
It looks like you should be able to just shrink it and add whatever you want after it. Shouldn't cause any boot problems.

Since you want to edit your system partition, you need to boot from the LiveCD so that it can be unmounted. Should be pretty self-explanitory from there.

---

### Post by Deucalion29710 on 2012-10-17
OK so just pop in my installation CD and change the size of the boot partition? I assume that once I do that the rest will be a usable storage partition?

---

### Post by sienile on 2012-10-17
You have to add a partition to the empty space to make it usable.

---

### Post by Deucalion29710 on 2012-10-17
I see. Hey, thanks for your input.  I shall give it a go.

---

### Post by Deucalion29710 on 2012-10-17
You are talking about the Gparted live CD and not the Xubuntu CD...am I correct?

---

### Post by sienile on 2012-10-18
Your install disk. It should have Gparted already on it.

---

### Post by Cheesemill on 2012-10-18
> **Deucalion29710 said:**
> You are talking about the Gparted live CD and not the Xubuntu CD...am I correct?
Either.

The Ubuntu Live CD's all have Gparted already installed on them.

---

