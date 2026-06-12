---
title: "RAID 5 setup?"
date: 2008-01-02
forum: General Help
---

### Post by matt91 on 2008-01-02
I am thinking about setting up a software RAID 5 array with 3 320GB hard drives.

My current setup (3 disks):
[LIST]
[*]160GB - /
[*]320GB  - /data/storage
[*]320GB - /data/storage_backup     -- this mirrors /data/storage with RSYNC daily
[/LIST]

Proposed Setup (Another 320GB):
[LIST]
[*]160GB - /
[*]3*320GB RAID 5 - /data/storage
[/LIST]

All partitions EXT3, running Ubuntu Server 7.10

So my idea is to buy another 320GB drive to put with my other 2 to give me double the storage with redundancy, this would only cost me another £50. I do not need to boot of the RAID array so that should make it easier.

Not sure how to go about doing this, i followed this guide  [http://bfish.xaedalus.net/?p=188]("http://bfish.xaedalus.net/?p=188") on a vmware and worked ok. I have also had a look at [http://ubuntuforums.org/showthread.php?t=408461]("http://ubuntuforums.org/showthread.php?t=408461").  Problem is that running RAID isn't as simple as setting it up, I would need to know what to do if  the dreaded happens and how to extend the array with more drives at a later date.

Would software RAID be reliable enough? I would keep extra backups of important stuff just in case. I would rather not buy hardware raid as this looks expensive and the cheaper ones require the cpu to  work anyway.

Any help would be appreciated:)

Matt

---

### Post by fjgaude on 2008-01-02
As best as I can tell, know, software raid under Linux is as realiable as the drives in the array, and can be as fast as the bus that drives the SATA controllers used for the drives. PCI bus is good to about 120 MB/sec; PCI-Epress X1, 250; X4 thru X16, very quick. <smile>

The way I'd go with your present setup is build the array with only two drives active, format it after built, then copy all data from the third drive (the one that is primary now), after the copy, add it into the array. Assuming all drives are about 300 MB each. That's what I have, use with a fourth as a spare.

You'd start with this on the command line:

```
sudo mdadm --create /dev/md0 --level-5 --raid-devices=3 /dev/sdb1 /dev/sdc1 missing
```

assuming your boot drive is /dev/sda. Then the added one would be /dev/sdd1.

Read, study the **man pages** for mdadm. If you have questions, there are several people here with loads of experience. You'll get answers. <smile>

---

### Post by matt91 on 2008-01-02
does it matter if the drives are on different SATA controllers ? The mobo on my server has 2 on a VIA chipset and 2 on Promise. Does the drive i buy have to be the exact model number becouse the ones i have some shops have stopped selling :(

---

### Post by fjgaude on 2008-01-02
No, the more controllers the better for speed, throughput.

No, the drives can be of any make, but the array will be built, created by mdadm using the size of the smallest one. So it's really best to have drives of the same size.

Format each the same size; I only use one partition, e.g., sdb1, sdc1, etc. Though it is possible to have many partitions of each drive, it gets confusing, at least for me, especially when failures occur. <sigh>

---

### Post by matt91 on 2008-01-02
thanks for that, will order another drive soon.

When i build the array with "missing" how do i add this to the array once i have transferred the data?

---

### Post by fjgaude on 2008-01-02
Well, just as the man page states:

```
sudo mdadm /dev/md0 --add /dev/sdd1
```

That should do it.

One more thing, use this:

```
sudo cat /proc/mdstat
```

to monitor the creation, assembly, additions, etc., to an array. **Do not** start doing things to an array before the automatic action of mdadm has finished.

---

### Post by matt91 on 2008-01-03
thanks for that, will be ordering drive soon.

Currently practicing on vmware before i go ahead and mess up ;)

---

### Post by matt91 on 2008-01-03
I have created an array on a vmware with 4 1GB virtual disks, sdb1, sdc1, sdd1 and sde1.

For a test i deleted the sdc1 disk from my vmware and powered it backup, the array has become inactive  and the devices have changed names (eg, sdd1>sdc1 and sde1>sdd1).

