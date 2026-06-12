---
title: "edgy network and upgrade help please"
date: 2006-12-02
forum: General Help
---

### Post by frup on 2006-12-02
So for the last 12 hours or so i have been trying to update my dapper box to edgy (I just got this box working since edgy was released) now the installation which i did through the apt-get dist-upgrade method has broken as i expected :P

but for me i think the reason is because pinging even my internal network doesnt work. Network is unreachable.

ifconfig brings up

etho     Link encap:Ethernet HWaddr 00:00:E8:45:11:EE
         UP BROAD CAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:82 errors:0 dropped:0 overuns:0 frames:0
         TX packets:15 errors:0 dropped:0 overuns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:11042 (10.7 KiB) TX bytes:1434 (1.4 KiB)
... i can type out more of this if needed :P

but basically no subnet gateway etc...

resolv.conf has my router in it 10.0.0.2

how can i switch from DHCP to static over terminal? (since the connection has died i can't complete the edgy upgrade and its borked)

---

### Post by Beernut on 2006-12-02
If you want to set your interface statically just do the following.

```
sudo nano /etc/network/interfaces

**iface eth0 inet dhcp          - change this line to the following lines** 

(assume 10.0.0.3)

iface eth0 inet static
         address 10.0.0.3
         netmask 255.255.255.0
         network 10.0.0.0
         broadcast 10.0.0.255
         gateway 10.0.0.2
```

Save the file then restart the network.

```
/etc/init.d/networking restart
```

---

### Post by frup on 2006-12-03
thank you very very much, worked perfectly.

Next question i have, not absolutely important though because i have the network running, on a live cd, to mount obviously sudo mount /dev/hda1 /mnt works.

i then tried to mount another drive, first to /mnt as well and then to /media (which i supposed should work)

both didnt work. each time (and I tried more than once and spent over an hour searching through the forums) it asked for a fs type... i'm guessing this is like the fstab format, unfortunately for me that didn't work either. I have 2 ext3 drives (the first being hda1 which worked fine) and one reiserfs. without having one of the other two mounted i can't transfer my data from hda1 before formatting. 

In hindsight i really should have backed up and its all my own fault but i was too excited about finally having my computer working again :P 

some help on correct syntax for mounting more than one drive over liveCD would be apreaciated. i'm worried the other two drives may have been corrupted

---

### Post by Beernut on 2006-12-03
Have you tried feeding it the file system type?

```

sudo mkdir /<directory> (you choose the name)
sudo mount -t reiserfs /dev/<name of drive, such as hda1> /<directory>
```

> In hindsight i really should have backed up and its all my own fault but i was too excited about finally having my computer working again :P 

Don't feel bad I know all about not having a backup see [here]("http://www.ubuntuforums.org/showthread.php?t=308986").  ](*,)

---

### Post by frup on 2006-12-04
```
laurent@ubuntu:~$ sudo mount -t reiserfs /dev/hdb1 /home/laurent/Reiser
mount: special device /dev/hdb1 does not exist
laurent@ubuntu:~$ sudo mount -t ext3  /dev/hdc1 /home/laurent/ext3
mount: special device /dev/hdc1 does not exist
laurent@ubuntu:~$ sudo mount -t ext3  /dev/hdc /home/laurent/ext3
mount: special device /dev/hdc does not exist

```


I believe possibly my hard drives are screwed from all the rebooting i've done in the last 6 weeks when my gfx card first began to show systems of dying and i was trying to fix it :(

---

### Post by Beernut on 2006-12-04
Are you sure about the drive names?

```
sudo fdisk -l
```

This will list the partition table.

---

### Post by frup on 2006-12-05
```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdb doesn't contain a valid partition table

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        9728    78140128+   7  HPFS/NTFS

```

hdb and hdd were my two 80gb document drives, it looks like hdd might be ok by that but it is ONLY reiserfs or ext3... no way in hell its ntfs. This is shocking if i can't get them work as they were a backup of each other! thats why i use different filesystems, so that if one fails the other probably wont because its a different system. I know its weird logic.

laurent@ubuntu:~$ sudo mount /dev/hdd1 /home/laurent/Reiser
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


dmesg | tail
[17180802.132000] JBD: no valid journal superblock found
[17180802.132000] EXT3-fs: error loading journal.

---

### Post by Beernut on 2006-12-09
> **frup said:**
> [code]
hdb and hdd were my two 80gb document drives, it looks like hdd might be ok by that but it is ONLY reiserfs or ext3... no way in hell its ntfs.

Not sure why it report the wrong file system.  Did you try and mount it as NTFS just for the heck of it?

---

