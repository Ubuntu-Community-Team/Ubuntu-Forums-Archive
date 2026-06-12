---
title: "Partition help"
date: 2007-12-21
forum: General Help
---

### Post by drfox on 2007-12-21
I have a 250GB disk which I've partitioned this way
/boot 4GB
/   10GB
/home  125 GB
extended 8GB
    /swap   4GB
    /opt  4GB

I have 93GB which I left unused, thinking that I could move/extend partitions in the future.
Trying to use Gutsy Live CD, I can't make a new partition out of the unpartitioned space, nor can I merge or move or enlarge my extended partition. I would like to enlarge /home.

How do I accomplish this?

Larry

---

### Post by p_quarles on 2007-12-21
My best guess is that the free space on your drive is physically discontiguous with the location of the extended partition. In other words, the free space may be at the beginning of the drive, whereas the extended partition may be at the end of the drive.

There may be better solutions, but the only one I know of is to go into Gparted, delete all of the partitions except for /home (which is, after all the important one) and find a configuration that allows everything to work properly.

---

### Post by drfox on 2007-12-21
> **p_quarles said:**
> My best guess is that the free space on your drive is physically discontiguous with the location of the extended partition. In other words, the free space may be at the beginning of the drive, whereas the extended partition may be at the end of the drive..

The extended partition is at the end of the drive, just before the unallocated part. I hate to reconfigure the whole system...I hope there's another way...

---

### Post by p_quarles on 2007-12-21
> **drfox said:**
> The extended partition is at the end of the drive, just before the unallocated part. I hate to reconfigure the whole system...I hope there's another way...
Well, if they're contiguous, it should be as simple as deleting the logical partitions, and then you should be able to resize the extended partition. The only problem there is that you've mounted /opt in a logical partition. You could try copying that partition to a newly created /opt directory in your root partition, but I honestly don't know if that will work easily.

---

### Post by drfox on 2007-12-21
> **p_quarles said:**
> Well, if they're contiguous, it should be as simple as deleting the logical partitions, and then you should be able to resize the extended partition. The only problem there is that you've mounted /opt in a logical partition. You could try copying that partition to a newly created /opt directory in your root partition, but I honestly don't know if that will work easily.

Well, fools rush in, and I did exactly that. I copied /opt to /bin, deleted swap and /opt and then the extended partition, enlarged my /home and recreated /swap and /opt. I got an fsck error when I rebooted, but I was able to get past it and I copied the /opt files back to where they belong. Now I just have to figure out how to correct the fsck tables. 

If you know how, let me know--in the meantime, I'll be searching the forum.
Thanks.

Larry

---

### Post by drfox on 2007-12-22
Well, interesting. The error I was getting is:
fsck.ext3 unable to resolve UUID= 7aecb6d2.....

I edited my /etc/fstab to comment out that UUID (it happens to be sda6, my /opt partition. 

Now booting works fine, but fstab didn't repair itself, and /opt is no longer defined (except in the commented out part. 

Is this a problem?

Larry

---

### Post by p_quarles on 2007-12-22
Honestly, I'm not really sure, but I think I know how to find out. Try getting some information from the /opt directory by typing the following commands:
```
df -h
free
acpi -t
ifconfig -a
```
If these reply with results that are within the expected range, I'd say things are working properly. If not . . . well, I dunno.

---

### Post by drfox on 2007-12-22
> **p_quarles said:**
> Honestly, I'm not really sure, but I think I know how to find out. Try getting some information from the /opt directory by typing the following commands:
```
df -h
free
acpi -t
ifconfig -a
```
If these reply with results that are within the expected range, I'd say things are working properly. If not . . . well, I dunno.

I get this:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.7G  2.7G  6.5G  30% /
varrun               1007M   92K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  136K 1007M   1% /dev
devshm               1007M     0 1007M   0% /dev/shm
lrm                  1007M   38M  970M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             3.9G   91M  3.6G   3% /boot
/dev/sda3             208G  118G   81G  60% /home
/dev/sdb1             193G   27G  157G  15% /media/sdb1
/dev/sdb2             267G  188M  253G   1% /media/sdb2
/dev/scd1             697M  697M     0 100% /media/cdrom0


/opt should be /dev/sba6
how do I get it back?
how do I tell if swap is working?

---

### Post by p_quarles on 2007-12-22
The fact that the df command works should indicate that /opt is working properly. It's no longer on its own separate partition, though . . . so, no, it should *not* be at /dev/sba6. That was its old partition.

Run the rest of the commands I gave you. The second one will show your swap partition and usage.

---

