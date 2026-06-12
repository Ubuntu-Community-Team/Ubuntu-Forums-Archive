---
title: "Lost GB when formating new MyPassport 3TB"
date: 2016-07-06
forum: General Help
---

### Post by matrooswolf on 2016-07-06
Hi,

I just bought a MyPassport 3TB and removed the Nfts partition with Gparted, then made a new one with ext4. But to my surprise Gparted shows the new partition with 44GB already in use. Is this normal?

And when I right click on the disk and look at the properties, it gets even worse. The pie chart shows 150GB in use.

Is this normal or did I do something wrong? Or is ext4 not the best way to format a MyPassport drive?

Any help or information would be greatly appreciated (before I start filling the disk ;)

---

### Post by btindie on 2016-07-06
When you create an ext4 partition it usually reserves a portion for use by root which I think defaults to 5%.

You can get this back by running:
```
$ sudo tune2fs -m 0 /dev/sdX1
```
where */dev/sdX1* is the name of your partition.

---

### Post by Impavidus on 2016-07-06
Part of that 3 TB partition is used for file system overhead. Could that be those 44 GB? 1.5% of the total size? I think so.

By default 5% of the partition is reserved for root. That's good for a smaller root partition to have some emergency space (or a few years back for any full install, when hard drives were much smaller than now), but for a big data partition it's much. Although you probably won't miss that 5% of your disk space and it's better anyway to leave some free space to prevent fragmentation and keep performance high. That explains the 150 GB unavailable space. The 44 GB overhead isn't even shown in the pie chart.

Edit: You want to update your forum profile. I hope you aren't really running Ubuntu 10.10 anymore.

---

### Post by matrooswolf on 2016-07-06
Hi btindie and Impavidus,

Thank for your replies.

So would it be save to reduce the partition reserved for root to 0% with tune2fs? Or would it be safer to reserve some small percentage? (are percentages like 0.25 allowed?) Or doesn't it matter on a usb drive and can I safely reduce it to zero?

(I'll update my profile ;) I'm on 14.04)

---

### Post by matrooswolf on 2016-07-06
Hi everybody,

So I went ahead and did (substitutin sdX1 with the right partition)
```
$ sudo tune2fs -m 0 /dev/sdX1
```
and...

the 150GB in the pie chart (disk properties) disappeared.

But the 44GB that Gparted reports as being in use didn't...

So what are those mysterious 44GB doing that Gparted reports?

---

### Post by oldfred on 2016-07-06
Probably the ext4 journal to improve performance. And partition table which is small.

 MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space for superuser.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by Habitual on 2016-07-06
The MyBook I have is a 3T and formats to 2.7T using ext4

---

### Post by mcduck on 2016-07-07
> **Habitual said:**
> The MyBook I have is a 3T and formats to 2.7T using ext4

That would be 3*TB* (as that's the unit hard rive manufacturers prefer due to it giving them prettier big numbers ;)) formatted to 2.7 *TiB* (The unit that matches how your computer actually uses binary data). No space lost at all. 3TB = 2.728 TiB.

It's quite common that programs use different units while not actually changing the name, as the standard for using 1000-based system instead of 1024-based is relatively new (and like mentioned, doesn't actually match with what's happening in your computer, even though it does fit better with the usual SI standards used for other units). If there's any doubt, I usually just do a quick check if the difference in numbers would match for 1000 VS 1024 based units conversion, almost always it does...

edit. To make it more confusing, data transfers use 1000-base anyway (as pure data transferred through a network might or might not be computer related), while things like RAM, memory cards and (at least professional) SSD drives are built & sold in 1024-based units (because of how our binary-based computers and memory technology actually work and are manufactured). This means that if you have a GB of data in you have a GB worth of data in your RAM, it won't fit to GB of disk space :D And the contents of 1GB SD card would fit in 1GB of memory, but once again would not fit on 1GB hard drive. :D

edit2: [https://www.unitjuggler.com/convert-memory-from-TB-to-TiB.html?val=3]("https://www.unitjuggler.com/convert-memory-from-TB-to-TiB.html?val=3")

---

