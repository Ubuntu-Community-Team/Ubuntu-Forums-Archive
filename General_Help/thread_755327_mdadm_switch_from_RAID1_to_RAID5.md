---
title: "mdadm switch from RAID1 to RAID5"
date: 2008-04-14
forum: General Help
---

### Post by lobo235 on 2008-04-14
I currently have two 500GB drives setup in a RAID1 array. Everything is working fine right now but I am going to be purchasing another 500GB drive and I would like to set the three drives up as a RAID5 array. I have been thinking through the steps that I will need to take to accomplish this and here is what I have come up with.
[LIST]
[*]First I will need to fail/remove one of the drives in my RAID1 array. I will call this removed disk drive #2.
[*]At this point I will have one working drive in the array. I will need to unmount the raid disk (/dev/md0) and then somehow decommission the old RAID1 array.
[*]Now I will have one drive that has all the most recent data on it (the last one in the RAID1 array) which will serve as the base for the new array. I will call this drive #1.
[*]This is where I get stuck and need your help...
[/LIST]
Can I create a RAID5 array using a single drive as the base for all the data to start off with initially? Would it be better to create a faulty RAID5 array using drive #2 and drive #3 (the newly purchased one) and then copy the data from drive #1 over to that faulty RAID5 array before finally adding drive #1 to the array?

I understand the concepts behind mdadm but I get tripped up with the actual commands to type so any help would be greatly appreciated. Also, I read that it might be wise to make changes like this in single-user mode. Is that true, and if so, how do I accomplish that?

---

### Post by fjgaude on 2008-04-14
Well, nothing to do with single-user mode if you are the lone user?

The way I would do what you are wishing is let the drive #1, the one with the good data, be the missing drive as you create, for the first and only time, the raid5, three-drive array:

```
sudo mdadm --create /dev/md16 --level=5 --raid-devices=3 /dev/drive#2 /dev/drive#3 missing
```

Just like that. The word **missing** is not in quotes or anything else, just the word as typed. The #3 is the new drive, #2 is the failed old raid1 drive, and the missing is the good drive with the data, called for now drive#1.

You make the array, let it finish before doing anything else. Then create the filesystem:

```
sudo mkfs -t ext3 /dev/md16
```

After the array finishes syncing up, copy all your data from drive#2 to it.

Use **watch cat /proc/mdstat** to watch the array build, create.

Make sure you are using the right drives for the operations. And you can use any /md[nn]. I just missed 16 as it wasn't 0, used already. You might delete the mdadm.conf file in /etc/mdadm directory. That might make it easier to never have reference to the old raid1 array. The superblocks in the two drives will show them as part of that raid1 /md0 array.

After you have copied the data from the good drive to the array, you can then add it to the array:

```
sudo mdadm /dev/md16 -a /dev/sd[nn]
```

That's where watching the array synch up is important... will take maybe hours for it to do this.

Doing this is intesting too:

```
sudo mdadm -D /dev/md16
```

It'll show how far the sync has gone. You can do this many times while the synching up is going one.

Let us know how you are doing with the first creation of the raid5 array. The one with the missing drive.

---

### Post by lobo235 on 2008-04-16
With your help I was able to get the new RAID5 array up and running with the new drive, one of the drives from the RAID1 and a missing drive. I then made sure both devices were unmounted and then copied all the data from the old RAID1 drive using the command:
```
dd if=/dev/md0 of=/dev/md1 bs=8192k
```
This took about 3.5 hours because of the size of the disks (500GB). The size of the old RAID1 array was 500GB but with RAID5 the new array will be 1TB so after the dd copy command finished /dev/md1 (RAID5) was showing as only having 500GB. I then used resize2fs to resize /dev/md1 from 500GB to 1TB which took maybe 20 minutes. I was then able remove the last drive from the RAID1 array and add it to the RAID5 array. It is rebuilding now as I type this post and has about 3.25 hours to complete. Everything seems to have went well, thanks for the help!

---

### Post by fjgaude on 2008-04-16
Wonderful... but do let us know how you are doing... mdadm is a very complex program but is solid, mature. One of these days there may be a GUI for it, but who can say when?

---