I have read the man pages and i am getting confused, so many options. :confused: I now understand how to create the array, add new drives etc, but just not the bit about when something goes wrong. 	](*,)

---

### Post by fjgaude on 2008-01-03
Gosh, I have no experience with virtual disks, other than the one used by vmware to hold a guest.

You could simply try to assemble the so-called crippled array:

```
sudo mdadm --assemble --scan --verbose
```

and see what happens.

AFAIK, when you pull a drive from an array it is not like it failed. If one fails on its own mdadm knows and can let you know, but it will automatically start rebuilding without the failed drive. At that time the array is still usable, works. Amazing. I've watched it happen sometime back. As long as you don't do something stupid, without thinking, software raid is solid. There are lots of things to learn but it is doable. <smile>

I started out testing as you are doing but with with four real drives, all 32G Raptors from WD, the fastest there were at the time.

And, you could use this site to get a better feel for the man pages, easy to follow, maybe:

[http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm)

Have fun.

---

### Post by matt91 on 2008-01-03
the virtual disks are just like images, slow being used as RAID 5 as they are all on one real disk. No important information on them, just wanted to simulate what could happen, think it would have been better me just corrupting the volume.

So i have tried what you have said, the result:
```
root@raidy:/# sudo mdadm --assemble --scan --verbose
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda2: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: No arrays found in config file or automatically
```

And putting /dev/md0 at the end:
```
root@raidy:/# sudo mdadm --assemble --scan --verbose /dev/md0
mdadm: /dev/md0 not identified in config file.
```

Not touched any config files, guess it means /dev/mdadm/mdadm.conf which i haven't changed.

I haven't got any real drives i could test with, running low on space, hence i will be buying the extra 320GB.:) I'm sure  nothing will go wrong when i do set the raid up, the Seagate's are pretty reliable (touch wood).

---

### Post by fjgaude on 2008-01-03
What does the mdadm.conf file look like:

```
gksudo gedit /etc/mdadm/mdadm.conf
```

The fact these drives are declared busy points to them being part of an array. So... we will get to the bottom of it all. Just don't format any of them, or do anything like that. <smile>

---

### Post by matt91 on 2008-01-04
mdadm.conf looks like this:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR removed@removed.com

# definitions of existing MD arrays

# This file was auto-generated on Thu, 03 Jan 2008 09:42:41 +0000
# by mkconf $Id: mkconf 324 2007-05-05 18:49:44Z madduck $

