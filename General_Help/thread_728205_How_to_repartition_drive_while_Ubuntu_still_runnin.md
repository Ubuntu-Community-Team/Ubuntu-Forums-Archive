---
title: "How to repartition drive while Ubuntu still running?"
date: 2008-03-18
forum: General Help
---

### Post by solarwind on 2008-03-18
Hey all, I want to repartition my Ubuntu hard drive. Currently, (as you can see in the picture below), there are two partitions on it: the main EXT3 partition and the SWAP partition. I want to *split* the main partition into half to create HDB1 and HDB2. HDB1 is what Ubuntu is running on right now. **Is it possible to repartition it to the way I want while Ubuntu is running and without losing any data?**

[IMG]http://img116.imageshack.us/img116/1298/screenshotei1.png[/IMG]

---

### Post by bodhi.zazen on 2008-03-18
No, you should partition from a live CD. If you partition while Ubuntu is running there is a risk of data loss.

---

### Post by solarwind on 2008-03-18
> **bodhi.zazen said:**
> No, you should partition from a live CD. If you partition while Ubuntu is running there is a risk of data loss.

The problem is, I don't have a CD drive. I'm trying to get SystemRescueCD to boot off of my USB drive. I'm sure that will work. However, I have a Linux system on my USB drive. 

1. Is there a way to "image" the USB drive so I can safely put back my old bootable stuff back on my USB drive?
2. If I were to use GPARTED or QTPARTED from a live CD, would I be able to resize my main partition without data loss?

---

### Post by bodhi.zazen on 2008-03-18
LOL

You can partition anything that is not mounted. 

Install gparted with 

```
sudo gedit gparted
```

Unmount your USB drive, but leave it plugged in. Use Gparted to manage the partitions.

For your Ubuntu root partition, yes this means a live CD.

---

### Post by solarwind on 2008-03-18
> **bodhi.zazen said:**
> LOL

You can partition anything that is not mounted. 

Install gparted with 

```
sudo gedit gparted
```

Unmount your USB drive, but leave it plugged in. Use Gparted to manage the partitions.

For your Ubuntu root partition, yes this means a live CD.

No, OMNEG (oh my non-existent god, for those of you who don't know :P), that's not what I meant. I meant:

1. How do I make an exact *image* of my USB drive?
2. Is it possible to resize my Ext3 partition with gparted **without data loss**?

---

### Post by bodhi.zazen on 2008-03-18
> **solarwind said:**
> No, OMNEG (oh my non-existent god, for those of you who don't know :P), that's not what I meant. I meant:

1. How do I make an exact *image* of my USB drive?

There are several tools to do this. I use Partimage [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

You could use [Clonezilla](http://clonezilla.sourceforge.net/) or any number of other tools.

> 2. Is it possible to resize my Ext3 partition with gparted **without data loss**?

Yes. Data loss is always possible mind you but it is rare.

---

### Post by solarwind on 2008-03-18
> **bodhi.zazen said:**
> There are several tools to do this. I use Partimage [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

You could use [Clonezilla](http://clonezilla.sourceforge.net/) or any number of other tools.

2. Is it possible to resize my Ext3 partition with gparted **without data loss**?

Yes. Data loss is always possible mind you but it is rare.[/QUOTE]

I meant data loss as in does the program have to delete the data before resizing. But anyway, I know the answer now. Thanks a lot for your help! Thanks for the links to those programs!

---

