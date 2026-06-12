---
title: "Setting up a new HDD through the command line?"
date: 2013-11-17
forum: General Help
---

### Post by junk.here on 2013-11-17
I've always used GParted, so I have no idea how to set up a brand new HDD in the command line...

---

### Post by bab1 on 2013-11-17
> **junk.here said:**
> I've always used GParted, so I have no idea how to set up a brand new HDD in the command line...
The CLI version is called *parted*.  Check out ```
man parted
```

---

### Post by nerdtron on 2013-11-17
Do the following. Be careful that you select the correct disk when you do this.
This will show you the correct drive letter of you new disk.
```
sudo fdisk -l
```
Then use lsblk to see the partitions. Since this is a new disk and no filesystem, you see (I assume) just the main disk like /dev/sdc.
```
lsblk
```
Then we can commence creating a partition. Assuming just a single partition for the whole disk.
```
sudo fdisk /dev/sdc
```
Now on the fdisk utility,
Type n and press enter for new partition.
Press enter again (about 3 to 4 times) to accept the default options.
When you go back to the default prompt in fdisk, type w and press enter to write the changes to disk.
Type q and hit enter to exit.
Now run lsblk again.
```
lsblk
```
You should see you now have a /dev/sdc1 partition.
Now we need to format the partition.
```
sudo mkfs.ext4 /dev/sdc1
```
Wait for it to finish. Now all you have to do is to mount the hard drive to be ready for use.

---

