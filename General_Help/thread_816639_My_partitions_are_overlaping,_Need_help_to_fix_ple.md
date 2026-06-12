---
title: "My partitions are overlaping, Need help to fix please."
date: 2008-06-02
forum: General Help
---

### Post by Tanjer1588 on 2008-06-02
I just upgraded to 8.04 over the weakend and wanted to clear up some space on my system and found out my partitions are all wacky.

```

/dev/sda1               1        8336    66958888+  83  Linux
/dev/sda2   *        8337       14073    46082452+   7  HPFS/NTFS
/dev/sda3           14074       14593     4176900    5  Extended
/dev/sda4           14441       14593     1228941   82  Linux swap / Solaris
/dev/sda5           14074       14440     2947864+  82  Linux swap / Solaris

```

As you can see, /dev/sda4 is overlaping in the end of /dev/sda3 and /dev/sda5 is overlaping it as well.... i dont know how in the world i did this but it has to have been something to do with updating to 8.04 when i run GParted or QTParted they both say there is a problem with the partitions something about "cannot have overlaping partitions" so i need some help with this if you can, is there a way that i can go in and change up some stuff in grub or something or if i can edit my fdisk

thank you.

---

### Post by jimv on 2008-06-02
sda3 is an extended pratition...which, simply put, is a partition that you can make partitions inside of.  You can only have a maximum of 4 primary partitions on a drive, and if you want more partitions than that, you make an extended partition, and then put your additional partitions inside of it.

---

### Post by geirha on 2008-06-02
Indeed. /dev/sda4 should not be inside an extended partition. I think your best bet is to delete sda3, sda4 and sda5. They are fairly safe to delete since they don't contain any useful data.

If you boot the liveCD and open the partition editor (gparted) are you able to delete the partitions from there? If so, do so and create a new swap partition in their place.

After that you need to update /etc/fstab to use the new swap partition by replacing the UUID-part of the line containing swap in the third field:
```
UUID=<hexadecimal-sequence> none swap sw 0 0
```
You find the new UUID by running the following command in a terminal: ```
sudo blkid
```

EDIT: Please make sure to backup valuable data from /dev/sda1 and /dev/sda2 first. You'll probably be fine, but things CAN go wrong.

---

### Post by VMC on 2008-06-02
You confused us by saying that your partitions are overlaping. They are not. What you have is two swap partitions inside an extended partition.
 You Linux /dev/sda1 partition looks okay. 
Just do as suggested above and delete the extended and rebuild your swap.

---

### Post by Tanjer1588 on 2008-06-02
when i  booted from the live cd i got the same problem with gparted it said that my whole drive was empty and said something about cannot have overlaping partitions. Is there a way to log in as root and deleate the partitions that way?

---

### Post by geirha on 2008-06-02
sda1-4 are primary partitions. Logical partitions start counting from 5.
I.e. if you have one primary partition, one extended partition, and one logical partition inside the extended, you would have the partitions /dev/sda1, /dev/sda2 and /dev/sda5 respectively. So, /dev/sda4 should NOT lie inside an extended partition.

@Tanjer1588:
You might have luck using fdisk. If you run ```
sudo fdisk /dev/sda
``` from the live session, and then from the new prompt, type «m» to list commands, type «p» to print the partition table (do this often), and «d» to delete partitions. If you do something wrong, don't panic, just type «q» to quit, and your changes will be discarded. Nothing will be done before you type «w» to write your changes.

---

### Post by Tanjer1588 on 2008-06-02
> **geirha said:**
> sda1-4 are primary partitions. Logical partitions start counting from 5.
I.e. if you have one primary partition, one extended partition, and one logical partition inside the extended, you would have the partitions /dev/sda1, /dev/sda2 and /dev/sda5 respectively. So, /dev/sda4 should NOT lie inside an extended partition.

@Tanjer1588:
You might have luck using fdisk. If you run ```
sudo fdisk /dev/sda
``` from the live session, and then from the new prompt, type «m» to list commands, type «p» to print the partition table (do this often), and «d» to delete partitions. If you do something wrong, don't panic, just type «q» to quit, and your changes will be discarded. Nothing will be done before you type «w» to write your changes

ok thank you very much i will try this right when i get back to my computer i will let you know how it go's thank you very much

---

### Post by Tanjer1588 on 2008-06-03
> **geirha said:**
> Indeed. /dev/sda4 should not be inside an extended partition. I think your best bet is to delete sda3, sda4 and sda5. They are fairly safe to delete since they don't contain any useful data.

If you boot the liveCD and open the partition editor (gparted) are you able to delete the partitions from there? If so, do so and create a new swap partition in their place.

After that you need to update /etc/fstab to use the new swap partition by replacing the UUID-part of the line containing swap in the third field:
```
UUID=<hexadecimal-sequence> none swap sw 0 0
```
You find the new UUID by running the following command in a terminal: ```
sudo blkid
```

EDIT: Please make sure to backup valuable data from /dev/sda1 and /dev/sda2 first. You'll probably be fine, but things CAN go wrong.

Ok so i used Fdisk and edited the partitions so that sda3,4,and 5 were gone and i made one in the spot of 3 used the default size, and gave it the right id so that it is a swap partition. When i used blkid i get this...
```

/dev/sda1: UUID="5b0e0087-2af9-4e03-b957-ce7933782e83" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="061830FE1830EE75" TYPE="ntfs" 

```

So where is /dev/sda3 for my swap? i need the codes so i can put it in my fstab right? i figured the part of fstab i have to change is this ...
```


# /dev/sda6
UUID=36623ca7-be17-4ddb-a787-dd8265347c93 none            swap    sw              0       0

```
I have to change /dev/sda6 to /dev/sda3 right? cus thats where i put it. and i have to change the UUID to the one i would get from blkid if my /dev/sda3 showed up right? im a little lost

allso when i booted up my system and i was watching all the text that when by when it loads up i notced on that passed by said something about my swap and it said "FAILD" in red.

---

### Post by geirha on 2008-06-03
blkid probably needs a reboot to be able to see the new partition then, though your system should work without a swap partition. Anyway after booting up your system (with or without a working swap partition) try running ```
sudo blkid
``` in a terminal. It should now list an UUID for your new swap. Alternatively you can use /dev/sda3 instead of UUID, but UUID is preferred.
```
/dev/sda3 none            swap    sw              0       0
```

After editing fstab, run ```
sudo swapon -a
``` to mount the swap. It should then be listed if you run ```
swapon -s
# and/or
free
```

EDIT: Oh one more thing. Did you make the new swap partition using fdisk or gparted? A swap partition needs to be formatted. gparted does this automatically, but fdisk doesn't. If you did create it in fdisk, you'll need to run ```
sudo mkswap /dev/sda3
``` as well. And then it should also get an UUID.

---

### Post by Tanjer1588 on 2008-06-03
Thanks for your help guys i got it working now and im not having any problems with it.

blkid stoped working alltogether for me now i dont know whats up with it, but i edited the fstab to /dev/sda3 for the swap, it should work for now till i can change it again. Thanks for all your help guys.

---

