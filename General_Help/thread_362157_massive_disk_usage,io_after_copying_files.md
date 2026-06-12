---
title: "massive disk usage,i/o after copying files"
date: 2007-02-15
forum: General Help
---

### Post by chrisjentys on 2007-02-15
Ive been moving my files from my windows install over to Ubuntu edgy. At the end of the file copying process (when the nautillus copy dialog box says finishing move) I sometimes get massive hdd i/o which brings my system to its knees.

I was copying 100Gb folder of mp3's at the time. CPU usage was normal (hovering around 5%-10%).

This strikes me as odd as my / partition is on a separate physical disk to the two that I was transferring files between (hope that makes sense). So why should system performance suffer so drastically? (maybe im thinking of this from a windows point of view?)

I have a total of 5 sata disks connected to my system, 3 through an onboard nvidia nforce 4 controller and 2 through a silicon image controller (no raid in either case),  which are mounted through fstab;

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b00639b1-38ab-41ff-86aa-21d5e907c74d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5c07f157-2e88-4d34-88cf-0e4a3f8689ba none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
# edited 12/02/07
/dev/sdb6	/mnt/sdb6	auto	user,rw		0 	0
/dev/sdc1	/mnt/sdc1	auto	user,rw		0 	0
/dev/sdd1	/mnt/sdd1	auto	user,rw		0 	0
/dev/sde1	/mnt/sde1	auto	user,rw		0 	0


P.S. how do i make the above apear in a code box?

Bellow "# edited 12/02/07" are the 4 partitions i mounted and am copying data between they are all ext3. The rest of fstab was created automatically during installation. Please feel free to correct/improve any of it (sdb-sde are all formatted in ext3). 

My best guess is its some kind of indexing after copying the files? I do run beagle, could this be the cause?

I just want to know what the hell my system is doing!

---

### Post by phork on 2007-02-15
Beagle will try to reindex that, and it's slowed my system to a crawl on more than one occasion.  This would also explain why this happens after the copy, and not so much during.  Try killing off beagle first, or checking out 'top' after the copy to see what is sucking up your cpu cycles and/or i/o.

---

### Post by dcstar on 2007-02-15
> **chrisjentys said:**
> Ive been moving my files from my windows install over to Ubuntu edgy. At the end of the file copying process (when the nautillus copy dialog box says finishing move) I sometimes get massive hdd i/o which brings my system to its knees.
.......
I just want to know what the hell my system is doing!

There is also the inherent disk caching that Linux has, even though a write process has finished **as far as the application is concerned**, the kernel may still have a lot of data in memory waiting for a convenient time to flush the data to the physical disk.

I see this a lot with my USB stick drive, the app has finished writing but the light still keeps flashing indicating major activity as the data is actually written to the device.

---

### Post by chrisjentys on 2007-02-16
Thanks, disabled beagle and it seems to be fine. Guessing indexing 1000's of mp3's doesnt come for free.

---

