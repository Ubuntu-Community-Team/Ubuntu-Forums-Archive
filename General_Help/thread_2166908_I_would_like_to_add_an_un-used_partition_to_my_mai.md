---
title: "I would like to add an un-used partition to my main Ubuntu partition"
date: 2013-08-11
forum: General Help
---

### Post by jacob5 on 2013-08-11
Hi, 

I currently have an unused NTFS partition that has absolutely nothing on it. I would like to add this partiton to my main Ubuntu partition so that I have more availible space for the file system. What is the best way to do this? 

Any help is very much appreciated. :)

---

### Post by ibjsb4 on 2013-08-11
First open up gparted and take/post a pic of you partitions.

If you don't have gparted installed:

```
sudo apt-get install gparted
```

---

### Post by jacob5 on 2013-08-11
> **ibjsb4 said:**
> First open up gparted and take/post a pic of you partitions.

If you don't have gparted installed:

```
sudo apt-get install gparted
```


Hi, ibjsb4. Thank you for your reply!

For some reason I cannot upload the screenshot. The attatchment manager gives me an error message for the file.

---

### Post by The-Server-4dmin on 2013-08-11
I have not used the GUI [COLOR=#000000][FONT=Ubuntu Mono]gparted, but I think```
 [/FONT][/COLOR]fdisk -l
``` will do the same thing--list the disk.

---

### Post by bab1 on 2013-08-11
> **The-Server-4dmin said:**
> I have not used the GUI [COLOR=#000000][FONT=Ubuntu Mono]gparted, but I think```
 [/FONT][/COLOR]fdisk -l
``` will do the same thing--list the disk.

If you are not the root user then you need to use *sudo* like this```
sudo fdisk -l
```

To be consistent with gparted while using the GUI, you can use the CLI  terminal command like this```
sudo parted -l
```
The output is easier to read.

---

### Post by jacob5 on 2013-08-11
> **The-Server-4dmin said:**
> I have not used the GUI [COLOR=#000000][FONT=Ubuntu Mono]gparted, but I think[/FONT][/COLOR]```
fdisk -l
``` will do the same thing--list the disk.

Hi, and thank you for your reply! When I use the ```
fdisk -l
``` command, it does not show the same thing as GParted does.

---

### Post by The-Server-4dmin on 2013-08-11
I always do a ```
sudo -i
``` before doing any system work.

---

### Post by jacob5 on 2013-08-11
> **bab1 said:**
> If you are not the root user then you need to use *sudo* like this```
sudo fdisk -l
```

To be consistent with gparted while using the GUI, you can use the CLI  terminal command like this```
sudo parted -l
```
The output is easier to read.

Hi, bab1. Thank you for sharing that, but I got the screenshot image from GParted uploaded. :)

The highlighted partition (E) is the one that I would like to add to my Ubuntu ext4 partition (the only ext4 partition listed). 


 [ATTACH=CONFIG]245292[/ATTACH]

---

### Post by jacob5 on 2013-08-11
> **The-Server-4dmin said:**
> I always do a ```
sudo -i
``` before doing any system work.

What does that command do?

---

### Post by bab1 on 2013-08-11
> **The-Server-4dmin said:**
> I always do a ```
sudo -i
``` before doing any system work.

So are you just talking to yourself here?  The OP doesn't know that.  :-(

---

### Post by bab1 on 2013-08-11
> **jacob5 said:**
> What does that command do?

Are you asking what the command *sudo * is for?  This is the command to allow you to execute a command using the root user.  Both fdisk and parted are executable only by the user root.  If you use sudo without specifying a user it assumes (defaults to) that you mean to use the command as root 

If you want to combine partitions they need to be side by side (contiguous).  You will need to remove the data on the partition(s) that are next to the partition that you want to enlarge.

See here for more information:
   [[COLOR="#0000FF"]http://askubuntu.com/questions/66000/how-to-merge-two-partitions[/COLOR]]("http://askubuntu.com/questions/66000/how-to-merge-two-partitions")

Back up all your data before you try any of this.  None of this is failsafe.

---

### Post by jacob5 on 2013-08-21
> **bab1 said:**
> Are you asking what the command *sudo * is for?  This is the command to allow you to execute a command using the root user.  Both fdisk and parted are executable only by the user root.  If you use sudo without specifying a user it assumes (defaults to) that you mean to use the command as root 

If you want to combine partitions they need to be side by side (contiguous).  You will need to remove the data on the partition(s) that are next to the partition that you want to enlarge.

See here for more information:
   [[COLOR=#0000FF]http://askubuntu.com/questions/66000/how-to-merge-two-partitions[/COLOR]]("http://askubuntu.com/questions/66000/how-to-merge-two-partitions")

Back up all your data before you try any of this.  None of this is failsafe.

Hi, bab1. Thank you for replying. It seems that I overlooked my notification of your reply, so I am just now getting it. I was referring to the ```
-i
``` part of the ```
sudo
``` command. 

I actually solved my problem, and I am happy to say that my disk is now organized the way I want it to be. It took me a while, but I realized that the partitions I wanted to combine needed to be contiguous. However, it would have been a lot less time consuming if I would have been aware of your reply. :/

But again, thank you for replying!

---

