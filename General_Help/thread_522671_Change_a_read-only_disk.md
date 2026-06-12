---
title: "Change a read-only disk?"
date: 2007-08-10
forum: General Help
---

### Post by adamd on 2007-08-10
I just got a Trojan on the vista partition of my hard drive and I still need vista to do certain things. I think I found the perpetrating file but I cannot delete it because it says it is a read only file because it is on the vista partition. Is there any way I could change it so I can delete the file? Thanks a lot.

---

### Post by bodhi.zazen on 2007-08-10
You need ntfs-3g

ntfs-config is a gui front end ... [http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

---

### Post by adamd on 2007-08-10
That only tells you what to do on a fresh install. Mine isn't a fresh install.

---

### Post by bodhi.zazen on 2007-08-10
fresh install or no, you still need ntfs-config ;)

See here for some pictures :

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by adamd on 2007-08-10
Alright well I installed it from the Synaptic Package Manager and configured it and it only came up with one partition of my hard drive and it was the wrong partition. It was the one that HP automatically puts on your hard drive for recovery. I need to access something on the standard partition of my hard drive and I can't quite figure out how to do this. That you very much for your help so far though bodhi.

---

### Post by bodhi.zazen on 2007-08-10
do you know your vista partition ? is it mounted ?

Unmount it 

```
sudo umount /dev/hdxy   #or /dev/sdxy as the case may be
```

Now re-mount it :

```
sudo mount -t ntfs-3g /dev/hdxy /mnt -o umask=000
```

You should now have read-write access to the drive at /mnt

We can configure /etc/fstab if you need

If you do not know your partition, list them with :

```
sudo fdisk -l
```

---

### Post by adamd on 2007-08-11
Ok this is what came up when I typed in "sudo fdisk -l":

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9860    79198408+   7  HPFS/NTFS
/dev/sda2           13777       14593     6562552+   7  HPFS/NTFS
/dev/sda3            9861       13609    30113842+  83  Linux
/dev/sda4           13610       13776     1341427+   5  Extended
/dev/sda5           13610       13776     1341396   82  Linux swap / Solaris

Partition table entries are not in disk order

I can't really make out what this means so I don't know what to do. And what does it mean to mount or unmount a partition? Thanks.

---

### Post by bodhi.zazen on 2007-08-11
I assume the partition you want to work with is /dev/sda1

Open a terminal

```
sudo umount /dev/sda1
sudo mount -t ntfs-3g /dev/sda1 /mnt -o umask=000
```

Now open nautilus (your filer, your home directory) and navigate to /mnt

Or you can : ```
nautilus /mnt &
```directly in your terminal.

You should see the contents of your C drive & have read-write access.

/dev/sdxx = your physical partitions
mount - prepare your partition for access and place it some where (at your mount point) in your tree or file system.

umount = remove the device (no access)

---

