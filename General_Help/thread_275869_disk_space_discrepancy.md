---
title: "disk space discrepancy"
date: 2006-10-12
forum: General Help
---

### Post by ludicrouSpeed on 2006-10-12
Hey All

I am having an issue with my ubuntu server, we are attempting to free some disk space. I wont go into our main issue just now which involves files much greater than the total HD space of a VM (around 150GB)being taken up on the ubuntu disk.

Ok, sidetrack aside, heres the problem at hand.

upon running a df -h i get the following output.
[HTML]
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                       30G  2.2G   26G   8% /
varrun                2.5G   84K  2.5G   1% /var/run
varlock               2.5G  4.0K  2.5G   1% /var/lock
udev                  2.5G  112K  2.5G   1% /dev
devshm                2.5G     0  2.5G   0% /dev/shm
lrm                   2.5G   22M  2.4G   1% /lib/modules/2.6.15-27-amd64-xeon/volatile
/dev/mapper/Ubuntu-rootbk
                       30G  2.3G   26G   9% /mnt/rootbk
/dev/sda1             228M   58M  158M  27% /boot
/dev/mapper/Ubuntu-storage
                      605G  575G  5.7G 100% /srv
[/HTML]

Notice the discrepancy in the used soace when compared to the available space.

It is reporting 575GB used and a total of 605GB, but as you can see the available space is only 5.7GB... so somewhere along the line, 24.3GB is being eaten.

Any ideas anyone?

Is there a way to run a search on this to find the free space and reclaim it, like a checkdisk or a defrag (apoligise for ms talk)

Cheers

Ludi

---

### Post by anaconda on 2006-10-12
When you create&format partitions in ubuntu installer ~5% of disk-space is reserved for user root.. That is reaaally old thing and it used to be good when disk-size was ~200MB or so.. So when other users got the disk full root still had some room to move around and free space without crashing the system..

Obviously with 605GB drive 5% is waaaaay too much for this purpose.
with ext2/3 filesystems the procentage can be adjusted afterwards with
tune2fs -m 0 /dev/whatever

dont know about other filesystems.. 

(FYI. debians installer asks how much you want to reserve for root user when making the partitions. It might be a good idea to reserve 1-2% for root in your "/" root ubuntu filesystem.. with data storage drives it is completely unnesessary)

And by the way df gives more accurate numbers.. df -h rounds the numbers..

---

### Post by amo-ej1 on 2006-10-12
And offcourse there is always some diskspace used by the filesystems, The journal eats up space, there's always some metadate needed around to blocks (what define your filesystem). And you don't always use entire blocks either.  So there really isn't any magic solution except a) using the royal rm -rf command b) add more disks ;)

---

### Post by ludicrouSpeed on 2006-10-12
Hey Guys well that answers my question, thanks a lot for the ultra fast response.

Ill look further into the "tune2fs -m 0 /dev/whatever" command.

Im pretty sure im using ext3

Thanks again guys

---

### Post by ludicrouSpeed on 2006-11-02
The command i used was 

sudo tune2fs -m 1 /dev/*drive

1% is the minimum size from what i could gather.

Thanks for the help guys.

Ludi

---

