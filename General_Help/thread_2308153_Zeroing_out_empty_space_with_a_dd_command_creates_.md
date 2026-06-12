---
title: "Zeroing out empty space with a dd command creates an unreasonably big file"
date: 2015-12-31
forum: General Help
---

### Post by Roman_Mironov on 2015-12-31
Hello,

I am running Ubuntu 14.04 on a virtual machine using VirtualBox. Since my VM file got too big after months of usage, whereas the actual size of the files and folders in the VM is not that big, I assume this is due to “empty” space on the drive in my VM. 
I proceed to zero out this empty space with a dd command.

Now, this is the command I run:
dd if=/dev/zero of=/media/Rezerv02/bigemptyfile bs=4096k

The problem that I faced is that the dd process never stops and proceeds to create a bigemptyfile that is over 1 TB in size (at this point I stop the process), whereas the actual size of the drive in my VM is just 200 GB. fact, the dd process never stops, i.e., it seems to loop.

What could be causing this kind of behavior? Thank you.

---

### Post by sudodus on 2015-12-31
When you run such a dd 'wiping' command on a real mass storage device (HDD, SSD, USB pendrive), it works correctly and halts, when all the free space is used for the 'very big file'. I do that in order to prepare compressed image files.

I don't know why it does not work with VirtualBox. Maybe the system for virtual drives is limited in size, so that there will be overflow somewhere (some variable will pass its maximum value and create strange results).

-o-

In SSDs there is the trim feature, that is doing a corresponding thing on the system level, so that it is much faster.

A method that might be 'in between' in speed is to use ***zerofree*** but it works only on ext2, ext3 and ext4 file systems. See 

