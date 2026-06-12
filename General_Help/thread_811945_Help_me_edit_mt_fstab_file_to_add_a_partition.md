---
title: "Help me edit mt fstab file to add a partition"
date: 2008-05-29
forum: General Help
---

### Post by sofasurfer on 2008-05-29
I created a new partition (sda3) on my hard drive which I will use for my backup storage. Here is my fdisk output...

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44694469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13563   108944766   83  Linux
/dev/sda2           30141       30515     3012187+   5  Extended
/dev/sda3           13564       19962    51399967+  83  Linux
/dev/sda5           30141       30515     3012156   82  Linux swap / Solaris



How do I edit my /etc/fstab file to make the new partition mountable?
Here is my current fstab file...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ea29642e-720e-4685-b90c-e03ed2e2c87f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f437e089-2bac-4180-bcbe-6c4575eabe52 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


After editing the fstab file I think that all I need to do is run the "mount" command, correct?

Is it recommended that I comment out the UUID lines and use the /dev lines instaed, which is what one post recommended?

Also, what is /etc/mtab used for?

---

### Post by fjgaude on 2008-05-29
I would use the UUIDs for drives for sure.

Once you put the new partition in your fstab file it will show on boot up, so you don't have to mount it.

First create a mountpoint in /media:

```
sudo mkdir /media/sda[n]
```

Enter the drive name in the above command.

Now find the UUID for the new partition like so:

```
sudo blkid /dev/sda[n]
```

Now do this:

```
gksudo gedit /etc/fstab
```

At the bottom of the file add this line:

```
UUID=nnnnnnnnnnn /media/sda[n] ext3 defaults 0  0
```

That should do it. Reboot and you see your new partition, ready to be used.

Let us know if you run into any troubles.

---

### Post by sofasurfer on 2008-05-29
I'll try this out after work. Gotta go now.
I just edited my previous post so you can see my fdisk output if interested.
Thanks for a quick reply.

---

### Post by wkulecz on 2008-05-29
/etc/mtab shows what is mounted automagically.  /etc/fstab lists what gets mounted on bootup by default.

I prefer /dev/partition names over UUIDs (sure to be wrong after you've replaced failed hardwre) or partition labels (filesystem dependent which can cause disaster with name collisions if you multiboot and play around with other systems. RedHat is a big offender here often creating multiple LABEL=/ partitions if you multiboot different versions).

 To your /etc/fstab add:

/dev/partition /mnt/point exte defaults,noauto 1 2

is what I like to do for backup drives/partitions (a backup partition is IMHO pointless as if the drive fails you lose all partitions, so I dedicate entire drives as a single partition to backup usage) then I make the first line of my backup script be:

/bin/mount /mnt/point

and the last line is: /bin/umount /mnt/point

This either does the right thing or fails.

There is a weakness in the Ubuntu madness to map everything as /dev/sd.  If hardware fails /dev/sdc can become /dev/sdb and wreak havoc.  UUIDs cure this problem at the cost of having to find out and type in a very user unfriendly stirng after a hardware failure to recover your partition data in the event of failure.

Last ting I want to have to do is find some arcane procedure to recover the UUID of the backup drive to be able to mount it for recovery after the system won't boot.  I think backup drives should only be mounted when you need to use them.

--wally.

---

### Post by fjgaude on 2008-05-29
As long as you only have one drive using the drive name is okay. But with two or more you can count on the names chaning... the UUID doesn't change for physical devices like drives. If the single drive fails, like in this case, you will find that new drive has a different UUID.

The /dev/sda[n] I've been showing can now be /dev/sda3, the partition that is your backup. You understand that if any aspect of your drive fails you likely will lose your backup data also on sda3.

It's good to have a separate drive for true backup.

Good luck, but do let us know how you are doing.

frank

---

### Post by sofasurfer on 2008-05-30
I succeeded by using fjgaudes method. 
I then started partimage using sudo and after I entered the "file image to create/use" ( /dev/sda3 ) and the pressed "F5" I got the message ...

"The /dev/sda1 partition is mounted. Partition image can't work on mounted partitions. Please unmount it before. You can do it with "umount /". 

So I went to terminal and entered "umount /dev/sda1" and I get the message "umount: /: device is busy". I also tried the command "umount /" and got the same message.

What am I missing.

---

### Post by fjgaude on 2008-05-30
From what I know you can't use partimage on mounted drives. You will have to use a LiveCD and work from there.

What you are trying to do is copy, sector by sector, a drive that is running, active, that has the OS on it, and that OS is needed to actually run the copy program.

I've never used partimage but it may be on the LiveCD. If not download it while on the CD from the repository, and then use it with sda1 and sda3.

There's so much to learn when you get off the path, eh?

---

### Post by sofasurfer on 2008-05-30
That makes sense. I assumed you could use it while the system to be copied was still running. Duh!

---

### Post by Victormd on 2008-05-30
Check this out...
[http://ubuntuforums.org/showthread.php?t=802699](http://ubuntuforums.org/showthread.php?t=802699)

---

### Post by sofasurfer on 2008-06-01
Ok. I learned how to use the LiveCD to run Partimage. For "file image to create/use", I entered /media/sda3. And I started to backup my SDA1 partition. But after a while of copying I got a message that "the disk is full" or something like that. Now, today I put the LiveCD back in for another attempt and I got the message that /sda1 is empty or does not exist or something like that, although my Linux system will still run.

I will try again tomorrow and get the exact errors message that appeared but in the meantime, any thoughts on what is wrong?

By the way. I created the partition (sda3) as an ext3 partition. I see in some examples that the backup partition is a "Linux" partition. Is there a differance?

---

