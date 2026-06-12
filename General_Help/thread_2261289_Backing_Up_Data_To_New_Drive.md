---
title: "Backing Up Data To New Drive"
date: 2015-01-17
forum: General Help
---

### Post by bigpappajohn1984 on 2015-01-17
These are the commands I used to copy my data from a failing hard drive to a new drive and I think either 1) I omitted a step or 2) I just totally did it incorrectly.  The issue I am having is even on the "new" drive my computer just sees it as unallocated space which does me no good!

WHat should I have done differently or what can I do to recover my data?

sdb = bad hard drive
sdc = good hard drive

1) Formatted a drive to Linux format
```

sudo mkfs.ext3 /dev/sdc

```
2) Mounted drive, created a recovery directory and entered it
```

sudo mkdir mnt
sudo mount /dev/sdc mnt
cd mnt
sudo mkdir recovery
cd recovery

```
3)Used DDRescue to copy over data
```

sudo ddrescue -r 3 /dev/sdb image log

```
4) unmount the good drive
```

sudo umount /dev/sdc

```
5) Restore the image from sdc
--Now sdb is the 'raw' data
--sdc is the desination
```

sudo mkddri mnt
sudo mount /dev/sdb mnt
cd mnt
cd recovery

```
6) Copy Data
```

sudo ddrescue image /dev/sdc

```

---

### Post by Holger_Gehrke on 2015-01-17
You forgot step 0: PARTITION THE DRIVE ! mkfs.ext3 will write a file system into anything it can write to (so it can for example be used on a file to prepare a loopback mount). But the mount in step 2 should have failed with several error messages. The recovered files were probably written into the directory /mnt/recovery on whatever disk is mounted as '/'.

---

### Post by bigpappajohn1984 on 2015-01-17
UGH!!!!  Surprisingly the mkfs.ext3 did not show any errors, it acted as if it was succesful.

Where in the steps above would I partition the drive - and what would be the command to do such?

---

### Post by nerdtron on 2015-01-17
Where did you get those steps? I think if you use ddrescue to "clone" a drive, you don't have to format and mount the destination drive.

Since dd command copies everything bit by bit, you just plug you new drive and start dd-ing.
```
dd /dev/sdb /dev/sdc 
```

---

### Post by bigpappajohn1984 on 2015-01-17
I was trying to follow the guide found here, but no such luck.  Either I can't follow simple instructions or something is missing...

[http://www.geekyprojects.com/storage/how-to-recover-data-even-when-hard-drive-is-damaged/](http://www.geekyprojects.com/storage/how-to-recover-data-even-when-hard-drive-is-damaged/)

---

### Post by nerdtron on 2015-01-18
I think you can even skip step 1 and step 2, I mean, does step 2 even successfully mount?

I guess it all boils down to this:
1. You have you OS on /dev/sda
2. Next your bad drive is /dev/sdb (unmount it first). You make a image of it and save it as a file on /dev/sda. That is step 3 on your post. Also worth mentioning that the whole /dev/sdb should fit on the free space of /dev/sda.
3. Now that you have an image file of /dev/sdb, you will write it to the new drive /dev/sdc (unmount it first). Which is step 6 on your post.

Those two are the only things you need. What I don't understand is that why don't you just directly clone /dev/sdb to /dev/sdc, why bother creating a separate image file.


What part of your steps are you having trouble with?

---

### Post by efflandt on 2015-01-18
You mention a failing drive. Not sure what dd does if it gets to bad sectors it cannot read, but I know that clonezilla grinds to a halt when that happens. And depending upon what you might have done with the failing drive (like locking out badblocks) those blocks would also end up locked out (or corrupted) if cloning to new drive sector by sector.

When the Linux partition (at the end of my drive) began failing (symptom, auto remounting read-only), using secondary Ubuntu installation on my SSD I was able to fix it a few times using fsck with options to lock out badblocks. But when it got too bad, I used a free version of Acronis to clone unaffected Windows partitions to a new drive in eSATA caddy (after shrinking Win7 partition with its own Disk Managment, since I needed more room for Linux Steam). Then I installed new drive and fresh Ubuntu, then copied (cp -r) my /home over from old drive using eSATA caddy. Only a few Steam game files were corrupted from the old drive and Steam on the new drive was able to replace those by verifying game files.

While recently updating my system from 12.04 to 14.04.1 I first copied my /home to ext4 partition on USB drive, then after install copied /home from USB to 14.04.1 system. Everything worked for Firefox and Steam like nothing changed (no new verfification needed for Firefox or Steam logins).

---

### Post by gordintoronto on 2015-01-18
To create a partition on a brand new drive: sudo gparted

With some versions or variants of Ubuntu, you might need to install gparted first.

---

