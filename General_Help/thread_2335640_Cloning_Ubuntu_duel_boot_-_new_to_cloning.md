---
title: "Cloning Ubuntu duel boot - new to cloning"
date: 2016-08-30
forum: General Help
---

### Post by petenoob on 2016-08-30
So i have install a duel booted Ubuntu Server 16.04 on a separate partition on my HD intended to be used as a webserver. Windows 8 is the other OS. What I want to do is clone my Ubuntu so that if anything goes wrong, I can just reinstall from the clone, an exact copy of the original, is that how it works!?

I am new to cloning a "partition" as I have never done it before. I watched some youtube videos and it looked easy with clonezilla, but since my set-up is dual boot I am unsure if it is going to be difficult to get everything to work again. Can anyone give me pointers what I should be looking out for and initials steps? 

Another question, if I am cloning to an USB external drive, does that mean I would be able to run the cloned linux from that?

Thanks!

---

### Post by C.S.Cameron on 2016-08-31
Clonezilla is safer than cc for cloning and easier to use.
The boot stuff is not located on a partition but on the root.
If you want to boot the clone you will need to clone the entire drive.
This will require a USB drive larger than your internal drive.
You can remove the Windows partition later, I'm not sure if it will work on an external drive.

---

### Post by sudodus on 2016-08-31
There are basically three alternatives of backups (and several tools for each of them).

1. Cloning the drive to another drive of at least the same size.

***Clonezilla*** can do this, and is a good alternative. Ubuntu can boot from the drive when connected via USB, but Windows is made to not boot that way, but if you replace your internal drive by the cloned copy, both operating systems will boot.

2. Creating a compressed image, which can be expanded into a cloned copy in the same drive or another drive of at least the same size. The advantage of this method is the compression and easy of management. The compressed image is a file or a directory with a set of files, and they are easy to copy and store. ***Clonezilla*** can do this task too. I use Clonezilla like this for my system drive and for single partitions.

3. Making a backup, which is neither a complete clone nor a compressed image (of a complete clone).

- You can synchronize or or more partitions or directories (directory trees). This means that the backup consists of the same files. Files will be removed from the image, if removed from the original drive. Unison is a tool for this purpose. I use ***Unison*** like this for my data partition.

- You can use a backup system with separate copies of the content in partitions or directories.

- You can use an incremental backup system which adds new files from the original partition(s) or directory tree(s) to the backup location. There are many tools with graphical user interface as well as tools that you use via the command line. I use the command line tool ***rsync*** like this.

-o-

For all kinds of backup it is important to test it. ***Test that it really works to restore your system from the backup*** (without overwriting your original drive). It means that you need 'a third drive' for testing. Later on you can use that drive either as a second backup target drive, or for other purposes.

---

### Post by petenoob on 2016-09-03
Thank you!

---

### Post by petenoob on 2016-09-03
> **sudodus said:**
> There are basically three alternatives of backups (and several tools for each of them).

1. Cloning the drive to another drive of at least the same size.

***Clonezilla*** can do this, and is a good alternative. Ubuntu can boot from the drive when connected via USB, but Windows is made to not boot that way, but if you replace your internal drive by the cloned copy, both operating systems will boot.

2. Creating a compressed image, which can be expanded into a cloned copy in the same drive or another drive of at least the same size. The advantage of this method is the compression and easy of management. The compressed image is a file or a directory with a set of files, and they are easy to copy and store. ***Clonezilla*** can do this task too. I use Clonezilla like this for my system drive and for single partitions.

3. Making a backup, which is neither a complete clone nor a compressed image (of a complete clone).

- You can synchronize or or more partitions or directories (directory trees). This means that the backup consists of the same files. Files will be removed from the image, if removed from the original drive. Unison is a tool for this purpose. I use ***Unison*** like this for my data partition.

- You can use a backup system with separate copies of the content in partitions or directories.

