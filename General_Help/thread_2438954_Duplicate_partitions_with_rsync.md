---
title: "Duplicate partitions with rsync?"
date: 2020-03-20
forum: General Help
---

### Post by scodrot on 2020-03-20
Hello, I'm completely new to rsync and I have never used it. I have 2 drives: /dev/sdb which has partition sdb1 and /dev/sdc which has partition sdc1.
I want to copy the whole information from sdb1 to sdc1 so there are no differences at all. Can I just copy the whole content from sd1 to sdc1 or I have to use rsync for that purpose? If so, how can I use rsync to transfer everything from one to another partition (the partitions are on different disks mounted on different mounpoints).

Edit: drives AND partitions are different sizes (newer is larger), I just need to copy the whole content of the partition to another one.

---

### Post by SeijiSensei on 2020-03-20
You'd have to mount sdb1 and sdc1 to use rsync.  If the partitions are the same size, you can use dd to make a bit-by-bit copy of one partition to the other.

```
sudo dd if=/dev/sdb1 of=/dev/sdc1
```

Make sure neither partition is mounted when you do this.

dd has a bs (blocksize) option.  The optimal value may depend on your hardware but 64k is thought to be a good compromise.

```
sudo dd bs=64K if=/dev/sdb1 of=/dev/sdc1
```

