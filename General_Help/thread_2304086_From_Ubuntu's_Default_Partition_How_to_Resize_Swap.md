---
title: "From Ubuntu's Default Partition How to Resize Swap"
date: 2015-11-24
forum: General Help
---

### Post by snarkyCoder on 2015-11-24
By being new to this, I installed ubuntu with the default partition table to not mess around with it.
This is the partition:
[ATTACH=CONFIG]265751[/ATTACH]

Since the hard drive it's a SSD and I have 16GB of RAM I want to know how could I resize the swap partition.
Also I have swapiness set at 0 but I would want to resize I could use some of that space later.


[LIST]
[*]Could someone explain me how to resize the swap partition?
[*]If I would reinstall ubuntu, could I go without a swap partition?
[*]What could be the best partition table for using just a SSD?
[/LIST]

---

### Post by mcduck on 2015-11-24
You'll need to do the partition editing while running from a live USB, as you can't edit partitions that are in use at the moment.

Then, your swap partition is a logical one, sitting inside extended partition (sda2). This means you'll also need to resize & move the extended partition before you can grow your / partition to use the freed space. On the other hand, since it's just swap there so no need to worry about loosing any information, you could just delete it and create a new one.

So, two options:

1. Shrink sda5 -> shrink sda2 to match sda5 -> move sda2 to end of disk -> grow sda1 to fill the space.

or 2. delete sda5 -> delete sda2 -> grow sda1 leaving enough space for new smaller swap -> create new sda2 and assign it as swap. (no need to do the extended partition since you only have two partitions and probably won't want  ore on that drive)

Which ever way you choose, make sure that your fstab has correct information for the swap partition afterwards.

With 16GB of RAM you probably won't really ever use the swap, at least unless you want to hibernate your computer, but as the Linux kernel uses a little bit of swapping for generic memory management tasks, and some programs might expect you to have swap, having a small 1GB swap partition might be worth it.

---

### Post by snarkyCoder on 2015-11-24
> **mcduck said:**
> You'll need to do the partition editing while running from a live USB, as you can't edit partitions that are in use at the moment.

Then, your swap partition is a logical one, sitting inside extended partition (sda2). This means you'll also need to resize & move the extended partition before you can grow your / partition to use the freed space. On the other hand, since it's just swap there so no need to worry about loosing any information, you could just delete it and create a new one.

So, two options:

1. Shrink sda5 -> shrink sda2 to match sda5 -> move sda2 to end of disk -> grow sda1 to fill the space.

or 2. delete sda5 -> delete sda2 -> grow sda1 leaving enough space for new smaller swap -> create new sda2 and assign it as swap. (no need to do the extended partition since you only have two partitions and probably won't want  ore on that drive)

Which ever way you choose, make sure that your fstab has correct information for the swap partition afterwards.

With 16GB of RAM you probably won't really ever use the swap, at least unless you want to hibernate your computer, but as the Linux kernel uses a little bit of swapping for generic memory management tasks, and some programs might expect you to have swap, having a small 1GB swap partition might be worth it.

Thanks!
I will opt to do the option 1 :)
But in the case of option 2, Why is the extended partition not needed when only using 2 partitions?
How would I know if fstab has the correct information for the swap partition?

---

### Post by Bucky Ball on 2015-11-24
2Gb of /swap is normal. Are you intending to hibernate while using a heap of resources and with most of your RAM full? Doubtful. Do you intend for the machine to hibernate ever? With 16Gb of RAM you will probably barely ever touch the /swap, if ever.

Open all the programs you would normally use so you have a regular day-to-day setup you would use on your computer. Open a terminal and type 'top'. At the top of that read out you will find your RAM. How much is being used?

As per mcduck: I can almost guarantee you don't need anywhere near a 16Gb /swap. As I say, 2Gb is normal.

I would personally right click sda5 (swap) and 'swapoff', delete the swap and the extended partition, expand your / partition and leave 2Gb for a new /swap. Create a 2Gb swap. You will need to do this from a Live session.

Whatever you choose, let us know if you need help setting up the fstab. :)

PS: I have removed the large font in your first post. Please don't use it as it is considered shouting. Thanks. ;)

PPS: Yes, technically you can go without a /swap (if you are considering that more proof there is no need for that huge /swap you have now), but best to put one in there to keep Ubuntu happy (it can sometimes be problematic from what I've read and seen, but never tried it myself - you can switch swap off without issue, though, which I've done and forgot to switch back on again for a day and a half without issue). Bottom line: Have a 2Gb /swap.

---

### Post by snarkyCoder on 2015-11-24
> **Bucky Ball said:**
> 2Gb of /swap is normal. Are you intending to hibernate while using a heap of resources and with most of your RAM full? Doubtful. Do you intend for the machine to hibernate ever? With 16Gb of RAM you will probably barely ever touch the /swap, if ever.

Open all the programs you would normally use so you have a regular day-to-day setup you would use on your computer. Open a terminal and type 'top'. At the top of that read out you will find your RAM. How much is being used?

I can almost guarantee you don't need anywhere near a 16Gb /swap. As I say, 2Gb is normal.

I would personally right click sda5 (swap) and 'swapoff', delete the swap and the extended partition, expand your / partition and leave 2Gb for a new /swap. Create a 2Gb swap. You will need to do this from a Live session.

Whatever you choose, let us know if you need help setting up the fstab. :)

PS: I have removed the large font in your first post. Please don't use it as it is considered shouting. Thanks. ;)

