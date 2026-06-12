---
title: "software raid 5 with mdadm - problem with initial resync"
date: 2008-06-03
forum: General Help
---

### Post by mavicus on 2008-06-03
Ubuntu 7.10, Celeron D 1.8mhz, 2gb ram, asus p5b-mx with onboard lan and graphics. apic disabled necessary for lan and usb to function properly.

I am trying to set up a 4 disk raid 5 array for data. My OS is already installed on it's own separate disk and controller. The only thing that has been installed beyond the base OS is gparted.

I have 4 samsung 750gb disks installed on sata ports, sdb through sde.

I have made partitions that are of type linux raid auto detect using fdisk. (sdb1 through sde1)

I then use the following command to create the array:

```
mdadm -Cv /dev/md0 -l5 -n4 -c128 -f /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

The array is created, but using:

```
mdadm -D /dev/md0
```

reveals that 3 drives are active, and the 4th was removed and designated as a spare.

I then read that by default, mdadm creates a raid 5 array with a spare if possible, in order to speed up the initial resync.

Not seeing that the spare ever becomes active nor that the initial resync takes place, and not able to find  instructions on making it active, I decided to zero the superblocks and try the following, to force no initial spare:

```
mdadm -Cv /dev/md0 -l5 -n4 [COLOR="Red"]-x0[/COLOR] -c128 -f /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

After this, I see all drives as active and that resync is in progress. After checking again only minutes later, I see that now sdb1 has been removed and made into a spare.

I'm not ready just yet to acknowledge that I might have a bad drive simply because 2 different ones have been kicked as spares. I know it's possible to have 2 out of 4 new drives ship broken, but I hope someone can tell me what I'm doing wrong, or what I'm omitting from the process.

Any help would be great.

---

### Post by fjgaude on 2008-06-04
I don't know what you might be doing wrong... I never use the -f function in creating a new array.

After the creation you did create a filesytem for the array?

If so, then just add the spare into your array.

I've not run into issues like you face. If the drives are relatively new it's not likely that two are bad.

---

### Post by mavicus on 2008-06-04
> After the creation you did create a filesytem for the array?

If so, then just add the spare into your array.

I guess here's part of my problem, I don't actually know how to create a filesystem on the array once it's built. I guess I have incorrectly assumed that all desired drives must be active before I create a filesystem. How do I create the filesystem there? If I remember correctly, I can't see /dev/md0 with fdisk, and I know for sure when I look at it inside gparted it reports an incorrect size of 47gb. So what program do I use to create the filesystem?

Once that's done, how do I add the spare? Is it simply with the "add" command in mdadm?

---

### Post by fjgaude on 2008-06-04
First off, gparted doesn't understand raid, period. So whatever it shows is not correct. Use mdadm -R command to observe the array.

You create a filesystem for the array with this command:

```
sudo mkfs -t ext3 /dev/md1
```

Now make a mountpoint like so:

```
sudo mkdir /home/<raid>
```

You can then mount it:

```
sudo mount /dev/md1 /home/raid
```

You can of course pick any name you like for the name <raid>.

You might wish to delete the /etc/mdadm/mdadm.conf file. Then when you re-boot your machines you simply assemble the array with this command:

```
sudo mdadm --assemble --scan
```

That does it for mdadm scans all drives and assembles according to the superblock of each drive.

Let us know if you have issues, questions.

---

### Post by mavicus on 2008-07-21
The problem has been solved. One of the drives was indeed bad. The other is fine, so I cannot explain why 2 different drives were getting kicked from the array.

Once I got the replacement and began configuring the array, I learned a valuable piece of info that was VERY hard to find online for some reason, so I will reiterate it here in case it helps someone else find the info.

[COLOR="SeaGreen"]Keep in mind that I'm referring to an old array that was never completely configured or used, and that this info doesn't apply to healthy arrays or ones that have been healthy and a drive gone bad.[/COLOR]

If a drive appears busy when you try to manipulate it or start the array, other than being defective, it could also unknowingly be in use.

You can check with
```
cat /proc/mdstat
```

When making an array where some of the drives have preexisting superblocks and some don't, I found that the ones with superblocks were somehow automatically becoming an incomplete array upon bootup. (I have not configured this anywhere yet it still happened)
The others could not be added to the existing array, and the old ones could not be removed to have their superblocks zero'd until after I manually stop the incomplete array by using
```
mdadm --stop --scan
```

Again, I'm speaking of zeroing the superblocks only because these drives are left over from an unsuccessful attempt at making an array, and I wanted to start over with each and every drive from scratch for control purposes. This doesn't apply to healthy members of an array.
After zeroing one of the superblocks, the incomplete array would automatically start immediately again! For some reason I found myself having to stop the array after every little change I make, because any use of mdadm at the command line seemed to also start the array. I've not seen this behavior documented.

---

### Post by fjgaude on 2008-07-22
"For some reason I found myself having to stop the array after every little change I make, because any use of mdadm at the command line seemed to also start the array. I've not seen this behavior documented."

What little changes are you pointing to?

I don't think I ever --stop my array, except to umount it. Then when unmounted you have access to the drives, as you will.

Sometimes I have created an array with /dev/sd[n] and not /dev/sd[nn] and have drives with superblocks in /sd[n] and not in /sd[nn], e.g. /sdc not /sdc1, and that has stumped me for a long time.

We can always zero the drive using something like:

```
dd if=zero of=/dev/sdc bs=1M count=1
```

That will put zeros in the first megabyte of the drive, which should do the job. [B]But do be careful with the drive names.
[/B]

---

