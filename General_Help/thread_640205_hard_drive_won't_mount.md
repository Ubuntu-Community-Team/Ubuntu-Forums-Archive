---
title: "hard drive won't mount"
date: 2007-12-13
forum: General Help
---

### Post by drudogg on 2007-12-13
i have a problem with my extra hard drive. ubuntu won't find it...

there is an explanation of my setup in the first post in this thread:
[http://ubuntuforums.org/showthread.php?t=632209](http://ubuntuforums.org/showthread.php?t=632209)

anyway the second hard drive is the IDE drive and was visible when i first set up the machine... as well as the 2 windows partitions. i don't really need access to the windows partitions, but would like it. i do need access to the IDE drive. it shows up and gives me an error when i try to mount it. at first they were all on my desktop, but not now. the windows partititions don't even appear, here is my info from the fdisk -l:

drudogg@drudogg-ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 100.2 GB, 100256292864 bytes
84 heads, 51 sectors/track, 45708 cylinders
Units = cylinders of 4284 * 512 = 2193408 bytes
Disk identifier: 0x160a1609

   Device Boot      Start         End      Blocks      Id  System
/dev/hdb1   *           1       45708    97903616    7  HPFS/NTFS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a4ca4cd

   Device Boot      Start         End      Blocks          Id  System
/dev/sda1   *           1         12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       60800   385977690     f  W95 Ext'd (LBA)
/dev/sda5           12749       47791   281482866     7  HPFS/NTFS
/dev/sda6           47792       60539   102398278+  83  Linux
/dev/sda7           60540       60800   2096451        82  Linux swap / Solaris


so it sees teh drive  and the extra partitions, but won't mount them (or display the windows ones.

also not sure what is going on with sda2 and sda5 - they should both be windows vista

sda1 is xp pro

the others are obvious.

---

### Post by drudogg on 2007-12-14
is there anyone out there??

---

### Post by taurus on 2007-12-14
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hdb1
sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1
df -h
```
And if there is an error, post the complete error message here.

---

### Post by drudogg on 2007-12-14
here is what i got with that all seemed to do what it was supposed to except the next to last

drudogg@drudogg-ubuntu:~$ sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hdb1 /media/hdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hdb1 /media/hdb1 ntfs-3g defaults,force 0 0
drudogg@drudogg-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              97G  2.4G   89G   3% /
varrun                944M   88K  944M   1% /var/run
varlock               944M     0  944M   0% /var/lock
udev                  944M  108K  944M   1% /dev
devshm                944M     0  944M   0% /dev/shm
lrm                   944M   38M  907M   4% /lib/modules/2.6.22-14-generic/volatile

---

### Post by drudogg on 2007-12-14
tried the force mount and it worked for the backup drive... the windows drives are still not showing up

---

### Post by taurus on 2007-12-14
It means that you didn't shut down your windows cleanly.  So, you have two options.

1.  You can use the force option to mount it for now.

```
sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1 -o force
```

Or

2.  You can boot windows but this time, shut it down cleanly instead of using the hibernate stuff.

/dev/sda2 is an extended partition so you cannot mount an extended partition.  Therefore, forget about /dev/sda2.

```
sudo mkdir /media/sda1 /media/sda5
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
sudo mount -t ntfs-3g /dev/sda5 /media/sda5
```

---

### Post by drudogg on 2007-12-14
well like i said i don't neccessarily need tehse drives, so i will let it go if you are saying that it will fix itself when i reboot and shut down windows again.

i do not use hibernate or sleep so i do not know what my wife may have done.

---

### Post by taurus on 2007-12-14
If you boot windows again and shut it down cleanly, you shouldn't see that warning message again when you try to mount those partitions.

---

