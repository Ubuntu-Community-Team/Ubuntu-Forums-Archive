---
title: "Unable to mount partition"
date: 2023-12-24
forum: General Help
---

### Post by asb3 on 2023-12-24
I have a hard disk with two partitions; a corrupt boot partition and a partition containing data.

When I boot from my recently installed 22.04LTS, I can mount the corrupt old boot partition, but not the data partition:
```

> lsblk
sda      8:0    0   1.9T  0 disk 
&#9500;&#9472;sda1   8:1    0     1M  0 part 
&#9500;&#9472;sda2   8:2    0   513M  0 part /boot/efi
&#9492;&#9472;sda3   8:3    0   1.9T  0 part /var/snap/firefox/common/host-hunspell

sdd      8:48   0 223.6G  0 disk 
&#9500;&#9472;sdd1   8:49   0   243M  0 part /media/asb/10a6689b-8d37-4220-9f28-db55a68318bc
&#9500;&#9472;sdd2   8:50   0     1K  0 part 
&#9492;&#9472;sdd5   8:53   0 223.3G  0 part

```

The data partition is not visible.

If I try to mount sdd5 it fails:
```

> sudo mount /dev/sdd5 /media/asb/sd0

mount: /media/asb/sd0: unknown filesystem type 'LVM2_member'.

```

If I boot from a live USB, also 22.04, both partitions of the SDD are mounted as a LVM:

```

> lsblk
sda                 8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1              8:1    0   243M  0 part 
&#9500;&#9472;sda2              8:2    0     1K  0 part 
&#9492;&#9472;sda5              8:5    0 223.3G  0 part 
  &#9500;&#9472;ubuntu-root   253:0    0 191.6G  0 lvm  /media/ubuntu/7a420995-9611-46f9-8e1f-d177783b5794
  &#9492;&#9472;ubuntu-swap_1 253:1    0  31.7G  0 lvm  

```

Both partitions are now visible.

What do I have to do to mount sdd5, or to mount the entire drive as an LVM?

---

### Post by TheFu on 2023-12-27
> **asb3 said:**
> I have a hard disk with two partitions; a corrupt boot partition and a partition containing data.

When I boot from my recently installed 22.04LTS, I can mount the corrupt old boot partition, but not the data partition:
```

> lsblk
sda      8:0    0   1.9T  0 disk 
&#9500;&#9472;sda1   8:1    0     1M  0 part 
&#9500;&#9472;sda2   8:2    0   513M  0 part /boot/efi
&#9492;&#9472;sda3   8:3    0   1.9T  0 part /var/snap/firefox/common/host-hunspell

sdd      8:48   0 223.6G  0 disk 
&#9500;&#9472;sdd1   8:49   0   243M  0 part /media/asb/10a6689b-8d37-4220-9f28-db55a68318bc
&#9500;&#9472;sdd2   8:50   0     1K  0 part 
&#9492;&#9472;sdd5   8:53   0 223.3G  0 part

```

The data partition is not visible.

If I try to mount sdd5 it fails:
```

> sudo mount /dev/sdd5 /media/asb/sd0

mount: /media/asb/sd0: unknown filesystem type 'LVM2_member'.

```

If I boot from a live USB, also 22.04, both partitions of the SDD are mounted as a LVM:

```

> lsblk
sda                 8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1              8:1    0   243M  0 part 
&#9500;&#9472;sda2              8:2    0     1K  0 part 
&#9492;&#9472;sda5              8:5    0 223.3G  0 part 
  &#9500;&#9472;ubuntu-root   253:0    0 191.6G  0 lvm  /media/ubuntu/7a420995-9611-46f9-8e1f-d177783b5794
  &#9492;&#9472;ubuntu-swap_1 253:1    0  31.7G  0 lvm  

```

Both partitions are now visible.

What do I have to do to mount sdd5, or to mount the entire drive as an LVM?

LVM isn't a file system. It is a Logical Volume Manager.  You need to learn about LVM to use it like it is supposed to be used.

You can think of LVM as a type of container inside a partition.  LVM is made up of 
PVs, VGs, and LVs.  Go look up what each of those things are.

