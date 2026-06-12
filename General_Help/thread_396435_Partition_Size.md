---
title: "Partition Size"
date: 2007-03-29
forum: General Help
---

### Post by doooh_head on 2007-03-29
Hey All,

I think I have a strange problem.  Awhile ago, I had Edgy installed onto a small 6Gb drive.  I purchased a larger, 60Gb drive to replace it.  Instead of reinstalling everything I followed some directions I saw going through the Ubuntu Canada mailing list whereby I install both drives into the computer, boot up using the live CD, partition and format the 60Gb drive, then by issuing a CP command (I beleive) copy all of the contents of the 6Gb drive onto the 60Gb drive including my GRUB.  This all worked flawlessly, I was able to remove the 6Gb drive and replaced it with the 60Gb drive and everything booted up correctly with all of my system/configuration intact.  The problem i'm now noticing is that my system still thinks that I only have a 6Gb partition and am getting close to filling it up.

When I use the program "Disk Usage Analyzer", it tells me that my 6Gb partition is 85% full.  When I run GParted, looking at the 60Gb device, it tells me that my /dev/hdb1 (ext3) 55.83Gb partition has used 55.13Gb.  There seems to be a discrepancy between what is actually there (a 60Gb drive with a 55.83 Gb ext3 partition within it) and the old 6Gb partition that it was copied from.

Is there some way to fix or resolve this so that the system "knows" that I have more disk space than 6Gb?  Oh and I'm not all that familiar with Linux commands, so for any responses please be concise and explicit, I'll need everything spelled out in detail, thanks.

Any help would be greatly appreciated.

Doooh

---

### Post by koma77 on 2007-03-29
I would suggest running a file system check on the disk.

sudo fsck

might do the trick. Otherwise:

man fsck

Wait a minute... Did you happen to use the 'dd' command instead of 'cp'??

---

### Post by doooh_head on 2007-03-29
> **koma77 said:**
> I would suggest running a file system check on the disk.
...
Wait a minute... Did you happen to use the 'dd' command instead of 'cp'??


Ummmm, maybe...that sounds familiar, why, does that indicate a different command may make a difference (other than your suggested "sudo fsck")?

---

### Post by koma77 on 2007-03-29
The dd command makes an exact copy (I think) of the device you point it to (given the correct parameters to dd ofcourse).

That means that the partition table and master boot record would be copied as well and I think that things like the size of the partitions are stored there.

So if you used dd, you copied the information that your partition is 6 GB to your new disk.

I don't know if sudo fsck will do the trick, but I think it is worth a shot.

(You still have the old disk as a backup, right?)

---

### Post by doooh_head on 2007-03-29
By your description of what the DD command does, that is exactly what I used.

I will try the fsck command and report back with the results...

I might have the old 6Gb hard disk intact but I was attempting to put it into another older machine on which I was going to put Xubuntu but it was giving me problems.

---

### Post by Rui Pais on 2007-03-29
Hi,
you can boot from a live cd and use gparted to ensure that the partition have the size you want. 

After that run from a terminal on the live cd:
```
sudo resize2fs /dev/XXX
```
(replace /dev/XXX with your partition scheme)

that should enlarge your filesystem to occupy the all partition.


hth

---

### Post by doooh_head on 2007-03-31
Ok, I booted up using the live CD, opened a command window.

I issued the command "sudo resize2fs /dev/hdb", I got the following message:

> john@OASISLINUX:~$ sudo resize2fs /dev/hdb
Password:
resize2fs 1.39 (29-May-2006)
resize2fs: Bad magic number in super-block while trying to open /dev/hdb
Couldn't find valid filesystem superblock.


I got a similar message when I issued the command "sudo fsck".  It suggested I try specifying a blocksize and suggested I try "sudo fsck -b 8193 /dev/hdb".  If I try this other blocksize, I will lose everything I have on the partition won't i?

---

### Post by Rui Pais on 2007-03-31
> **doooh_head said:**
> Ok, I booted up using the live CD, opened a command window.

I issued the command "sudo resize2fs /dev/hdb", I got the following message:



I got a similar message when I issued the command "sudo fsck".  It suggested I try specifying a blocksize and suggested I try "sudo fsck -b 8193 /dev/hdb".  If I try this other blocksize, I will lose everything I have on the partition won't i?

hi,
it's not /dev/hdb but /dev/hdb1 (or hdb2, etc ... )
/dev/hdb is your harddisc. you resize a partition, not a disc ;)

same thing goes for "sudo fsck -b 8193 /dev/hdb"

Those commands only apply to partitions. be careful or you will loose what ever you have on that disc.

---

### Post by doooh_head on 2007-04-04
Thanks for everyone's help, but I think I'll actually try these commands after Fiesty has been released and I've downloaded and created my install CD, then if the commands fail or screw up my configuration/partitions, then I'll just reinstall everything from scratch.  I'll likely do that anyways, but we'll see what happens after I execute these commands.

---

### Post by doooh_head on 2007-04-21
Hi all,

I just wanted to let everyone know that the suggested commands to fix my problem actually did work.

I issued the resize2fs command as well as fsck command and between them both I now have a 60 gb partition instead of the previous 6gb.

Thanks for everyone's help.

---

### Post by Rui Pais on 2007-04-22
hi,
glad it worked. :)

Thanks for the feedback. 
That way other users with same issue that may found this thread will know that at least with one user it was a solution.

Have fun.

---

