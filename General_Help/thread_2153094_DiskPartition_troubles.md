---
title: "Disk/Partition troubles"
date: 2013-06-10
forum: General Help
---

### Post by Macamba on 2013-06-10
Hi all,

It seems I'm having problems with my collection of disks and partitions. I need to perform regular (automatic?) checks of my disks when I start up. Today however I did not have wait for a disk check, but I had some warning that there where problems mounting my disks and partitions. In the end I choose to ignore these warnings, and started booting. At the moment I have no problems accessing my disks/partitions. However, I would like to work a bit on straightening out my system. So, if you could help, I would be obliged.

Some data
Currently I'm running 3.2.0-45-generic.

I have a 750 GB ATA Samsung HD753LJ disk, partitioned in 11 parts, mostly running Windows XP partitions.
I have 82 GB ATA Maxtor 6Y080L0, containing data.

My fstab:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda13 during installation
UUID=848d600a-f793-485b-816d-0d75a76c1f5c /               ext4    errors=remount -ro 0       1
# /home was on /dev/sda8 during installation
UUID=e6813a59-b8ec-4f6f-9b61-7651d77f459f /home         ext3    defaults                0        2
# swap was on /dev/sda9 during installation
#UUID=38232412-528d-41a4-82c8-8e6d65e7e46f none       swap    sw                      0        0
/dev/mapper/cryptswap1 none swap sw 0 0

# Music partition
UUID=B00C31B10C317386 /home/macamba/Music	ntfs	nls=iso8859-1,ro,umask=0  0 0

# Second hard disk
UUID=56e96ed1-4787-4081-afbc-3f4e77f6b2d2 /home/macamba/Downloads/Stuff2	 ext3	defaults        0       2

# A previously lost partition
UUID=57825d60-616a-480e-bae7-4e044ac31183 /home/macamba/Downloads/Stuff3 ext3 defaults,user,exec,dev,suid   0    2

```

I know partitions should not be mounted on the locations I have chosen, but humour me.

I did some checking using the 'Disk utility', 'Smart Data'. The big HD had the following problems:
[LIST=1]
[*]Reallocated Sector Count - Warning - 26 sectors
[*]Current Pending Sector Count - Warning - 166 Sectors
[/LIST]

The smaller HD had only the following problem:
[LIST=1]
[*]Reallocated Sector Count - Warning - 253 Sectors
[/LIST]

What should to do to get my system in spanking condition?

TIA,
Macamba

---

### Post by Rebelli0us on 2013-06-10
Put this command in Startup Applications  "gksudo touch /forcefsck" it will check & repair all ext4 partitions that you designate.

To fix NTFS partitions you have to boot a Windows OS because Linux can't do it.

---

### Post by Macamba on 2013-06-13
Thanks. I'm trying it and wondering the result. 

According to the man pages touch 'update[s]  the  access  and modification times of each FILE to the current time'. I could not find what /forcefsck did.

---

### Post by 3rdalbum on 2013-06-13
Your smaller hard disk has failed, and you should keep a close eye on your bigger one.

Back up your data from both disks and replace the smaller disk. Do it now or as quickly as possible because you have probably already lost data from the small one and maybe even from the big one.

---

### Post by gordintoronto on 2013-06-13
+1

Also check the airflow in your computer, since heat is the big evil. Install hddtemp and run it: sudo hddtemp /dev/sda

The temperature of your drives should be about the same as the temperature of your blood. (37 Celsius)

---

