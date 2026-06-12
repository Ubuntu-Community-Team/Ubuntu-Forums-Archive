---
title: "Swap partition not working/enabled"
date: 2016-04-05
forum: General Help
---

### Post by charitosha on 2016-04-05
I am under impression that my swap partition is not enabled/working.
The swap partition is in a extended.
```
haris@Mini-210:~$ sudo parted -l
Model: ATA Hitachi HTS72502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  205GB  205GB   primary   ext4            boot
 2      205GB   248GB  42.6GB  primary   ext4
 3      248GB   250GB  2202MB  extended
 5      248GB   250GB  2201MB  logical   linux-swap(v1)
```

However:
At the following, shouldn't in the total column swap would be 2201MB?
```
haris@Mini-210:~$ free
             total       used       free     shared    buffers     cached
Mem:       2049404    1704056     345348          0      88428     986920
-/+ buffers/cache:     628708    1420696
Swap:            0          0          0
```

Now at the swapon command i don't know if swap device is the same as swap partition, but the outputs are the following:
```
haris@Mini-210:~$ swapon -a
swapon: cannot find the device for UUID=cebb6afd-99e2-4cfc-b3aa-4750b5543d46
haris@Mini-210:~$ swapon -s
Filename                Type        Size    Used    Priority
haris@Mini-210:~$
```

What is going on?

---

### Post by QDR06VV9 on 2016-04-05
what is the out put of this in the terminal

```
sudo blkid /dev/sda
```

---

### Post by sudodus on 2016-04-05
Please post also the output of the following commands

```
df
sudo lsblk -fm
cat /etc/fstab
```

It is important that the UUID of the swap partition matches the entry in /etc/fstab.

Also, you need sudo to turn swap on, ```
sudo swapon -a
``` but normally it will be done automatically at boot according to the entry in /etc/fstab.

See ```
man fstab
``` for details.

---

### Post by charitosha on 2016-04-05
it doesn't output anything at all...

```
haris@Mini-210:~$ sudo blkid /dev/sda
[sudo] password for haris: 
haris@Mini-210:~$ 
```

---

### Post by charitosha on 2016-04-05
```
haris@Mini-210:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1      197323044 88640236  98659336  48% /
udev             1017432       12   1017420   1% /dev
tmpfs             204944      864    204080   1% /run
none                5120        0      5120   0% /run/lock
none             1024700     1284   1023416   1% /run/shm

```

```
haris@Mini-210:~$ sudo lsblk -fm
NAME   FSTYPE LABEL MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                            sda    232.9G root  disk  brw-rw----
&#9500;&#9472;sda1 ext4         /          &#9500;&#9472;sda1 191.2G root  disk  brw-rw----
&#9500;&#9472;sda2 ext4                    &#9500;&#9472;sda2  39.7G root  disk  brw-rw----
&#9500;&#9472;sda5 swap                    &#9500;&#9472;sda5   2.1G root  disk  brw-rw----
&#9492;&#9472;sda3                         &#9492;&#9472;sda3     1K root  disk  brw-rw----

```

```
haris@Mini-210:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8c380d92-246c-444d-a057-2a2c08e3bb85 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cebb6afd-99e2-4cfc-b3aa-4750b5543d46 none            swap    sw              0       0

```

```
haris@Mini-210:~$ sudo swapon -a
[sudo] password for haris: 
swapon: cannot find the device for UUID=cebb6afd-99e2-4cfc-b3aa-4750b5543d46
```

---

### Post by QDR06VV9 on 2016-04-05
Hmmm?
One more command if you would
```
sudo blkid -c /dev/null -o list
```
Paste back the out put

---

### Post by charitosha on 2016-04-05
```
haris@Mini-210:~$ sudo blkid -c /dev/null -o list
[sudo] password for haris: 
device                  fs_type    label       mount point                 UUID
----------------------------------------------------------------------------------------------------------------
/dev/sda1               ext4                   /                           8c380d92-246c-444d-a057-2a2c08e3bb85
/dev/sda2               ext4                   (not mounted)               28963fb6-f387-4d55-ace6-d13021740522
/dev/sda5               swap                   (not mounted)               9807a0b1-984b-40e2-a1f6-bdb9851603f1
```

sda2 and sda5 not mounted????

---

### Post by sudodus on 2016-04-05
There is a mismatch between the UUID of /dev/sda5 and the entry in /etc/fstab. It is easiest to change the entry in /etc/fstab to

9807a0b1-984b-40e2-a1f6-bdb9851603f1

You can do it with the editor nano (cut and paste to avoid typing errors).

```
sudo nano /etc/fstab
```

---

### Post by QDR06VV9 on 2016-04-05
Ok Good!
```
sudo nano /etc/fstab
```
And add this to the top
```
UUID=9807a0b1-984b-40e2-a1f6-bdb9851603f1 swap swap defaults 0 0
```
Save and close.
Followed by
```
sudo swapon -s
```

Mine looks like this
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#
UUID=771bc512-302b-4684-9e0a-febdcfd7739b swap swap defaults 0 0
UUID=2fac0709-374b-4546-9202-7626acdc47eb / ext4 defaults,rw,relatime,data=orde$


```

---

### Post by charitosha on 2016-04-05
i copy pasted it now its with the new UUID
```

