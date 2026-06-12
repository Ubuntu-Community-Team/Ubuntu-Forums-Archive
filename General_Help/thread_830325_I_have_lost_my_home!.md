---
title: "I have lost my /home!"
date: 2008-06-15
forum: General Help
---

### Post by treacle boy on 2008-06-15
Hello all,

Feeling very pleased with myself for having formated and mounted myself a new hard drive (/media/sda) :guitar:

I have now missed placed my /home directory :(
I used this command to copy it across to my new drive:

$sudo find . -depth -print | cpio --null --sparse -pvd /media/sda

which worked like a dream, I have also changed the mount point of my new drive in the fstab file to: 

/dev/sda        /home      ext3    defaults             0       2

I thought everything would be sweet after this, however now when I try and download with firefox to /home/treacle/downloads it tells me that there is not enough space on the drive!

I know that I now have 2 copies of /home ,each on a separate hard disk, but how do i get the system to recognise the new one? I would also  like to delete the old one to free up space on my old hard disk, yet I can't find it any more :confused:

Any help would be appreciated as it will increase my knowledge of the ubuntu file system :)

many thanks,

Treacle boy

---

### Post by chrisccoulson on 2008-06-15
/dev/sda isn't a valid partition. It will probably be /dev/sda1 or something. What is the output of:
```
sudo fdisk -l
```

---

### Post by treacle boy on 2008-06-16
The output I get is shown below:

```
treacle@ubuntu:~$ sudo fdisk -l
[sudo] password for treacle:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c6d2c6c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/hdb: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefc9efc9

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2382    19133383+  83  Linux
/dev/hdb2            2383        2491      875542+   5  Extended
/dev/hdb5            2383        2491      875511   82  Linux swap / Solaris
treacle@ubuntu:~$ 

```
I notice that it says /dev/sda does not have a valid partition table
but how come I managed to copy /home across to it in the fist place? Will creating a new partition table mean that I loose all the data I have transfered to the disk:confused:?

Thanks for your help,

Treacle boy

---

### Post by tgrimley on 2008-06-16
You copied to /media/sda which is just a mount point (possibly of /dev/sda1)

---

### Post by ByteJuggler on 2008-06-16
> **tgrimley said:**
> You copied to /media/sda which is just a mount point (possibly of /dev/sda1)

Yes and if it wasn't actually mounted there, then your original disk is now full due to having 2 copies of your home data, one in /home/<user> and one in /media/sda...

---

### Post by ByteJuggler on 2008-06-16
> **treacle boy said:**
> 
I notice that it says /dev/sda does not have a valid partition table
but how come I managed to copy /home across to it in the fist place? Will creating a new partition table mean that I loose all the data I have transfered to the disk:confused:?


If it doesn't in fact have a partition table, then your original assumption that you successfully created a new partition and filesystem on your new disk and mounted it was incorrect.  If so, then your copy command would've merely made another copy of the data on your existing root partition and not touched your new disk, which is probably why it's full.  It means that there's nothing on your new disk to lose when you now really create a partition on the new disk and format it!  You'll obviously have to repeat the copy operation, after really mounting the new disk somewhere and verifying that it's actually mounted...

---

### Post by chrisccoulson on 2008-06-16
If /dev/sda doesn't contain a valid partition table, try using testdisk to see if it can find a valid filesystem and recover the partition table.

As ByteJuggler has pointed out, it is likely nothing was mounted under /media/sda and that you now have 2 copies of all your files on the root filesystem. You only have one Linux partition (according to your output of fdisk), so it's likely you never had a dedicated /home partition anyway, and what you currently see in /home is all your original files. 

What does the output of these show:
```
df -h
sudo du -h --max-depth=1 /
```

---

### Post by treacle boy on 2008-06-16
Here are the results of my disk analysis:

```
treacle@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              18G   18G     0 100% /
varrun                251M   84K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M   88K  251M   1% /dev
devshm                251M     0  251M   0% /dev/shm
lrm                   251M   38M  213M  15% /lib/modules/2.6.22-14-generic/volatile
/dev/sda              147G   14G  134G  10% /home
overflow              1.0M  464K  560K  46% /tmp

treacle@ubuntu:~$ sudo du -h --max-depth=1 /
3.3M    /lib32
4.0K    /mnt
252K    /dev
4.0K    /srv
7.0M    /sbin
2.6G    /usr
332K    /root
22M     /opt
4.0K    /initrd
464K    /tmp
173M    /lib
0       /sys
18M     /boot
0       /proc
14G     /home
221M    /var
11M     /etc
20K     /media
5.7M    /bin
16K     /lost+found
17G     /
```

I notice that 14Gb of /dev/sda has been used up, I had assumed previously that this was all the /home data that I had copied accross (It was completely blank when I got it, I bought it from a software company who no longer had any use for it and had wiped it clean) but it seems that some of you more learned gents think otherwise:(

I am quite happy to have two hard disks dedicated to Ubuntu, I would like to use the smaller for all the program files and then the larger for all my data; in this case I put / and swap on the 20Gb /dev/hdb1 and /home on the 160Gb /dev/sda, is that right? Does it sound sensible? 

Cheers,

Treacle boy

---

### Post by ByteJuggler on 2008-06-16
OK... I think I see what's really happened now based on your disk analysis output. (My previous suspicions are incorrect.)

Instead of first creating a partition table and then a partition spanning the entire disk, and then formatting that, you seem to have instead simply formatted the ***entire*** /dev/sda, without creating a partition table first, as a particular filesystem, and then indeed you mounted it on /home. (It's impossible to tell if your original files are still in /home while you've mounted /dev/sda there.) 

So, although you don't have a partition table on the disk, as is apparent from partitioning tool's output, you do in fact appear to have a valid filesystem on it, and it is in fact currently mounted on /home.  So, not exactly a standard setup, but one that is possible thanks to Linux's flexibility in treating many things in your system as though it's a file, including entire disks (as in your case) or disk partitions (usually the case.)

What you do next, depends on whether you want to fix your new disk so it's used as most people would use it, e.g. with a partition table.  If so, you'll need to unmount it, verify your original /home is still there and copy the files back if they're not (and even if they are you might want to do so to ensure you get any changes you've made since you made the copy.)  Then you'll need to partition the new disk, format the new partition, mount the new partition (e.g. /dev/sda1) somewhere, and repeat your copy operation. Then verify the copy worked ok, rename the folder to "/oldhome", creae a new empty "/home", test your new auto-mount home, verify all is OK, and once that's done, delete "/oldhome".

---

