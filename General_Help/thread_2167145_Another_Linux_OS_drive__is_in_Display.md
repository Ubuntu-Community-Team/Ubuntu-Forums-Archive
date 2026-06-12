---
title: "Another Linux OS drive  is in Display"
date: 2013-08-12
forum: General Help
---

### Post by nachinew on 2013-08-12
Hi,

I installed Windows 8 alongside of Ubuntu 13.04, After successful install I found Another Partition is displayed.
Previous My Hard disk Partitioned in 4. One Is Dell Utility, Second One is Linux OS, third one is Linux Data Drive and Fourth one is for Windows 8.

After installing Windows 8 the Linux OS partition is in display, Please see the screenshot so that you can understand my query better.

[IMG]http://s24.postimg.org/7kd0zm251/My_Computer_Screen_Shot.png[/IMG]


My question is How to hide this drive?

---

### Post by Gilad_Pellaeon on 2013-08-12
I would think that if it's an ext4 formatted partition Windows 7 wouldn't even show it as an accessible drive letter so i'm curious why it's even showing up.

---

### Post by ajgreeny on 2013-08-12
I do not see what you are trying to figure out from your question, nor can I tell which partition is which, or if you actually have two physical disks or just one divided into partitions.

As Gilad_Pellaeon says, windows can not see what linux partitions are; they are usually just described as unknown, healthy partitions in windows disk management utility.  It will be much more helpful to see a screenshot of gparted running from either your installed Ubuntu OS or from a live USB/DVD, as that will give a much better opportunity to really see what each partition really is.

Can we also see the output from terminal in ubuntu of the command ```
sudo parted -l
```

---

### Post by 3rdalbum on 2013-08-13
That looks like your Dell recovery partition. Perfectly normal. As others have said here, Windows can't recognise Linux partitions so it will never display them.

---

### Post by nachinew on 2013-08-13
> **ajgreeny said:**
> I do not see what you are trying to figure out from your question, nor can I tell which partition is which, or if you actually have two physical disks or just one divided into partitions.

As Gilad_Pellaeon says, windows can not see what linux partitions are; they are usually just described as unknown, healthy partitions in windows disk management utility.  It will be much more helpful to see a screenshot of gparted running from either your installed Ubuntu OS or from a live USB/DVD, as that will give a much better opportunity to really see what each partition really is.

Can we also see the output from terminal in ubuntu of the command ```
sudo parted -l
```
 
Here is my gparted output


[IMG]http://s16.postimg.org/3kw0tvzfp/Gparted.png[/IMG]

---

### Post by nachinew on 2013-08-13
> **3rdalbum said:**
> That looks like your Dell recovery partition. Perfectly normal. As others have said here, Windows can't recognise Linux partitions so it will never display them.

Thanks, may be its Dell Utility If it is Dell Utility how to hide this drive

---

### Post by Slug71 on 2013-08-13
That is SDA2 = FAT32  that is showing up. 
Looks look your Recovery partition.

SDA1 appears to be dell utility and SDA4 your Windows install.

---

### Post by Mark Phelps on 2013-08-14
Your Windows screenshot is only showing sda2 and sda4.  It's not showing sda1 because that's probably not mounted, and it won't show the Linux partition because it can't read Linux filesystems.  There does not appear to be anything wrong -- you're misinterpreting the display.

---

