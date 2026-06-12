---
title: "partitioning nightmare"
date: 2007-02-02
forum: General Help
---

### Post by DMAthlon on 2007-02-02
ok so i used paragon partitioner in Hiren's BootCD and deleted one of my NTFS partitions so i could make it FAT32 to store stuff for Linux AND windows. and n ow that partition doesnt show as mounted in linux. how do i mount it?

and then i also added on about 10GB when i did the partitioning to the beginning of my primary linux partition (Ext3) and so the partitioner copied all the data to the new empty space at the beginning of the drive but it seems that the old data is stall there and i have the same amount of free space as before adding 10GB more.


how do i get it to do as i wanted? thanks for you help!

---

### Post by DMAthlon on 2007-02-02
this is QTParted displays which is what everything should look like: [IMG]http://img.photobucket.com/albums/v349/Shouryuu/Screenshot-qtpartedv0.png[/IMG]

instead, it doesnt even show the FAT32 as mounted and i should have 12GB free instead of 1.3 GB free

---

### Post by az on 2007-02-02
> **DMAthlon said:**
> ok so i used paragon partitioner in Hiren's BootCD and deleted one of my NTFS partitions so i could make it FAT32 to store stuff for Linux AND windows. and n ow that partition doesnt show as mounted in linux. how do i mount it?

You need to add the appropriate entry in /etc/fstab

And why use anything but a free-libre partitionner?

> **DMAthlon said:**
> 
and then i also added on about 10GB when i did the partitioning to the beginning of my primary linux partition (Ext3) and so the partitioner copied all the data to the new empty space at the beginning of the drive but it seems that the old data is stall there and i have the same amount of free space as before adding 10GB more.
how do i get it to do as i wanted? thanks for you help!

You extended the partition, but not the filesystem on it.

Use Gparted on the live cd to extend the filesystem.  You can also just use growfs from the command line.  I don't know offhand the syntax, but it should be pretty straightforward.

---

### Post by DMAthlon on 2007-02-02
> **az said:**
> You need to add the appropriate entry in /etc/fstab

i have an /etc folder in / but there's no /fstab folder in /etc.

once i figure that out then how do i mount it?

thanks captain kirk!

---

### Post by Vox754 on 2007-02-02
Oh man, you've got to take things easy.
I guess you are one of those guys that start with Ubuntu and ask many questions (make a lot of threads) before even attempting to research and try to solve things by themselves.

Give the search buttons a try, you are not the first one asking this.

A quick answer: "/etc/fstab" is not a folder.
Well, "/etc/" is a folder, but "fstab" is a file, a text file.
You see, in Unix there is no need for files to have extensions. You'll find lots of Linux text files lacking any extension such as ".txt".

1. Make sure you partitioned correctly your drive.
2. Save changes.
3. Then search in the documentation for "mount filesystems".

Basically you type in the terminal
```
mount -a
```
provided your "/etc/fstab" is written correctly, otherwise you'll have to manually edit it with
```
sudo gedit /etc/fstab
```

---

### Post by DMAthlon on 2007-02-02
what? You think i havent TRIED looking elsewhere and tried doing this **** myself? i've only been linuxing for a few months so cut me some slack Dr. "I know all things linux." you didnt know jack **** about this at one point or another in your life too.

i realized my fault that fstab was a file - i just forget that text files dont need file extensions. it is a pretty easy misconception though considering it you were telling me to go to navigate to my desktop you'd say "/home/user/Desktop"

i figured i wasnt the first one asking this anyways but the searches in this forum turn up little relevant information

----

perhaps you could explain things to help rather than explaining things to make me look stupid. could you maybe tell me what specific things to edit in fstab, with what information and i would have an easier time figuring it out.

thanks ultra mega ubuntu god for helping! [/sarcasm]

---