- You can use an incremental backup system which adds new files from the original partition(s) or directory tree(s) to the backup location. There are many tools with graphical user interface as well as tools that you use via the command line. I use the command line tool ***rsync*** like this.

-o-

For all kinds of backup it is important to test it. ***Test that it really works to restore your system from the backup*** (without overwriting your original drive). It means that you need 'a third drive' for testing. Later on you can use that drive either as a second backup target drive, or for other purposes.

Lots of details. Thanks very much!

I am going to try option 2 and see how it pans out.

---

### Post by petenoob on 2016-09-04
Well I did a clone of my Ubuntu partition but when I try to clone that to an external SSD it seems that Clonezilla doesn't recoginise it is there? The OS sees it though (sdb)

[https://s10.postimg.io/kway3a8m1/Screenshot_from_2016_09_04_12_47_40.png](https://s10.postimg.io/kway3a8m1/Screenshot_from_2016_09_04_12_47_40.png)

But in Clonezilla

[https://s16.postimg.io/siq10rvo5/Picture_result.jpg](https://s16.postimg.io/siq10rvo5/Picture_result.jpg)

External SSD is connected I see a light, also recognized in boot. BTW my linux OS is in sd7 and the mount image is in sd5. Help anyone?

---

### Post by wildmanne39 on 2016-09-04
*Thread moved to **General Help**.*

Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

### Post by sudodus on 2016-09-04
> **petenoob said:**
> Well I did a clone of my Ubuntu partition but when I try to clone that to an external SSD it seems that Clonezilla doesn't recoginise it is there? The OS sees it though (sdb)

[https://s10.postimg.io/kway3a8m1/Screenshot_from_2016_09_04_12_47_40.png](https://s10.postimg.io/kway3a8m1/Screenshot_from_2016_09_04_12_47_40.png)

But in Clonezilla

[https://s16.postimg.io/siq10rvo5/Picture_result.jpg](https://s16.postimg.io/siq10rvo5/Picture_result.jpg)

External SSD is connected I see a light, also recognized in boot. BTW my linux OS is in sd7 and the mount image is in sd5. Help anyone?

/dev/sdb seems to be a drive without any partition. Clonezilla cannot mount anything on it.

At this stage you should mount the partition,

- in the backup case: where you want to create an image,
- in the restore case: where you have saved your image, maybe the image is in sda5(?)

Don't bury the Clonezilla image deeply in a directory tree, the image directory should be in the top directory of the partition, or maybe better: one subdirectory level down. Otherwise Clonezilla will not find it.

---

### Post by petenoob on 2016-09-04
Strange because I was sure I did a partition beforehand, anyway did a partition again in ext4 and Clonezilla still cannot see my external SSD sdb

[https://s9.postimg.io/qz9bionzj/Screenshot_from_2016_09_05_09_36_55.png](https://s9.postimg.io/qz9bionzj/Screenshot_from_2016_09_05_09_36_55.png)

[https://s11.postimg.io/eg0dhjn4j/Screenshot_from_2016_09_05_09_26_04.png](https://s11.postimg.io/eg0dhjn4j/Screenshot_from_2016_09_05_09_26_04.png)

[https://s14.postimg.io/bucucnptd/pic1.jpg](https://s14.postimg.io/bucucnptd/pic1.jpg)

[https://s10.postimg.io/l6l9igyih/pic2.jpg](https://s10.postimg.io/l6l9igyih/pic2.jpg)

Also my clonezilla images are in the top directory already in sda5

---

### Post by sudodus on 2016-09-05
You should mount the partition, where you have the Clonezilla image, and select the directory above the image itself. So with your Clonezilla images in the top directory, stay at the top directory. In the next step you will be able to select the clonezilla image to restore.

I made a restore a week ago, and it was successful, so I know that it works (in the version that I use, and I think this behaviour is the same in newer versions). Notice that you must restore to the same partition number as the original partition, that you cloned (but the drive letter can be different).

-o-

If you give up with Clonezilla, there are other tools, that might work better for you. If this is the case, please tell us, and we can help you with another tool.

---

