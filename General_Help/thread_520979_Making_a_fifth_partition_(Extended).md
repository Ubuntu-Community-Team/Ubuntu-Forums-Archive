---
title: "Making a fifth partition (Extended)"
date: 2007-08-08
forum: General Help
---

### Post by bronze on 2007-08-08
Hi, at the moment, my harddrive (only have 1) is divided like this:
1. Windows XP
2. Ubuntu root (/)
3. SWAP
4. Ext3 home (/home)
I have some unallocated space at the end of the harddrive (after the /home partition) that I want to format into FAT32 for temporary sharing between Windows XP and Ubuntu. All of the 4 above are "primary", and I can only have 4 primary partitions on one harddrive, so how can I create the 5th partition without losing any data? I've read a bit about using an extended partition but I don't know how it's done. Can someone please explain what I need to do?

-bronze

---

### Post by ruibernardo on 2007-08-08
Hi bronze,

I think that you should have done this before you had 4 primary partitions. Now you can't create any extended one.

Maybe you can do the following:

Backup your home and root (if you need to), delete all partitions but the windows one and create an extended partition.

Install Ubuntu inside the extended partition and restore your backups. You will have problems about GRUB (you have to set the numbers of the partitions it calls) and the UUIDs in /etc/fstab, but with a LiveCD you may know the new UUIDs. Just mount them in the LiveCD and run the "sudo blkid" in a console and change the /etc/fstab in the restored system with the new UUIDs.

I think that's it, but maybe someone should confirm this.

---

### Post by meierfra on 2007-08-08
Delete the swap partition. Create an extended partition. Move the unallocated partition to the extended partition. Create a Fat32 and  a swap partition inside the extended partition.

If you  need more detailed help, let me know. I recommend using the gparted Live CD.

---

### Post by merlinus on 2007-08-08
I would not be certain that deleting /swap, making an extended partition, and then creating /swap and another logical partition would give enough free space, unless /swap is larger than the recommended 1.5G or so.

And even in doing that, the partition numbers and UUIDs would change, necessitating editing of /etc/fstab.

So I would basically agree with epimeteo.

-merlin

BTW, blkid does not need sudo to run, unlike sudo fdisk -l.

---

### Post by ruibernardo on 2007-08-08
Oh, thats a much simpler solution!!! A great one! Didn't though about that...

---

### Post by meierfra on 2007-08-08
> would give enough free space,

It depends how large the unallocated space at the end of the drive is. (Otherwise he also has to shrink some of the other partitions)

He  should be able to move the unallocated partition to the swap partition by first increasing the  home partition at the end, and then  shrink it and leave  unallocated space at the front.

---

### Post by meierfra on 2007-08-08
> And even in doing that, the partition numbers and UUIDs would change, necessitating editing of /etc/fstab..

Yes, but seems easier than erasing  the home and root partition.

---

### Post by ruibernardo on 2007-08-08
> **meierfra said:**
> It depends how large the unallocated space at the end of the drive is. (Otherwise he also has to shrink some of the other partitions)

He  should be able to move the unallocated partition to the swap partition by first increasing the  home partition at the end, and then  shrink it and leave  unallocated space at the front.
That part of moving the beginning and the end of the partitions gives me the creeps...

I  strongly recommend to backup the home partition first.

---

### Post by meierfra on 2007-08-08
> **epimeteo said:**
> 
I  strongly recommend to backup the home partition first.

Definitely!

---

### Post by bronze on 2007-08-14
So basically I have no way of backing up all the data in root and home, so I'm gonna have a shot at the swap solution. Can anyone explain it in details. I don't really know how to "change the UUIDs" or anything like that.
[IMG]http://bildr.no/image/94805.jpeg[/IMG]
RIGHT CLICK ON THE PICTURE AND SELECT "VIEW PICTURE".

Swap: ~2GB
Unallocated: ~25GB

By the way, I've got the gparted CD and a lot of live CDs to help me out (ubuntu, pclinuxos, kubuntu).

EDIT: The unallocated space after C:Windows XP is there because I shrunk the Ubuntu root partition and increased Windows XP, but I didn't use all of the shrunk space so there's ca. 3 GBs there.

---

### Post by meierfra on 2007-08-14
The picture  you included is to small to read.

Before I give you detailed instruction I would like to have   look at your partition table.
Go to 

System->Administration->Gnome Partition Editor.

and take a snapshot of the screen (Press the  Prnt Scrn key)


Then post the snap shot.

---

### Post by bronze on 2007-08-14
Just right click on the picture and select "View picture".

---

### Post by meierfra on 2007-08-14
I was just ready to send you the instruction when I realized that there is a safer option:

Delete the swap space and leave it unallocated.

Create  an extended  partition from the unallocated space at the end.
Use the extended partition for your Fat32 and a new swap partition.

This way we will waste about  5GB ( the two unallocated partitions) But we won't have to mess with your home partition.  (and you can still move it at some later point when you feel more risky)

Let me know what you prefer.

---

### Post by meierfra on 2007-08-14
Here are the instruction for the safer option (leaving 5 GB unallocated):

Boot from the gparted Live CD. Follow the instructions on the screen. If you have a choice between "gparted .." and "gparted ... more options" choose "gparted ... more options"

Wait for the partition screen to appear.

Right click the "swap" partition and select "delete"

Right click the  last unallocated partition and select "New".
In the pop up window under "Create as" choose "Extended Partition".
Don't change anything else and click on "Add"

RightClick the "unallocated partition" inside the extended partition and select "New"
Drag the right handle to shrink the partition by 2GB.
Under "File System " choose "Fat32".
Click Add.

RightClick the new "unallocated partition" and select "New"
Under "File System " choose "Linux/Swap."
Click Add.

Click Apply.
Wait for the partitioning to be done (might take a while)

Exit and reboot.

There is a some chance that you computer fails to load ubuntu, since the addresses of the partitios changed. If this happens boot from the ubuntu live cd and come back here for help.

If everything goes well, you still might comeback here to get help on mouting your new fat32 partition and the swap partition.

---

### Post by Abra on 2007-11-17
I was looking for that. Using your instructions I have 4 os' and 7-8 partitions (I don't know exact number :P) atm.
Thank you ver much meierfra...

---

### Post by meierfra on 2007-11-17
> Thank you ver much meierfra...

You are welcome.

Since you delete and then recreated "swap" there is some chance that ubuntu no longer recognizes the swap partition. 

open a terminal and type

```
free
```

The last line of the output should look  something like

Swap:      2273156          0    2273156

If it says 

Swap      0            0                0

come back here and I show you how to fix  "swap".

---

