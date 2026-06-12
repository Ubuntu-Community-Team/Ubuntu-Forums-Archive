---
title: "did I copy the corruptness onto the new drive?"
date: 2019-08-15
forum: General Help
---

### Post by ray field on 2019-08-15
Desktop refused to boot up a week ago -- the only clue was /dev/sda5 completing fsck before the emergency command prompt popped up, so it made sense to replace the five-year old 240GB Crucial SSD drive. So, the other day I switched it out by connecting a new 2TB Samsung SSD and then 

```
cat /dev/sda > /dev/sda
```

Everything seemed to work great -- completed quickly, then once I pulled the old drive, system booted up beautifully, a little more smoothness and snap to it. 

However: Ubuntu 16.04 is still fscking /dev/sda5 at bootup, and when I boot with a USB key and check it, I get the "bad superblock" error

```
The superblock could not be read or does not describe a correct ext4
filesystem.  If the device is valid and it really contains an ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 etc.

```

none of the values succeeded.

Now, I believe (though I'm not certain) this is the error I had consistently gotten with the old drive, and which I managed to successfully ignore for a time. I gather -- and someone kindly please correct me if I'm wrong -- that I managed to copy over the corrupt geometry & hence have no choice but to copy everything off the drive, reformat, redo my /etc/fstab folder, and start anew.  

unless I am wrong -- that is, I do have another choice -- or I'm really in trouble and have no choice is all?

---

### Post by #&amp;thj^% on 2019-08-15
Only time and effort will tell
A bad superblock. To fix this:

Firstly, boot into a live CD or USB

```

sudo fdisk -l|grep Linux|grep -Ev 'swap'
```

Then, list all superblocks by using the command:
```

sudo dumpe2fs /dev/sda2 | grep superblock
```

Replace sda2 with your drive number:

You should get a similar output like this:
```
sudo dumpe2fs /dev/sda2 | grep superblock
[sudo] password for me: 
dumpe2fs 1.45.3 (14-Jul-2019)
  Primary superblock at 0, Group descriptors at 1-1
  Backup superblock at 32768, Group descriptors at 32769-32769
  Backup superblock at 98304, Group descriptors at 98305-98305

```
Now, to check and repair a Linux file system using alternate superblock #XXXX (Use your numbers here) 
Now try mounting the partition
```

sudo mount /dev/sdaX /mnt
```
"X" specifies mounted disk part number.

Now, try to browse the filesystem with the following commands
```

cd /mnt
mkdir test
ls -l
cp file /path/to/safe/location
```
If you are able to perform the above commands, you have most probably fixed your error.

Mostly for myself it's as easy as:
If you don't want to manually press 'y' every time it asks for a fix, you can also run the command with the -y option.
```

(initramfs) fsck /dev/sdaX -y
```
Good Luck.

---

### Post by ray field on 2019-08-16
Much obliged for the detailed and very helpful response, which I've archived.

Predictably, however, the fallacy of my reasoning was only compounded by my ignorance: the "bad superblock" error came when I tried to fsck /dev/sda, without specifying a partition -- now having realized I failed to understand that was essentially meaningless, and seeing fsck succeed on the actual filesystems -- well, I'm looking for another cause for the check on bootup. Just goes to show, I guess, there is such a thing as being too anal.

---

### Post by TheFu on 2019-08-16
I hope you didn't do this:
```
cat /dev/sda > /dev/sda
```
Writing sda to sda would be bad, probably.  There are really very few good reasons to use 'cat' at all.   Maybe once every 4 yrs, I use cat.  I use **tac** more often.

Hope you did something more like:```

# Boot from alternate media, then
sudo ddrescue /dev/sda  /dev/sd**b**  /tmp/log-da-dd
```

**ddrescue** will try hard to get every sector off a failing storage device, unlike other options.  Cloning different sized disks means you probably need to fix the partition table (using alternate boot media) and then fix the /etc/fstab for any new UUIDs these changes caused.  If the SSD is using GPT (it should), then the 2nd copy of the partition table will be in the wrong place after the cloning.  It needs to be relocated.  I think gdisk can do that.

But really, this migration is a perfect time to test out your backup and recovery techniques.  That is really how this migration should have been done.

---

### Post by ray field on 2019-08-17
I believe cat worked just fine -- however, per your suggestion, I booted from USB, rsync'd the contents of the new SSD drive to an internal HD, repartitioned the SSD using gdisk, rsync'd back, created a BIOS partition, and rejiggered fstab. now everything is smoother, and various anomalies that had crept in the last few months seem to be resolved. thanks for the guidance; in fact, my backup strategy is fairly redundant, with rsnapshot backing up locally every four hours, a cloud backup, and Resilio working between laptops and this desktop.

---

### Post by TheFu on 2019-08-17
Give it a few days to see if things are really good.
If you think this is solved, please use the "thread tools" button and mark it "SOLVED" to help the community.

---

### Post by ray field on 2019-08-17
always mark the thread... waiting till midweek. thanks again.

---