PS: Yes, technically you can go without a /swap (if you are considering that more proof there is no need for that huge /swap you have now), but best to put one in there to keep Ubuntu happy (it can sometimes be problematic from what I've read and seen, but never tried it myself - you can switch swap off without issue, though, which I've done and forgot to switch back on again for a day and a half without issue).

Thanks!
I don't know how to set up the fstab hehe. Or can I change the partitions and later worry about the fstab? Or do I have to edit the fstab in the live session?
Have never put a desktop on hibernation not even suspend...After I'm done I turn them off.
Yeah, I won't be using swap. I have never used it with my kind of usage.
I used to use an old laptop with just 4 GB of RAM and never used all of it. The most I use is 3GB.
What I do in Ubuntu is web development so I am just using a browser and a text editor. 
I got 16GB of RAM because later I want to use this machine for audio production on a different SSD with anorther OS anyway.

---

### Post by Bucky Ball on 2015-11-24
> **snarkyCoder said:**
> ... can I change the partitions and later worry about the fstab? Or do I have to edit the fstab in the live session?

You only need to resize the / partition from the live session. You can do the rest from a regular boot, but may as well make the /swap while you are resizing the / partition in the live session.

Yes, do the partition manipulations first and when you're done boot to a live session. You may get an error that the fstab is wrong. Ignore and 'S'kip it. Once you're back at a desktop, open a terminal and give us the output of this command and the file the second one brings up:

```
sudo blkid
nano /etc/fstab
```

> **snarkyCoder said:**
> Have never put a desktop on hibernation not even suspend...After I'm done I turn them off.
Yeah, I won't be using swap. I have never used it with my kind of usage.
I used to use an old laptop with just 4 GB of RAM and never used all of it. The most I use is 3GB.
What I do in Ubuntu is web development so I am just using a browser and a text editor. 
I got 16GB of RAM because later I want to use this machine for audio production on a different SSD with anorther OS anyway.

Make it a 2Gb /swap, then. :)

---

### Post by snarkyCoder on 2015-11-24
> **Bucky Ball said:**
> You only need to resize the / partition from the live session. You can do the rest from a regular boot, but may as well make the /swap while you are resizing the / partition in the live session.

Yes, do the partition manipulations first and when you're done boot to a live session. You may get an error that the fstab is wrong. Ignore and 'S'kip it. Once you're back at a desktop, open a terminal and give us the output of this command and the file the second one brings up:

```
sudo blkid
nano /etc/fstab
```



Make it a 2Gb /swap, then. :)

It has been done!
I restarted and it shows like that. Why is there no Lock Icon in the swap partition? Do I have to do the swap on?
Below is the output to the commands you showed me. The fstab still show sda5 but now swap is on sda2

[ATTACH=CONFIG]265754[/ATTACH]

sudo blkid
```

/dev/sda1: UUID="a4ad35a6-3ed5-47e4-9b5f-081d80899f20" TYPE="ext4" 
/dev/sda2: UUID="6a2182b1-8762-46dd-a5ab-47b2cb6c3c09" TYPE="swap" 

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a4ad35a6-3ed5-47e4-9b5f-081d80899f20 /               ext4    noatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f572c64b-23bd-41f7-b4f5-b00bd315348f none            swap    sw              0       0


```

---

### Post by mcduck on 2015-11-24
> **snarkyCoder said:**
> Thanks!

But in the case of option 2, Why is the extended partition not needed when only using 2 partitions?

Bucky Ball pretty much answered everything else so I'll just cover this one...
The old MBR partitioning system only allows 4 *primary partitions*, or alternatively you can have 3 primary partitions and then one* extended partition*, which can then contain unlimited amount of *logical partitions*. So, the extended partition is only needed if you want to have more than 4 partitions on the drive.

Ubuntu's installer will, by default, make the / partition into a primary one, and then to make sure users wouldn't run into the primary partitions limit in the long run, creates extended partition and places everything else inside it. (This also helps a lot with dual-boot setups since Windows will also want one primary partition, plus any system restore partitions etc and you'd pretty soon reach the "4 primary partitions"-limit). But since it seems like you won't be needing more than those 2 partitions you'll be fine with just making those two into primary partitions. Which also removes some extra steps should you ever want to resize them.

---

### Post by snarkyCoder on 2015-11-24
> **Bucky Ball said:**
> -

Thanks!
I already updated the fstab file
I changed the old uuid that it have to the new one from blkid :)
Now the swap appears as on

> **mcduck said:**
> Bucky Ball pretty much answered everything else so I'll just cover this one...
The old MBR partitioning system only allows 4 *primary partitions*, or alternatively you can have 3 primary partitions and then one* extended partition*, which can then contain unlimited amount of *logical partitions*. So, the extended partition is only needed if you want to have more than 4 partitions on the drive.

Ubuntu's installer will, by default, make the / partition into a primary one, and then to make sure users wouldn't run into the primary partitions limit in the long run, creates extended partition and places everything else inside it. (This also helps a lot with dual-boot setups since Windows will also want one primary partition, plus any system restore partitions etc and you'd pretty soon reach the "4 primary partitions"-limit). But since it seems like you won't be needing more than those 2 partitions you'll be fine with just making those two into primary partitions. Which also removes some extra steps should you ever want to resize them.

So extended acts as a container then for other partitions.
Thanks for the explanation. There is a lot of info but sometimes not explained as well.

Thank you guys!

---

### Post by Bucky Ball on 2015-11-24
Well done fixing all this up while I slept! :)

... and for marking as solved. Enjoy the ride. :)

---

