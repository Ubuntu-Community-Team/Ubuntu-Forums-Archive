---
title: "Change physical partition marker in /dev"
date: 2007-10-31
forum: General Help
---

### Post by abrichr on 2007-10-31
I moved around a couple of partitions on my hard drive, and I'd like to know if it's possible to change the physical markers to reflect this.

Before the move, I had:
sda1: /
sda2: swap
sda3: windows
sda4: /home

Now, I have:
sda1: /
sda2: swap
sda4: /home
sda3: windows

That's the physical order of the disks, but as you can see, /home is still set to sda4.  Any way I can change this to sda3?

---

### Post by bingoUV on 2007-10-31
> **abrichr said:**
> I moved around a couple of partitions on my hard drive, and I'd like to know if it's possible to change the physical markers to reflect this.

Before the move, I had:
sda1: /
sda2: swap
sda3: windows
sda4: /home

Now, I have:
sda1: /
sda2: swap
sda4: /home
sda3: windows

That's the physical order of the disks, but as you can see, /home is still set to sda4.  Any way I can change this to sda3?

What method did you use to "move around" the partitions? I do not think it actually did anything. Also, what method did you use to find out the order of partitions after "moving around" the partitions.

If you want to really move around the partitions, create a gparted CD/pen drive and boot from it. Since you do not want to move your / partition, you can do edit partitions within your linux system also, but you have to do some trickery, because /home will have to be unmounted. If you cannot create a new CD/pen drive for gparted, read on

Create a temporary user (say temp)  with home directory  /root/temp
```

sudo adduser temp -d /root/temp -g admin
sudo passwd temp

```

The second command will ask to set new password for temp, and will ask you to type the passwd twice. Now, install gparted 
```

sudo apt-get install gparted

```

Now logout from your normal user account, login from temp user and start gparted
```

sudo gparted

```

Use gparted to unmount the home and windows partitions, and play with them (you can resize or move them). Backup important data before doing anything in gparted.

---

### Post by abrichr on 2007-10-31
My sincerest apologies, I definitely should have been more specific.

I used the gparted livecd to delete the windows partition, and move /home so that it was right after the swap partition.  What I'm now referring to as the windows partition is currently empty space.

To find the order of the partitions, I used "fdisk -l":

```
$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5332bd53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2553    20506941   83  Linux
/dev/sda2            2554        3039     3903795   82  Linux swap / Solaris
/dev/sda3           10689       12161    11831872+   7  HPFS/NTFS
/dev/sda4            3040       10688    61440592+  83  Linux

Partition table entries are not in disk order

```

So as you can see, sda4 is clearly located before sda3.  I'm thinking of just renaming the files in /dev:

```

$ sudo mv /dev/sda3 /dev/sda0
$ sudo mv /dev/sda4 /dev/sda3
$ sudo mv /dev/sda0 /dev/sda4

```

Of course, I would have to change my fstab to reflect the new location of /home.  But otherwise, would this break anything?

---

### Post by bingoUV on 2007-11-01
Oh, sorry. I misunderstood you. This is weird, I have always had partitions in their proper order. Anyway mv would not work as /dev will be computed again at boot time.

---

### Post by abrichr on 2007-11-01
Even after physically moving the partition with gparted?

---

