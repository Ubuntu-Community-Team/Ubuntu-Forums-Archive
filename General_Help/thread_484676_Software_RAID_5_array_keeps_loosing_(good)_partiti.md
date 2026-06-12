---
title: "Software RAID 5 array keeps loosing (good) partition"
date: 2007-06-26
forum: General Help
---

### Post by peachy on 2007-06-26
Hi Folks,
In have setup a server running feisty server. The machines primary use is storage for music etc, it's running samba, slimserver, nothing too stressful.

The spec is overkill for what i need, but cheap older kit isn't available where i am.

My mobo is a "Asus P5N32-E SLI Plus" processor "Intel Pentium E2160, Dual Core, 1.8 GHz" memory "Corsair ValueSelect 2x1GB, DDR2-667, CL5" and I have 5x "Samsung HD501LJ, T166, 7200rpm, 16MB, 500GB" disks on SATA ports 1-5.

The case cannot take any further disks, so I have software raid (onboard fake raid is diabled in the bios) setup as follows:

n.b. the md devices start at 2 as i had some bother setting this up originally and can't be arsed to start over just to get md0

/dev/sda1 100mb /dev/md4 (/boot, RAID 1)
/dev/sda2 512mb /dev/md5 (swap, raid 1)
/dev/sda3 4.4gb /dev/md6 (/var, raid 1)
/dev/sda4 495gb /dev/md2 (/home using LVM, RAID 5)

/dev/sdb1 100mb /dev/md4 (/boot, RAID 1)
/dev/sdb2 512mb /dev/md5 (swap, raid 1)
/dev/sdb3 4.4gb /dev/md6 (/var, raid 1)
/dev/sdb4 495gb /dev/md2 (/home using LVM, RAID 5)

/dev/sdc1 5gb 	/dev/md3 (/ raid 1)
/dev/sdc2 495gb /dev/md2 (/home using LVM, RAID 5)

/dev/sdd1 5gb 	/dev/md3 (/ raid 1)
/dev/sdd2 495gb /dev/md2 (/home using LVM, RAID 5)

/dev/sde1 5gb 	/dev/md3 (/ raid 1 spare)
/dev/sde2 495gb /dev/md2 (/home using LVM, RAID 5)

For some reason i occasionally find one of the partitionsdrops out of /dev/md2 and gets marked as bad, evry 2 weeks or so. Sometimes I can --re-add it. Yesterday i couldn't --re-add, but after a restart the partition was recognised in the webmin interface and i could re-add the disk.

Can you please advise what i should check to determine why my partitions keep dropping out of my RAID 5 array?

---

### Post by peachy on 2007-07-01
just lost /dev/sde2 again, rebuilding now..

any advice welcome guys

---

### Post by peachy on 2007-07-02
hmm, it dropped off again.

Is software RAID 5 just unreliable? Or might it handle multiple partitions on the same disk, and in different arrays badly?

Would I be better off trying to setup this with fakeRAID? 

Any comments or theories would be welcomed.

---

### Post by peachy on 2007-07-02
This post seemed to make sense on Slashdot by "brak":
[http://ask.slashdot.org/article.pl?sid=04/10/30/184256&tid=198&tid=4&tid=106]("http://ask.slashdot.org/article.pl?sid=04/10/30/184256&tid=198&tid=4&tid=106")

> You will get responses from people with good and bad experiences, but they are all jaded by their small particular case. After seeing what can happen with dozens of machines (8 drive and 4 drive) running Linux software RAID5, here is some concrete advice.

First, ensure that all of the drives are IDE masters. Don't double up slaves and masters.

Secondly, DON'T create gigantic partitions on each oft he 250's and then RAID them together, you will get bitten, and bitten hard.

Here's the skinny...

1) Ensure that your motherboard/IDE controllers will return SMART status information. Make sure you install the smartmon tools, configure them to run weekly self tests, and ensure you have smartd running so that you get alerted to potentially failing drives ahead of time.

2) Partition your 250GB drives into 40 GB partitions. Then use RAID5 to pull together the partitions across the drives. If you want a giant volume, create a Linear RAID group of all of the RAID5 groups you created and create the filesystem on top of that.

Here's why, this is the juice.

To keep it simple, let's say there are 20 secotrs per drive. When a drive gets an uncorrectable error on a sector, it will be kicked out of the array. By partitioning the drive into 5 or 6 partitions, let's say hd(a,c,e,g,i,k,l)1 are in one of the RAID5 groups, which contain sectors 1-4 (out of the fake 20 we made up earlier)

If sector 2 goes bad on /dev/hda1, Linux software RAID5 will kick /dev/hda1 out of the array. Now, it's likely that sector 11 might be bad on /dev/hdc. If you hadn't divided up the partitions, you would lose a second disk out of the array during a rebuild.

By partitioning the disks you localize the failures a little, thus creating a more likely recovery scenario.

You wind up with a few RAID5 sets that are more resilient to multiple drive failures.

If you are using a hot spare, your rebuild time will also be less, at least for the RAID5 set that failed.

I hope this makes sense.

My advice to you is to bite the bullet and simply mirror the disks. That way, no matter how badly they fail you'll have some chance of getting some of the data off.

Can anybody confirm that there is an advantage to dividing my disks into smaller partitions?

---

### Post by peachy on 2007-07-02
[http://www.linuxquestions.org/questions/showthread.php?t=535781]("http://www.linuxquestions.org/questions/showthread.php?t=535781")
hmmm, maybe Ubuntu is not the best choice for what I am trying to do :-/

---

### Post by peachy on 2007-07-02
I'm a bit disappointed that after a week nobody can even try to point me in the right direction.

I guess my options are either buy a hardware raid controller or try a different distro.

---

### Post by peachy on 2007-08-28
Hi folks,
After basically rebuilding this machine i'm pretty convinced that having multiple partitions in different array's on each disk caused the problem. Since after having a separate "system" disk and a single raid partition on each of the disks in the array this has been very reliable.

---

### Post by fjgaude on 2007-08-28
> **peachy said:**
> Hi folks,
After basically rebuilding this machine i'm pretty convinced that having multiple partitions in different array's on each disk caused the problem. Since after having a separate "system" disk and a single raid partition on each of the disks in the array this has been very reliable.

I've found that what you finally did is likely the way to go. It's what I've done after listening to mr. steve kidders' philosophy of running a reliable raid system.

Glad you have come to this way also.

frank

---