See [https://www.gnu.org/software/coreutils/dd](https://www.gnu.org/software/coreutils/dd), and especially the comments, for details.

---

### Post by TheFu on 2020-03-20
rsync is for files and directories, not devices.

To clone a full partition, use dd, ddrescue, fsarchiver, cp, partimage, or any other "image" clone tools you might prefer.

There are reasons for each method.

Regardless of the partition cloning tool, neither the source nor the target can be mounted.

---

### Post by scodrot on 2020-03-20
> **SeijiSensei said:**
> You'd have to mount sdb1 and sdc1 to use rsync.  If the partitions are the same size, you can use dd to make a bit-by-bit copy of one partition to the other.

```
sudo dd if=/dev/sdb1 of=/dev/sdc1
```

Make sure neither partition is mounted when you do this.

dd has a bs (blocksize) option.  The optimal value may depend on your hardware but 64k is thought to be a good compromise.

```
sudo dd bs=64K if=/dev/sdb1 of=/dev/sdc1
```

See [https://www.gnu.org/software/coreutils/dd](https://www.gnu.org/software/coreutils/dd), and especially the comments, for details.

Thanks, is dd a good option when everything in the partitions must be 1:1? I am copying SVN repositories and I must make sure that everything to the last bit is same before swapping the drives...

---

### Post by TheFu on 2020-03-20
i'd use ddrescue over dd.  dd stops when anything bad happens.  ddrescue continues trying to get every byte possible.

```
$ sudo ddrescue  SOURCE-DEV  TARGET-DEV  /tmp/log
```

The target-dev must be at least as large as the source-dev.

But if it where me, I’d want great backups before beginning AND I’d be using rsync with the repo unavailable to anyone else while the process happens.

---

### Post by scodrot on 2020-03-20
> **TheFu said:**
> i'd use ddrescue over dd.  dd stops when anything bad happens.  ddrescue continues trying to get every byte possible.

```
$ sudo ddrescue  SOURCE-DEV  TARGET-DEV  /tmp/log
```

The target-dev must be at least as large as the source-dev.

But if it where me, I’d want great backups before beginning AND I’d be using rsync with the repo unavailable to anyone else while the process happens.

Thanks but I'm trying to copy the content of the partition byte by byte since It's I'm replacing the disk which hold some SVN repositories and the SVN won't start with a different content. Is dd the best way to proceed in my case?

---

### Post by oldfred on 2020-03-20
If drive is gpt partitioned you need to copy entire drive, not partition.
And drives should be same size or backup partition table will not be at end of drive.

Drives using gpt have GUID in partition, primary partition table & backup partition table. If GUIDs get out of sync, it can be an issue. Issues may be fixable with gdisk. 

If you image copy a drive, then you have same UUID in both drives, so cannot reboot with both connected. You can change UUIDs in one drive or the other, but have to update grub, fstab & maybe some other settings using UUIDs.

---

### Post by scodrot on 2020-03-20
> **oldfred said:**
> If drive is gpt partitioned you need to copy entire drive, not partition.
And drives should be same size or backup partition table will not be at end of drive.

Drives using gpt have GUID in partition, primary partition table & backup partition table. If GUIDs get out of sync, it can be an issue. Issues may be fixable with gdisk. 

If you image copy a drive, then you have same UUID in both drives, so cannot reboot with both connected. You can change UUIDs in one drive or the other, but have to update grub, fstab & maybe some other settings using UUIDs.

The drive and partition I'm adding will be larger (I'm upgrading storage), partition is mbr. What are my option to copy the whole information from the old (smaller) partition to the new larger one?

---

### Post by oldfred on 2020-03-20
If MBR, it is not an issue as long as drive is not over 2TiB.

MBR does not have the built in checks that the newer gpt has. 
But then with MBR, you do not have those checks. 

I started converting new or totally reformatted drives to gpt back in 2010.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by TheFu on 2020-03-20
> But if it where me, I&#8217;d want great backups before beginning AND I&#8217;d be using rsync with the repo unavailable to anyone else while the process happens.

I&#8217;d use **rsync** as root.  

Don't be stuck on imaging. I would always choose **ddrescue** over dd when imaging is required, because the only time for imaging is when there is a hardware failure and no backs exist.  This is an ideal time to test any backup + restore process the system/disk might have.  After all, when will you ever have 2-4 copies again and a brand new disk to test onto?

---

### Post by scodrot on 2020-03-21
> **TheFu said:**
> I’d use **rsync** as root.  

Don't be stuck on imaging. I would always choose **ddrescue** over dd when imaging is required, because the only time for imaging is when there is a hardware failure and no backs exist.  This is an ideal time to test any backup + restore process the system/disk might have.  After all, when will you ever have 2-4 copies again and a brand new disk to test onto?

So rsync it is... like I said, I'm completely new, will this do the trick; rsync -vacHS --progress /oldmountpoint/ /newmountpoint/
Like I said, new drive+partition will be **larger **&#8203;than the old one, is this a problem?

---

### Post by HermanAB on 2020-03-21
Well, you say Subversion, which is a kind of database program.  There is a boring way to do it built right into the system: Prepare a new disk with a proper file system, export the database and import it into the new one [https://www.petefreitag.com/item/665.cfm](https://www.petefreitag.com/item/665.cfm)

There are of course any number of more exiting ways to do it...

---

### Post by TheFu on 2020-03-21
Assuming the mountpoints have only SVN stuff, I'd use:
```
sudo rsync -avz --progress --status /oldmountpoint/ /newmountpoint/
```

If you aren't root (i.e. sudo), then ownership isn't maintained.  Good use of the trailing / BTW.

If the mountpoints have more stuff, but you still need to get it too, that's fine.
Clearly, the /newmountpoint should only be temporary, since it will need to be moved to the /oldmountpoint for everything to work.

Also, you might want to use this opportunity to use LVM on the new disk, so moving this becomes trivial in the future using pvmove, plus LVM supports snapshots if you leave sufficient space unused to create a snapshot. Then you can take completely quiesced backups while the system keeps running.  There are many tricks to using LVM effectively. The most important is to only allocate to LVs the storage you actually need for the next few months.  So if the old HDD was 1TB and the new one is 2TB, then only allocate 1.1TB to the LV for now, but setup the PV and VG to use all 2TB.  Then you can resize up the LV in about 5 seconds at a time, while having plenty of room, logically, for other needs that can come and go.  

LVM is a little different way of thinking. Most of the time, it is completely unimportant.  For a tiny bit more complexity, we gain oh-so-much flexibility.

---

