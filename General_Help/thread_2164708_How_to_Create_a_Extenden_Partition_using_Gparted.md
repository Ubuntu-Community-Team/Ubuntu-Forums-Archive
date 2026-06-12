---
title: "How to Create a Extenden Partition using Gparted?"
date: 2013-08-01
forum: General Help
---

### Post by nachinew on 2013-08-01
Hi,

I accidentally delete my linux swap area using Gparted. Because the Gparted allow only 4 partition to create. 1st area is Dell Utility, 2nd for OS, 3rd Partition for Ext and 4th is NTFS for installing Windows OS. Please find the screenshot how to create a Swap area furthur or merging OS and Ext. If I wanted to create a swap Linux compulsory. Please share your views.

[IMG]http://s11.postimg.org/kn1pymsar/Gparted.png[/IMG]

---

### Post by The Cog on 2013-08-01
You can only have 4 primary partitions. If you already have 4 primary partitions, you will have to delete one in order to use it as an extended partition.

In gparted, I don't think you directly create an extended partition. I think you create a logical partition, and gparted will create the extended partition to put it in if one does not already exist.

Seeing the output from the commands
```
sudo fdisk -l 
sudo parted -l
```
would help us be sure exactly what is going on.

---

### Post by deadflowr on 2013-08-01
[Fixparts]("http://www.rodsbooks.com/fixparts/") might get you where you want to be.

I know it's suppose to allow you to convert primary partitions into logical ones and vice versa, which, I would assume means creating an extended partition for the logical partition.

---

### Post by nachinew on 2013-08-01
> **The Cog said:**
> You can only have 4 primary partitions. If you already have 4 primary partitions, you will have to delete one in order to use it as an extended partition.

In gparted, I don't think you directly create an extended partition. I think you create a logical partition, and gparted will create the extended partition to put it in if one does not already exist.

Seeing the output from the commands
```
sudo fdisk -l 
sudo parted -l
```
would help us be sure exactly what is going on.

How to create a logical partitioooon or convert the logical from primary, Please tell me with an illustration.

---

### Post by nachinew on 2013-08-01
> **deadflowr said:**
> [Fixparts]("http://www.rodsbooks.com/fixparts/") might get you where you want to be.

I know it's suppose to allow you to convert primary partitions into logical ones and vice versa, which, I would assume means creating an extended partition for the logical partition.

How to create a logical partition or convert the logical from primary, Please tell me with an illustration.

---

### Post by MIJ-VI on 2013-08-01
An alternative to having a swap partition:

Ubuntu, how to create a swap file at DuckDuckGo
[https://duckduckgo.com/?q=Ubuntu%2C+how+to+create+a+swap+file](https://duckduckgo.com/?q=Ubuntu%2C+how+to+create+a+swap+file)

---