LVs are like really, really, smart partitions and a file system is formatted into an LV. After a file system is placed onto an LV, we can mount it like we mount and use simplistic partitions with file systems.  LVM allows making changes while the file system is active, in-use. It allow being expanded, freezing blocks so backups are 100% perfect, without any risk of corruption among many other capabilities.  

Anyway .... with LVM, first we have to get the 3 different LVM objects to be activated.  That can be done a few different ways, but 
```
sudo vgchange -ay
```
is the normal way.  Run that.  If you run a good **lsblk** command - not the default like you did above - then all sorts of useful information will be shown.  Make this into an alias so you don't have to type it all the time:
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```

Now your system will have device files created for each LV - logical volume.  These devices will be in /dev, but there are symbolic links to make accessing them easier in /dev/{vg-name}/{lv-name}
For example, my swap LV is in /dev/vg01/swap01 .... so the VG name is *vg01* and the LV name is *swap01*.  
```
NAME                TYPE  FSTYPE   SIZE FSAVAIL FSUSE% LABEL          MOUNTPOINT
nvme0n1             disk         931.5G                               
<snip>
&#9492;&#9472;nvme0n1p4         part  LVM2_m 930.8G                               
  &#9500;&#9472;vg01-swap01     lvm   swap     4.1G                               [SWAP]
  &#9500;&#9472;vg01-root01     lvm   ext4      35G   25.3G    21%                /
<snip>

```
If we could mount swap (we sorta do in the fstab ... we'd use  /dev/vg01/swap01 as the device name. As you can see, I have another LV named "root01", so if it wasn't mounted, AND it already has a known file system, I'd use 
```
sudo mount -t auto /dev/vg01/root01  /
```
to mount it.    Those mount symbolic links aren't the only ones, but they are the cleanest for LVM-based devices.  See this:
```
$ df -Th .
Filesystem              Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01 ext4   35G  7.2G   26G  22% /
```

/dev/mapper/vg01-root01 is another symbolic link.  There are others using LABEL, UUIDs, PARTIDs, and a few others.  You can find them un /dev/disk/  ... for fun, I ran a command to find all the different symbolic links to the same device that /dev/vg01/root01 uses.
```
$ find /dev/disk/ -ls |grep [COLOR="#008000"]dm-7[/COLOR] | egrep -o '\/dev.*$'
/dev/disk/[COLOR="#FF0000"]by-dname[/COLOR]/vg01-root01 -> ../../[COLOR="#008000"]dm-7
[/COLOR]/dev/disk/[COLOR="#FF0000"]by-uuid[/COLOR]/6bf623da-31b5-4812-9b07-601a4c02c1ed -> ../../[COLOR="#008000"]dm-7
[/COLOR]/dev/disk/[COLOR="#FF0000"]by-id[/COLOR]/dm-uuid-LVM-YipbGpJaQ46QUsT5F5nxVEP0bgz1mpvsthZuCTdIKFblGrSL4mPvmoa9iR9rOBH7 -> ../../[COLOR="#008000"]dm-7
[/COLOR]/dev/disk/[COLOR="#FF0000"]by-id[/COLOR]/dm-name-vg01-root01 -> ../../[COLOR="#008000"]dm-7
[/COLOR]
```

If there was a LABEL on the file system, there'd be a by-label/ link too.

Just for completeness, the fstab entry for that root01 LV is this:
```
/dev/vg01/root01                          /                ext4 defaults 0 1
```

---

### Post by asb3 on 2023-12-27
I solved the problem.  The problem was a name conflict; the vg name of the drive was "ubuntu" which was already taken. I changed the name with the command
> 
>sudo vgrename j0REvK-p9li-Hdt1-91H0-WEhs-P3RU-SDc0y9 asb_old

I was still unable to mount it, but it was mounted automatically when I rebooted.

---

### Post by TheFu on 2023-12-27
Yep.  VG names cannot conflict.  That's why I rename mine to vg01, vg02, vg03, .... and on different systems, I ensure none collide. 

It is likely, someday, I'll need to connect a VG from another system to a different system. Best to use a clear naming scheme - perhaps hostname-01, -02, -03 could work too?  Depends.  I've had 1 laptop disk get migrated over and over to new systems, and the VG name, based on the original hostname from 2010, was carried forward.  It was clear to me, but confusing for anyone else.  Best to not have exceptions if someone else will ever need to manage the storage.

---