[man zerofree](http://manpages.ubuntu.com/manpages/trusty/man8/zerofree.8.html)

The package has the same name, so

```
sudo apt-get install zerofree
```

Maybe zerofree will serve you better than the dd command line.

---

### Post by Roman_Mironov on 2016-12-19
Thank you. Neither dd, not zerofree seem to produce any results. The actual amount of data on my drive is about 100GB, but the OS tells me it is almost 200GB.

Note: I realized that dd should be run to a smaller folder to avoid what I referred to as &#8220;looping,&#8221; but that still did not give the result I expect. The operation reports success, but the occupied space remains the same.

What could I be doing wrong? Or what are my other options?

---

### Post by QIII on 2016-12-19
Hello!

By drive, I take it you mean your virtual device?

Which OS is reporting 200GB?  The host or the guest?

---

### Post by sudodus on 2016-12-19
Please post the output of the following commands in a wide terminal window (to avoid line wrapping)

```
df
sudo lsblk -fm
sudo parted -ls
```

---

### Post by Roman_Mironov on 2016-12-19
> **QIII said:**
> Hello!

By drive, I take it you mean your virtual device?

Which OS is reporting 200GB?  The host or the guest?
Hello. Let me be more specific:
Guest: Ubuntu 14.04 64 bit. Reporting 84% usage (just 30GB free out of 200GB). However, the actual amount of data on the guest is about 100GB.
Host: Ubuntu 14.04 64 bit. Size of the VM (guest) reported is about 210GB.

> Please post the output of the following commands in a wide terminal window (to avoid line wrapping) 
Here you go — these are from the guest:
```
sudo lsblk -fm
NAME   FSTYPE LABEL MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                            sda      200G root  disk  brw-rw----
&#9492;&#9472;sda1 ext4         /          &#9492;&#9472;sda1   200G root  disk  brw-rw----
sr0                            sr0     1024M root  cdrom brw-rw----

sudo parted -ls
Model: ATA VBOX HARDDISK (scsi)
Disk /dev/sda: 215GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  215GB  215GB  primary  ext4         boot


```

---

### Post by QIII on 2016-12-19
After trying dd and zerofree, did you compact the virtual device (Only applies if it's dynamically resized)?

```
vboxmanage modifyhd /path/to/thedisk.vdi --compact
```

I'd get a snapshot before doing that.  I don't think it would cause trouble if there is something wonky with the vdi with regard to reported sizes, but you never know.

---

### Post by sudodus on 2016-12-19
> **Roman_Mironov said:**
> Hello. Let me be more specific:
Guest: Ubuntu 14.04 64 bit. Reporting 84% usage (just 30GB free out of 200GB). However, the actual amount of data on the guest is about 100GB.
Host: Ubuntu 14.04 64 bit. Size of the VM (guest) reported is about 210GB.

 
Here you go — these are from the guest:
```
sudo lsblk -fm
NAME   FSTYPE LABEL MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                            sda      200G root  disk  brw-rw----
&#9492;&#9472;sda1 ext4         /          &#9492;&#9472;sda1   200G root  disk  brw-rw----
sr0                            sr0     1024M root  cdrom brw-rw----

sudo parted -ls
Model: ATA VBOX HARDDISK (scsi)
Disk /dev/sda: 215GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  215GB  215GB  primary  ext4         boot


```

Thank you. Please add the output of ```
df
```

What I think now, is that it is a dynamic vdi file, and from the outside (seen from the host) it is smaller until it is fully used. It grows automatically but does not shrink automatically.

Filling with zeros will use it, so it will grow as seen from the outside (but should not grow seen from the inside (the guest). And as described by QIII, there is a command to make the vdi file compact after zeroizing the unused drive space in the partition in the guest. But there is something fishy with the numbers. I'm waiting for the output of ***df***.

---

### Post by kpatz on 2016-12-19
Are you running the dd command in the host or the guest?

You didn't specify a limit (count=N) in the dd command, so it will run until the drive or device is full/reaches the end.

If you're trying to shrink the VDI and it's dynamically sized, running zerofree in the guest, and then using the "vboxmanage modifyhd /path/to/thedisk.vdi --compact" in the host after shutting down the VM should do the trick.

---

### Post by Roman_Mironov on 2016-12-21
> **QIII said:**
> After trying dd and zerofree, did you compact the virtual device (Only applies if it's dynamically resized)?

```
vboxmanage modifyhd /path/to/thedisk.vdi --compact
```

I'd get a snapshot before doing that. I don't think it would cause trouble if there is something wonky with the vdi with regard to reported sizes, but you never know.
> **kpatz said:**
> Are you running the dd command in the host or the guest?

You didn't specify a limit (count=N) in the dd command, so it will run until the drive or device is full/reaches the end.

If you're trying to shrink the VDI and it's dynamically sized, running zerofree in the guest, and then using the "vboxmanage modifyhd /path/to/thedisk.vdi --compact" in the host after shutting down the VM should do the trick.
It is a dynamically sized VDI. I did not run the compact command, because I was expecting the actual amount of free space in the guest to increase after running the dd in the guest. However, it did not, so I never proceeded to compacting the guest using the compact command at the host.

After your suggestions, I ran the compact command on the host anyway, and the VDI size decreased from 210GB to 190GB — which is good, but still too much given the much smaller amount of data in the guest (about 100GB).

> **sudodus said:**
> Thank you. Please add the output of ```
df
```
Thank YOU. Here you go:
```

root@xtrf:~# df
Filesystem              1K-blocks       Used  Available Use% Mounted on
/dev/sda1               206291640  161969868   33819732  83% /
none                            4          0          4   0% /sys/fs/cgroup
udev                      2013308          4    2013304   1% /dev
tmpfs                      404828       1832     402996   1% /run
none                         5120          0       5120   0% /run/lock
none                      2024140          0    2024140   0% /run/shm
none                       102400          0     102400   0% /run/user
//192.168.0.4/Rezerv01 3845577736 2287186956 1363023564  63% /media/Rezerv01
//192.168.0.4/Rezerv02 3845577736  615035320 3035175200  17% /media/Rezerv02
root@xtrf:~#

```

---

### Post by sudodus on 2016-12-21
According to ***df*** 83% of the drive is used, 162 GB, and only 34 GB is free. So there is not very much to compress.

How do you come to the conclusion, that the amount of data is 100 GB? You could also run the command ***baobab*** and get a graphical view.

Maybe there are files, that your tool did not see, because it did not have permissions to some directories?

For example, the result of

```
find
```

and

```
sudo find
```

can be quite different.

---

