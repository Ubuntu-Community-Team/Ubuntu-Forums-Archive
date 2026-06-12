---
title: "[SOLVED] How to change partition sizes on Ubuntu server (not desktop) ?"
date: 2008-05-24
forum: General Help
---

### Post by dbyrne on 2008-05-24
So, I've just noticed that when I built my system, I allocated 50Gb to the root partition, not sure what I was thinking of :oops:

Anyway, I would like to shrink this partition down to 10Gb or so, and also change the size of my /home partition to +40Gb.

Is this possible to do in server edition ? It's a headless server, so only ssh access, no X-windows so gparted isn't an option. I'm running Ubuntu 7.10, with RAID-1 on dual 300Gb Barracudas, kernel 2.6.22-14-server.

Any tips or good ideas ? Would it be easier to do if I set up LVM ?

---

### Post by pointone on 2008-05-24
```
sudo apt-get install parted
man parted
```

---

### Post by dbyrne on 2008-05-25
Cool, thanks. Didn't occur to me that if there was a graphical parted, there might be a text mode one :)

Both my current disks are identical as they are RAID-1 mirrors:

```
Disk /dev/sda: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  52.4GB  52.4GB  primary   ext3         raid
 2      52.4GB  300GB   248GB   extended
 5      52.4GB  54.6GB  2147MB  logical   linux-swap   raid
 6      54.6GB  300GB   245GB   logical   ext3         raid

```
I've read through some docs, and the way forward seems to be:

1. Boot from a rescue disk so nothing is mounted;
2. Remove the journal from the partition /home is mounted on so that it can be moved and resized later:
```
$ sudo tune2fs -O^has_journal /dev/sda6
```
3. Resize the root partition to 5.5Gb, ext3 means the start must stay the same (32.3k from the beginning of the disk):
```
$ sudo parted /dev/sda
(parted) resize 1 0.0323 5500
```
4. Move the 2147Mb swap partition to start after the root partition:
```
(parted) move 5 5500
```
5. Move the home partition to start after swap and extend to the end of the disk:
```
(parted) move 6 7647 300000
```
6. Re-build the journal on /dev/sda6:
```
$ sudo tune2fs -j /dev/sda6
```
7. Do the same for /dev/sdb, then re-boot and let the RAID arry re-build.

Anything obviously wrong with this ? Expert opinion welcome !!

---

