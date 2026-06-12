---
title: "Adding Additional Drive To Software RAID5 Array"
date: 2008-02-08
forum: General Help
---

### Post by fjgaude on 2008-02-08
After several kernal updates during the last year or so, is it possible to add a drive to an existing raid5 array? If so, how?

Thank you for any reply.

---

### Post by fjgaude on 2008-02-14
Well after much playing around I finally got my raid array to go from **three** drives to **four.**

After reading that kernel 2.6.20 and later could add devices to grow a raid5 array I kept trying until the magic commands were found.

First the drive has to be added as a spare and then added by growing the array (mine is md32):

```
sudo mdadm /dev/md32 --add /dev/sd[nn]
```

Check to see that it got added as a spare, using the -D command:

```
sudo mdadm -D /dev/md32
```

Then go for it:

```
sudo mdadm -G --raid-devices=4 /dev/md32
```

A message outputs: Having to save 384K of critical data. Something like that.

Then its good to use this to watch the array assemble and grow:

```
sudo watch cat /proc/mdstat
```

Took six hours for my 4 times 300G array to re-assemble. Seems there is nothing wrong with using the array while it does its thing. After that you might wish to update your mdadm.config file in /etc/mdadm.

```
sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
``` #create new mdadm.conf
```
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```   #scan RAID device and appends results to the /etc/mdadm.conf file

Happy array growing. Let us know how things go.

---

### Post by matthodge on 2008-05-13
Hi fjgaude,

Thats a very nice guide. My array is now being updated with the 4th disk now (RAID5 with 4x500GB SATA's).

It is going to take a while until it completes.

My question is how does the partitioning work?

I already have a 1TB JFS partition on the drive which is full of data (about 10gb free). Now that this new disk is added, will that increase the JFS partition size to 1.5TB automaticlly? If not is there a way to increase the size of the JFS partition? Im not using LVM on my drives.

Thanks in advance.

---

### Post by matthodge on 2008-05-18
Just as a follow up post.

I added the new disk to my RAID array. It took about 4days to complete haha (there was 950GB of data on the array). 

After it finished i ran the following command : 

```
mount -o remount,resize /home
```

And it stretched the partition across the rest of the free space.

Yay for JFS partitions :)

---

