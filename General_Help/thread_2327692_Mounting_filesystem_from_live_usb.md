---
title: "Mounting filesystem from live usb"
date: 2016-06-13
forum: General Help
---

### Post by Hermann_Norpois on 2016-06-13
Hello,

I know there are some threads somehow related to my problem. But reading them did not help.

I try to mount my "original" system ubuntu 14.x via a usb live system (ubuntu 14.04). My original system failed to boot. thats why ...
I tried the usb live system.

In the terminal:

sudo mount /dev/sda1 mnt

... but this seems to be my usb device.

Actually, this is the only one I see if I use

gparted

/dev/sda1  fat32 /cdrom  3.71 GiB 3.5 GiB, 215.61 MiB boot, lba

sudo mount /dev/sdab mnt

does not work as it does not exist.

So, I would be happy to get some support accessing my "original" system. 

Thanks Hermann

---

### Post by sudodus on 2016-06-13
Welcome to the Ubuntu Forums :-)

Please post the output of the following commands and we can help you identify the partitions to mount

```
df

sudo parted -ls  # ... space minus ell ess

sudo lsblk -fm
```

-o-

You can try with the following command line to mount a partition (a small but important change from what you have tried)

```
sudo mount /dev/sda1 /mnt
```

In this case drive **a** partition **1**. Unmount it if you want to mount another partition to /mnt

```
sudo umount /mnt
```

or create subdirectories and mount several partitions at the same time, for example

```
sudo mkdir /mnt/pt1
sudo mkdir /mnt/pt2
sudo mkdir /mnt/pt3
```

and mount to these mountpoints for example

```
sudo mount /dev/sda1 /mnt/pt1
sudo mount /dev/sda5 /mnt/pt2
sudo mount /dev/sda6 /mnt/pt3
```

---

### Post by Hermann_Norpois on 2016-06-13
Following your instructions ...

ubuntu@ubuntu:~$ df
Dateisystem    1K-Blöcke Benutzt Verfügbar Verw% Eingehängt auf
udev             6069944       4   6069940    1% /dev
tmpfs            1216192    1280   1214912    1% /run
/dev/sda1        3882576 3661792    220784   95% /cdrom
/dev/loop1       1012608 1012608         0  100% /rofs
/cow             2505600   76468   2298524    4% /
none                   4       0         4    0% /sys/fs/cgroup
tmpfs            6080956    1064   6079892    1% /tmp
none                5120       4      5116    1% /run/lock
none             6080956      80   6080876    1% /run/shm
none              102400      40    102360    1% /run/user

ubuntu@ubuntu:~$ sudo parted -ls
Modell: Generic Flash Disk (scsi)
Festplatte  /dev/sda:  3985MB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos

Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags
 1      1049kB  3985MB  3984MB  primary  fat32        boot, LBA


ubuntu@ubuntu:~$ sudo lsblk -fm
NAME   FSTYPE   LABEL MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                              sda      3,7G root  disk  brw-rw----
&#9492;&#9472;sda1 vfat           /cdrom     &#9492;&#9472;sda1   3,7G root  disk  brw-rw----
loop0  ext3                      loop0    2,5G root  disk  brw-rw----
loop1  squashfs       /rofs      loop1  988,9M root  disk  brw-rw----

---

### Post by sudodus on 2016-06-14
> **Hermann_Norpois said:**
> In the terminal:

sudo mount /dev/sda1 mnt

... but this seems to be my usb device.

Actually, this is the only one I see if I use


It is the same problem for me. The only mass storage device I can see is your USB device.

Is there an internal drive?

What drive is it?

How is it connected?

Check if it is connected correctly - wiggle the connections to make sure there is good electrical connection.

Can you see it with lshw?

```
sudo bash -c 'lshw -sanitize -C disk > lshw.txt'
```

I'm afraid that something is damaged.

---

### Post by Hermann_Norpois on 2016-06-14
Yes, my harddisk is damaged. That is the solution.
Thanks
Hermann

---

### Post by sudodus on 2016-06-14
Probably yes, but before giving up you could try to connect the hard disk drive to another computer, and see if it can be seen in that computer, or connect it via an external adapter or 'box'.

---

