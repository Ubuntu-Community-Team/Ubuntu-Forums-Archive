---
title: "Root partition runs out out space after a while."
date: 2013-07-08
forum: General Help
---

### Post by eXidos on 2013-07-08
Hello,

I have been trying to troubleshoot this issue for a while now with no success, it has been ongoing for about 1yr.

**The PC**
Currently I have a 64GB SSD as ROOT for Ubuntu 12.04LTS but I was using a 750GB HDD for years witch also experienced this problem.

I am using this PC mainly as a NAS, it has several drives mounted into the home folder:
/home/myname/Music - 200GB (120GB Free)
/home/myname/Downloads - 750GB (600GB Free)
/home/myname/Videos/TV1 - 3TB (1TB Free)
/home/myname/Videos/TV2 - 3TB (1.3TB Free)
/home/myname/Videos/TV3 - 3TB (1.2TB Free)
/home/myname/Videos/Movies - 3TB (1.5TB Free)

**Problem Description**
When I boot up and check the ROOT partition it has about 47GB of free space but randomly it will drop to 0MB, I check the disk and there is in fact no space left. This can happen 30 seconds after boot or three weeks after boot, when it happens I can be downloading files or doing nothing at all, so I am having trouble identifying the culprit.

When this happens I can no longer download files to the mounted drives or even remote desktop onto it.

I have made sure that all torrent ".part" files from transmission-bt are saved in the /Downloads folder for temp storage not anywhere else.

I have tried Ubuntu 11.10, 12.04, 12.10, and 13.04 and this occurs on every OS, I have swapped the HDD fro a 750GB drive and it still happens as well.

**Full Specs**
1x Quad Core AMD
3x 2GB DDR3 6400
ASUS Motherboard
Nvidia PCIe Graphics with 1GB RAM
Great air cooling (max 31 degrees on any HDD)
650 Watt Thermaltake PSU
Aprox 13TB HDD's with about 5.5TB free

---

### Post by PaulEdwards on 2013-07-08
Have you found which file is filling up your HD? Is it the .xsession-errors file in your home directory? If so, you may be suffering from a known issue.
[http://matrix.z-labor.com/tmp/xsessionlogfix/](http://matrix.z-labor.com/tmp/xsessionlogfix/)

If you have the built-in Desktop Sharing enabled, see if disabling it resolves the issue.

---

### Post by sudodus on 2013-07-08
This is a hard nut. Maybe if you get some questions or ideas from me and other people, you will find the solution.

1. What files are filling the hard disk when it gets full? I think it is very important to check that to find the source of the problem.

2. When strange things happen, there might be problems with the memory. Run memtest overnight (from the grub menu).

3. Have you checked and repaired the filesystem booted from another drive (for example an install CD/DVD/USB drive) and run

```
sudo e2fsck -f /dev/sdxy
```

where x is the device letter and y is the partition number for the root partition.

---

### Post by pqwoerituytrueiwoq on 2013-07-08
can you post your [FONT=courier new]/etc/fstab[/FONT] file here
are you using trim via command line? [FONT=courier new]fstrim /[/FONT]

---

### Post by eXidos on 2013-07-08
I don't think it's an issue with the drive or filesystem as this issue has persisted on multiple HDD's, MOBO's, CPU's, and OS's.

I performed a memtest about 2 weeks ago, everything was fine.

I cannot find the files that are filling the drive. After the error occurs I check the disk usage analyser and it says the majority of space it taken up in my home folder on my mounted drives. I would expect to see a directory with about 47GB of used space but I cannot find one.

**fstab**
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0ee11da3-e41e-483c-a32e-01467e93428a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d4b3c9f1-8d56-41f5-9d14-2726b2c600cc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#HDDS
/dev/sdb1 /home/tylor/Videos/TV2 ext4 defaults 0 0
/dev/sdc1 /home/tylor/Downloads ext4 defaults 0 0
/dev/sdc2 /home/tylor/Music ext4 defaults 0 0
/dev/sdd1 /home/tylor/Videos/TV1 ext4 defaults 0 0
/dev/sde  /home/tylor/Videos/TV3 ext4 defaults 0 0
/dev/sdf1 /home/tylor/Videos/Movies ext4 defaults 0 0

```

---

### Post by sudodus on 2013-07-08
A. I think you need to check more carefully, what files are actually filling the space. Try with ***du ***booted from another drive (a live CD or USB drive).

B. *fstab*

1. I would use UUID instead of device names to identify the extra HDDs, because it decreases the risk of confusion. But it should not cause your present problem.

2.[FONT=courier new]** /dev/sde**[/FONT] is strange. Is there no partition, is the whole device mounted on TV3? Could this cause problems? Or is it only a typing error in the post?

---

### Post by eXidos on 2013-07-08
> Try with **du** booted from another drive (a live CD or USB drive)

I have tried to do trouble shooting from outside the operating system however as soon as I reboot the space is freed up again.

I noticed that the TV3 drive is set up oddly, however the problem pre-dates that drive by about 11 months and I have to transfer everything off of it before I can update the partition.

---

### Post by sudodus on 2013-07-08
OK!

1. Another track: did you try the xsessionlogfix suggested by [COLOR=#000000]*PaulEdwards*?

2. Or maybe the problem is some bug, that gets activated because you mount drives under /home. What would happen if you mount them under /mnt or /media instead, where it is common to mount data partitions?

If you remove the drives from fstab, and automount them when you want access to them, they should automount on /media/something.

But I have a multimedia partition mounted via fstab, mounted under /media, and it has worked properly for years.[/COLOR]

---

### Post by sudodus on 2013-07-08
You can still access the data partitions conveniently via symbolic links from your home folder, if you mount them under /mnt or /media.

---

### Post by eXidos on 2013-07-08
I have implemented the xsessionlogfix now, just a waiting game to see if it fixes it.

I will also be keeping an eye on my /home/name/.xsession-errors file to see if it grows to an unreasonable size.

If all else fails I will mount the drives outside the /home directory to see if that gives me any success.

---

### Post by efflandt on 2013-07-08
Could something be filling up /tmp? That is emptied every time you boot, so if something was running away and filling that up, you would not see it after a reboot. To see if that is the problem you would have to boot from another system and look at the drive (like a live system from CD/DVD or USB).

---

### Post by eXidos on 2013-07-08
Hey,

Confirmed!, it is the /home/my_name/.xsession-errors file. After I received the "Low disk space warning" the file is 51GB!!!

**DO NOT JUST DELETE YOUR ~/.xsession-errors file**
...its just a symlink and is auto loaded into your system on boot, it will even remain open as a process after you delete it and your system will continue to save errors.

---

### Post by eXidos on 2013-07-09
Sadly my solution did not fix the problem...

Any suggestions?

---

### Post by steeldriver on 2013-07-09
Let's see if we can find what message is filling up the log - this command will try to count the 10 most frequent messages in the last 10,000 lines

```
tail -n 10000 ~/.xsession-errors | sed -re '/^$/d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e 's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' | sort | uniq -c | sort -hr | head -10
```

---

### Post by eXidos on 2013-07-11
Unfortunatly I have deleted the ~/xsession-errors file so i cannot read it.

I am trying this solution : [https://marc.waeckerlin.org/computer/blog/get_rid_of_xsession-error_that_s_filling_up_the_home_directory]("https://marc.waeckerlin.org/computer/blog/get_rid_of_xsession-error_that_s_filling_up_the_home_directory")

---