```

Doesn't show any mention of them in here. The question is would this simiulation happen in real life? What would i do if one drive just simply"failed"? So finding the dead drive, removing from the array and adding another.

I am using ubuntu server so no GUI here, too much to be done through the terminal on my real server that i decided it was not worth having one.

Thank you for your help so far :grin:

---

### Post by fjgaude on 2008-01-04
Well, just after the create we should have done this:

```
echo ’DEVICE /dev/hd*[0-9] /dev/sd*[0-9]’ > mdadm.conf
```

the this:

```
mdadm --detail --scan >> mdadm.conf
```

The output goes to /home folder. Then put that info into the mdadm.conf file in /etc/mdadm folder.

Seems like all this should have been done automatically when you created the array. Like I say, I don't know what it's like doing this virtually.

All we can do is study this link, easier than the man pages:

[http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm)

---

### Post by matt91 on 2008-01-04
Just ordered the drive [http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=397203]("http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=397203") which is exactly the same as the others. I can backup the contents onto what bits of storage i have around here (some of my stuff isnt essential to be backed up) until i know it is all up properly. I will continue studying them man pages. Getting it going is the easy bit, guess i can leave worrying about that until something bad does happen.

VMWares virtual drives are presented to the host as physical driver so their shouldnt be a problem there.

---

### Post by fjgaude on 2008-01-04
Remember, create the array, then set the filesystem to ext3, raid.

Good luck.

Just thought of something: you can always force an assemble by using the -f option. Try that with your virtual array.

---

### Post by matt91 on 2008-01-09
Just a quick question, if a drive does fail how would i know which drive is which? For example, which hard drive to replace.

---

### Post by fjgaude on 2008-01-09
The only way I know is to use System/Preferences/Hardware Information menu, and from there go down to Host Adapte[s]r and find your drives, and relate their Serial Number to their name, /dev/sd[nn]. Then you have to look at each drive and note its SN, and maybe put a sticky tag on it for its /dev/sd[nn].

I've asked many times over the months and this is what comes up: do it this way. Should work, although I've never had to use it. I have added and removed drives and brought new ones into an array, but one has never outright failed on me to have to remove it physically. The time will come, though. <sigh>

---

### Post by dgray_from_dc on 2008-01-09
I built an array on a 733Mhz Pentium 3 with 3 * 250GB (IDE to USB) drives using Dapper (for LTS stability and less CPU overhead) and all worked well.  I used Webmin to simplify the build-up process.

  Strange thing happened after reboot, EVMS took over the array and I couldn't get it to release it.  I uninstalled EVMS and nothing worked.  I put it back in and it immediately identified and used the array.  The problem with that was that instead of /dev/sda1  /dev/sdb1  etc.  it was /dev/evms/sda1 (or something like that) which the standard tools no longer recognized.  For some reason (I'm hoping this is unique to Dapper) I can't get RAID to run without EVMS.  I wiped the machine and started from scratch and I couldn't create an array without EVMS in the background.

  I figured, as long as I could stumble through EVMS (which I could), I'd be ok.  So, I copied all of my data (about 200GB) to the array and it worked flawlessly.  I even made a mistake of accidentally unplugging one of the drives and seeing first-hand on real hardware how the array performed in degraded mode.  (I didn't notice a single hiccup while streaming video to my PS3.  Mind you, this is IDE to USB2.0, top speed 60MBytes/sec vs the 150 or 300 MBytes/sec you get with SATA)  I was able to remove, wipe, repartition, reformat the drive, mark it as a spare, and watch for two days as the array rebuilt itself.

  A few days later, I was going to attempt to move some data off of a fourth 250G drive so that I could add it to the array.  I plugged in a 120G drive formatted ext3 and the 250G drive formatted NTFS.  When I went to mount the 120G drive it suddenly dissappeared from my system, and the RAID array went nuts.  I couldn't get into EVMS to see what was happening, I panicked and shut down the 120G drive and lost the entire array with a bad superblock error that wouldn't go way.  Fortunately, I still have my data backed up so I'm going to start over.

  Am I right in thinking that EVMS did this?  I know that having this array making use of USB adapted IDE disks isn't a good idea.  But it gives me cheap hot-swappable drives without the need to buy a huge expensive power supply.  I'm even careful only to have the array plugged in during bootup so that sda, sdb, and sdc are detected first and in the right order.  I tried to create static mount points according to this thread written for dapper [http://ubuntuforums.org/showthread.php?t=91948](http://ubuntuforums.org/showthread.php?t=91948) but with no success.

Should I move to a more current distro?

---

### Post by fjgaude on 2008-01-09
Gosh, I didn't think that Dapper even uses mdadm... I know nothing of the earlier software raid used by Linux.

I have not experience with EVMS, sorry.

Maybe others here will pipe in.

---

### Post by dgray_from_dc on 2008-01-09
Thanks anyway, I'm going to try and go with Gutsy and I'll post my results.

---

### Post by fjgaude on 2008-01-09
Very good, as we each learn every day from each other knowledge.

---

### Post by dgray_from_dc on 2008-01-26
I switched to Gutsy, but now I'm having different problems here [http://ubuntuforums.org/showthread.php?p=4210008](http://ubuntuforums.org/showthread.php?p=4210008)

---

### Post by fjgaude on 2008-01-26
Hmmm... I replied to your mentioned post.

Take a look at this, near the end of the posts, last three:

[http://ubuntuforums.org/showthread.php?p=4209417#post4209417](http://ubuntuforums.org/showthread.php?p=4209417#post4209417)

to see how robust mdadm is. <smile>

---

### Post by matt91 on 2008-01-26
My RAID 5 has now been up for  2 weeks now, haven't had to touch it yet apart from just checking the status every so often.

SMART reports drive at around 45C while about not under much use at all, might be sticking a few more fans in to cool the hard drives as their isn't  any cooling to the front of the case.

---

