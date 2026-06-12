---
title: "[SOLVED] Important question about Clonezilla. Need your opinion/experience"
date: 2008-02-22
forum: General Help
---

### Post by geo909 on 2008-02-22
Hello everybody,
I'm doing a format to my Dad's Laptop (don't wanna know what will happen if I do something wrong). He now has Ubuntu 6.06/ Windows XP dual boot and a shared partition. That, including swap will make us something like 4 partitions (can't check, I'm on XP right now) in NTFS, ext3, FAT etc...

Well, before I do everything I thought it would be wise to do an image-copy of the hard disk in case I mess something up. Everybody says clonezilla is a fine tool and supports all the formats above. I downloaded clonezilla live and did a full backup of the entire internal laptop hard disk to an image on my external 500GB Seagate drive.

The thing is, I noticed the backup wasn't a byte-by-byte, dd-like backup.
For size-efficiency, clonezilla saw all of my partitions and handle everyone with different tools. Anyway, if that confuses everyone, I just used the DEFAULT OPTIONS for a entire image copy of my hda internal hard drive.

 My question is:

If I format the drive and change the partitions (resizing, deleting partitions etc), will clonezilla have any problem restoring the hda image it has done before?

Please, if you know anything about that, consider spending sometime and answering this one because messing up with my dad's laptop will be really bad for me

---

### Post by kpkeerthi on 2008-02-22
If I were you, I would have imaged the partitions individually so it is easier for me to restore the image to a partition of different size than the original.

---

### Post by magump on 2008-02-22
I have tried Clonezilla and Partimage.  I think Partimage may do the job you want, also.  It took me a couple of tries using Partimage Live CD but was happy with the results.

---

### Post by julian67 on 2008-02-22
> **geo909 said:**
> Hello everybody,
I'm doing a format to my Dad's Laptop (don't wanna know what will happen if I do something wrong). He now has Ubuntu 6.06/ Windows XP dual boot and a shared partition. That, including swap will make us something like 4 partitions (can't check, I'm on XP right now) in NTFS, ext3, FAT etc...

Well, before I do everything I thought it would be wise to do an image-copy of the hard disk in case I mess something up. Everybody says clonezilla is a fine tool and supports all the formats above. I downloaded clonezilla live and did a full backup of the entire internal laptop hard disk to an image on my external 500GB Seagate drive.

The thing is, I noticed the backup wasn't a byte-by-byte, dd-like backup.
For size-efficiency, clonezilla saw all of my partitions and handle everyone with different tools. Anyway, if that confuses everyone, I just used the DEFAULT OPTIONS for a entire image copy of my hda internal hard drive.

 My question is:

If I format the drive and change the partitions (resizing, deleting partitions etc), will clonezilla have any problem restoring the hda image it has done before?

Please, if you know anything about that, consider spending sometime and answering this one because messing up with my dad's laptop will be really bad for me

Clonezilla uses partimage and some other tools (different tools for ntfs/fat than  for ext3) . It does not do a bit for bit dump (dd), it makes an image. The advantage is that unused sectors are not copied, this speeds things up a lot. If you have repartitioned the target disk and then use your clonezilla image to restore it you will find clonezilla makes your disk exactly as it was originally...that's what it's for ;-) you will not have your newly resized partitions but the old ones.  But anyway you have a backup image now so the worst that can happen is you end up back where you started.   If you start deleting and resizing partitions you need to do some research so you understand what will be involved in making the OSs bootable and the partitions useable. The UUIDs of the partitions may change if you resize them, possibly your root and /home partitions will no longer be in the places described in fstab, you may end up with an unbootable system or a system which boots but seems to have no /home.  I really think you need to do some more research before proceeding.  At minimum you need to find out about editing/writing fstab manually and also reconfiguring grub (super grub disk is a good tool for this).

---

### Post by geo909 on 2008-02-22
> **julian67 said:**
>  If you have repartitioned the target disk and then use your clonezilla image to restore it you will find clonezilla makes your disk exactly as it was originally...that's what it's for ;-) you will not have your newly resized partitions but the old ones.  But anyway you have a backup image now so the worst that can happen is you end up back where you started.

 Hmm.. That was exactly what I wanted to hear!! I wasn't sure if the original partitioning should exist to make my image-copy restorable. Thank you very much for making it clear that it shouldn't!

 As for the actual partitioning, it worked fine. Both OSes bootable (and Dad's happy!) without having to reinstall XP. I had mess up things once in my computer, so now I learned (the hard way)! :mrgreen:

 Thanks very much for taking the time to answer this!

---

### Post by julian67 on 2008-02-22
> **geo909 said:**
> Hmm.. That was exactly what I wanted to hear!! I wasn't sure if the original partitioning should exist to make my image-copy restorable. Thank you very much for making it clear that it shouldn't!

 As for the actual partitioning, it worked fine. Both OSes bootable (and Dad's happy!) without having to reinstall XP. I had mess up things once in my computer, so now I learned (the hard way)! :mrgreen:

 Thanks very much for taking the time to answer this!

glad it was useful & everything worked out

---

