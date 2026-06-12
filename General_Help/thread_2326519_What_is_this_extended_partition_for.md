---
title: "What is this extended partition for?"
date: 2016-06-01
forum: General Help
---

### Post by inverged on 2016-06-01
[ATTACH=CONFIG]269397[/ATTACH]

This is from a default install setup. 
I'm trying to change my swap from 2gb to 4gb.
What is that 2GiB for and why is it there? I see that it's locked but I don't see it in etc/fstab, the mountpoint is  /dev/sda2 and it doesn't appear to have anything on it. My df looks like this:
df: &#8216;/run/user/1000/gvfs&#8217;: Transport endpoint is not connected
Filesystem      1K-blocks       Used  Available Use% Mounted on
udev              1976020         12    1976008   1% /dev
tmpfs              404736       1924     402812   1% /run
/dev/sda1       305471736  113664820  176266796  40% /
none                    4          0          4   0% /sys/fs/cgroup
none                 5120          0       5120   0% /run/lock
none              2023680      58116    1965564   3% /run/shm
none               102400         80     102320   1% /run/user
/dev/sdh1      1446791164 1318626804  128164360  92% /media/drown/Exo
/dev/sdb1      2884152536  139180416 2598442484   6% /media/drown/Primary-Storage

Would it be safe to delete it and simply add it to the swap partition?

---

### Post by steeldriver on 2016-06-01
Extended partitions are just containers for regular partitions - the installer uses them since it allows multiple (secondary) Linux partitions to be added without "using up" primary partitions (although in this case it currently contains just a single - swap - partition)

They don't use any space themselves so no, you can't delete it and "add" it to the swap partition

---

### Post by grahammechanical on 2016-06-01
> I'm trying to change my swap from 2gb to 4gb.

To do that run Gparted from a live session. It will make use of the existing swap partition. So, you will have to select the swap partition and from the Gparted menu system turn swap off. Then the key symbols will disappear from both the swap and the extended partition.

Then you can shrink sda1 by 2 GB to create unallocated space in front of the extended partition (sda2). Follow that by enlarging the extended partition to take up the unallocated space. This will seem to put the unallocated space inside the extended partition. Now, you can expand the swap partition (sda5) to take up the unallocated space. 

Regards.

---

### Post by pqwoerituytrueiwoq on 2016-06-01
To answer the title:
The default partition table is MSDOS (for legacy compatibility reasons), this has a limit of 4 partitions (though a XP install disk is limited to 3, probably a bug)
a extended partition allows you to have 4 partitions inside a partition, you can only have one extended partition
some bootloaders (eg: windows) can not operate unless they are a primary partition (aka not in a extend partition)
if you were using a GPT partition table there are no extended partitions, while there is a limit on the number of partitions, if you need more than that number you should be using probably 20 separate drives

---

