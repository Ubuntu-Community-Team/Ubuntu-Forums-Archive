---
title: "Enhancing Hard Disc capability?"
date: 2015-05-06
forum: General Help
---

### Post by Eorlinga on 2015-05-06
Please, Is it possible to enhace the Hard Disc Ubuntu partition capability once installed along with Windows Vista?

Thanks a lot

---

### Post by oldfred on 2015-05-06
What do you mean by capability?
Size or something Else?

Post this:
sudo parted -l
df -h

---

### Post by Eorlinga on 2015-05-06
Yes, more Gigabytes for my Ubuntu partition than the ones I decided when installing it in the Hard Disk.

---

### Post by deadflowr on 2015-05-06
> **Eorlinga said:**
> Yes, more Gigabytes for my Ubuntu partition than the ones I decided when installing it in the Hard Disk.
Maybe.

Post the output from the suggested commands, which should show us how the current setup is.
And whether or not a resize is easy or hard.

[Please use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168").

---

### Post by Eorlinga on 2015-05-06
Sorry, not an Ubuntu expert. What do you mean "suggested commands"? And how to get this output?

Thanks for your concern.

---

### Post by sandyd on 2015-05-06
> **Eorlinga said:**
> Sorry, not an Ubuntu expert. What do you mean "suggested commands"? And how to get this output?

Thanks for your concern.

Please run the commands in[ post #2]("http://ubuntuforums.org/showthread.php?t=2277052&p=13280043&viewfull=1#post13280043")

The commands can be run in the terminal, which can be accessible by going to Unity Dash (top-left button), and typing in 'Terminal'

---

### Post by Eorlinga on 2015-05-06
Thanks. Here it is what I've got:

Model: ATA WDC WD1600BEVS-6 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      32,3kB  138GB  138GB   primary   ntfs            boot
 3      138GB   152GB  13,9GB  extended
 5      138GB   150GB  11,7GB  logical   ext4
 6      150GB   152GB  2137MB  logical   linux-swap(v1)
 2      152GB   160GB  7914MB  primary   ntfs


And then: 

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        11G  8,2G  1,9G  82% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            987M  4,0K  987M   1% /dev
tmpfs           200M  1,2M  199M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            997M  1,4M  996M   1% /run/shm
none            100M   56K  100M   1% /run/user
/dev/sda1       129G  114G   16G  88% /media/eorlinga/40B8D249B8D23D5A

---

### Post by oldfred on 2015-05-06
Your hard drive is 160GB, but your Windows partition, sda1 is already 88% used. Windows NTFS partitions really like 30% free and at 10% free get really slow. You at at 12% so I expect you may see Windows as being slow.

You may be able to houseclean Windows a lot, but if not you need a larger hard drive. You do have 8GB in sda2, is that a recovery partition or more data?

---

### Post by Eorlinga on 2015-05-06
I'm quite sure it is a recovery partition.

---

### Post by oldfred on 2015-05-06
Most systems allow you to make a set of DVDs for recovery partition, so you can restore it, and then you do not need it taking space on hard drive. That would gain you the 8GB.

But sometimes booting into the recovery partition automatically resets the partition table. So best to back that up to make it easy to restore unless you think you may reinstall anyway. And always before making any system changes do backups of all your data.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Be sure to save parts.txt to another device. This just is similar partition configuration info that you posted above, not any of your data.
And have a Ubuntu live installer handy in case you do have to make repairs.

---