haris@Mini-210:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8c380d92-246c-444d-a057-2a2c08e3bb85 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9807a0b1-984b-40e2-a1f6-bdb9851603f1 none            swap    sw              0       0
```

Q: why /dev/sda2 is not in /etc/fstab?

But still not mounted...

```
haris@Mini-210:~$ sudo blkid -c /dev/null -o list
[sudo] password for haris: 
device                  fs_type    label       mount point                 UUID
----------------------------------------------------------------------------------------------------------------
/dev/sda1               ext4                   /                           8c380d92-246c-444d-a057-2a2c08e3bb85
/dev/sda2               ext4                   (not mounted)               28963fb6-f387-4d55-ace6-d13021740522
/dev/sda5               swap                   (not mounted)               9807a0b1-984b-40e2-a1f6-bdb9851603f1
```

---

### Post by QDR06VV9 on 2016-04-05
You missed this
```
sudo swapon -s
```
And you may need to reboot.

---

### Post by charitosha on 2016-04-05
swapon -s doesn't outpout anuthing:

```
haris@Mini-210:~$ sudo swapon -s
[sudo] password for haris: 
Filename                Type        Size    Used    Priority

```

I am going to reboot

---

### Post by sudodus on 2016-04-06
```
sudo swapon -s
``` shows the active swap.

```
[SIZE=3]sudo swapon -a[/SIZE]
``` turns swap on

See ```
man swapon
```

```
OPTIONS
       -a, --all
              All devices marked as ``swap'' in /etc/fstab are made available, except for  those  with
              the  ``noauto''  option.   Devices  that  are  already  being  used as swap are silently
              skipped.
...
```

But at reboot you should get swap activated automatically.

---

### Post by sudodus on 2016-04-06
If you still cannot get your swap active, please post again the output of the following commands

```
df
cat /etc/fstab
sudo blkid -c /dev/null -o list
```

---

### Post by charitosha on 2016-04-06
After the reboot the swap partition was mounted! 
I re-edited the fstab file so it would match what runrickus wrote.
So this is how you manually mount stuff??
Anyway, later on i'll try to mount the sda2 partition.
Huge thanks for the help!!!

---

### Post by charitosha on 2016-04-06
Oh and two last questions about the entries in fstab file:

Q1)in the swap partition row, under mount point, should it be 'none' or just swap? (or /dev/sda5?)

Q2)In order to mount /dev/sda2 i was thinking to write something like:
<file system>                                               <mount point>   <type>  <options>           <dump>  <pass>
UUID=28963fb6-f387-4d55-ace6-d13021740522      /          ext4 :confused:defaults:confused:errors=remount-ro:confused:       0             1

how should i write them?

---

### Post by sudodus on 2016-04-07
> **charitosha said:**
> ```
haris@Mini-210:~$ sudo blkid -c /dev/null -o list
[sudo] password for haris: 
device                  fs_type    label       mount point                 UUID
----------------------------------------------------------------------------------------------------------------
/dev/sda1               ext4                   /                           8c380d92-246c-444d-a057-2a2c08e3bb85
[COLOR="#0000FF"]/dev/sda2               ext4                   (not mounted)               28963fb6-f387-4d55-ace6-d13021740522[/COLOR]
/dev/sda5               swap                   (not mounted)               9807a0b1-984b-40e2-a1f6-bdb9851603f1
```
...
```
haris@Mini-210:~$ sudo lsblk -fm
NAME   FSTYPE LABEL MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                            sda    232.9G root  disk  brw-rw----
&#9500;&#9472;sda1 ext4         /          &#9500;&#9472;sda1 191.2G root  disk  brw-rw----
[COLOR="#0000FF"]&#9500;&#9472;sda2 ext4                    &#9500;&#9472;sda2  39.7G root  disk  brw-rw----[/COLOR]
&#9500;&#9472;sda5 swap                    &#9500;&#9472;sda5   2.1G root  disk  brw-rw----
&#9492;&#9472;sda3                         &#9492;&#9472;sda3     1K root  disk  brw-rw----

```
...

> **charitosha said:**
> Oh and two last questions about the entries in fstab file:

Q1)in the swap partition row, under mount point, should it be 'none' or just swap? (or /dev/sda5?)

The automatic method, when Ubuntu is installed is to have 'none', but it works with 'swap' too, as indicated by runrickus.
> 
Q2)In order to mount /dev/sda2 i was thinking to write something like:
<file system>                                               <mount point>   <type>  <options>           <dump>  <pass>
UUID=28963fb6-f387-4d55-ace6-d13021740522      /          ext4 :confused:defaults:confused:errors=remount-ro:confused:       0             1

how should i write them?

Mount only one partition as the root partition, symbolized with '/' !!! What is the {content of and intention with} /dev/sda2? Is it a partition to store data in general, or something special? If it is a data partition, I suggest the following:

1. Give it the label 'data' and create a mount point:

```
sudo tune2fs -L data /dev/sda2
sudo mkdir /mnt/data
```

2. I suggest that you add the following line in /etc/fstab:

```
UUID=28963fb6-f387-4d55-ace6-d13021740522  /mnt/data  ext4  defaults  0       2
```

---

### Post by charitosha on 2016-04-08
Well to be honest, recently I came across Linux From Scratch project, got really interested, downloaded the book
and want to implement/practice in that partition...
So what you think that needs to be done?

---

### Post by sudodus on 2016-04-08
Do you mean that you intend to create a Linux From Scratch system in that partition?

I think you can have the directories, where you develop it, in the Ubuntu root partition and reserve the other partition until you are ready. You need not mount it automatically at all, at least not now. I suggest that you follow the instructions, and create workspaces etc according to what is recommended for Linux From Scratch.

---

### Post by charitosha on 2016-04-08
Ok. 
Then i guess this thread is solved.
Thank you both for the help!

---

