---
title: "Hard Drive cloning - problems (resolved)"
date: 2007-06-19
forum: General Help
---

### Post by tact on 2007-06-19
ok so its easy enough to use dd (or other tools) to clone a hdd.  Lets say you want to clone your PC internal HDD to an external (USB) HDD.

I just went thru that exercise and hit on this small problem - The external drive used to be automounted when plugged into the USB port before - but after it became the cloned copy of my internal drive it was no longer automounted when plugged in.

I did a little digging to fix it and found this seems to be  why:
I used a simple command like this will clone one drive to the other (both were 120GB drives) using dd.
dd if=/dev/sda of=/dev/sdb conv=notrunc,noerror

With a decent sized HDD it does take a long time and dd gives no progress indication so perhaps there are better tools, but none simpler.  

This kind of disk cloning makes a complete sector by sector copy of one HDD to another.  So EVERYTHING is copied, including the MBR and also the disk's UUID.  

This would apply to any sector copier (as opposed to file copier) - not just disks cloned using dd, but any tool just like it also.

So now you have two HDD's with identical UUID's.  Not a problem perhaps with distros that do not refer to UUID's in critical system files like /etc/fstab and /boot/grub/menu.lst.  Its a problem for ubuntu users though.

Its a problem for ubuntu users because (assuming the clone is an external USB drive) when you connect the USB drive expecting it to be auto-mounted and icons appear on your desktop - they do not.  If you look into it you find some error like "unable to find mount point" and thats because the mountpoint for that UUID is in use already by the internal HDD, via /etc/fstab, mounted at boot time.   

When you plug in your external drive with same UUIDs on its partitions there is a clash and cannot automount.

You can view the uuid of any partition with a command like this:
sudo vol_id -u /dev/sdb1

Or for more detailed info:
sudo vol_id /dev/sdb1

After cloning with a sector copier like dd - Check it out and see if your original and clone have identical UUID's on each partition.

You can still mount the partitions manually (create a mount point and use "mount" to mount the partitions).  Because in doing so you refer to the partition as /dev/sdxx not by its UUID. That at least gives you access to the external (cloned) drive - and maybe thats enough for you.

But the auto mounting feature does not work.  You can live with this of course.  Specially
if the cloned drive will only ever be dropped into a bottom drawer and used as a perfect snapshot of the original drive should the original ever fail.  You WILL be able to take that clone HDD out of the drawer, replace the original HDD in your PC with it, and it will boot. (albeit a possibly outdated backup)

What if you want to be able to do incremental backups, or have the convenience of automounting whenever you want to grab some config file from the cloned HDD?  What if its not just left in a drawer for some emergency some day?

If you want to fix things and have your external drives auto mount again - you can 
do so by manually changing the UUID of the cloned (external) HDD partitions.   A command like 
this works:
(assuming your internal drive is /dev/sda1,2,3,etc and your external is /dev/sdb1,2,3,etc)
mk2fs -U random /dev/sdb1

You need to repeat this for each partition on the cloned drive (i.e. sdb2, sdb3 etc) that
you will someday wish to mount (or see automounted).

This is all you need to do if you want these drives to just auto mount as external drives.

However!  What if you plan to boot from the cloned (external) HDD?  If you try to boot from this drive (either as a bootable USB drive, or by installing it inside your PC as the main drive) then you have a bit more work to do - because you changed the UUID's they no longer match what is in the grub loader and fstab files.

Thats right - copies of /boot/grub/menu.lst and /etc/fstab on the cloned (external) drive now no longer point to the right UUID's.

You will need to note down the new UUID's you created above.
Use: 
sudo vol_id -u /dev/sdb1
and repeat for sdb2,3,etc

Note the UUID and matching designation (/dev/sdxx)

Now create a mount point and mount your external drive's root partition.  e.g.
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1

Now edit your external drive's /etc/fstab file:
sudo nano /media/sdb1/etc/fstab

Replace the UUID for each partition with the correct one you noted down earlier.  No need 
change the sda to sdb tho.  Whilst this drive is /dev/sdb now as an external drive, when 
it is booted it becomes /dev/sda then.

Now you need to temporarily edit your external drive's /boot/grub/menu.lst.  This is
 only a temporary change because next time you (or some system change) calls the 
"update-grub" script it will be overwritten (with the old UUID's) and your system 
wont boot next time you reboot.

sudo nano /boot/grub/menu.lst
change just the first of the autogenerated "kernel" lines referring to UUID to 
the correct UUID.
e.g.:
kernel   /boot/vmlinuz-2.6.20-16-generic root=UUID=c65657df-xxxx-xxxx-xxxx-d1219cd878ae ro quiet splash

After this you have to boot that kernel on that drive.  whether you slot that drive into your PC
temporarily, or whether you boot from USB, either is fine.

So now you are booted from the copy HDD:
First job is to back up, then delete, /boot/grub/menu.lst - for example:
mv /boot/grub/menu.lst /boot/grub/menu.lst.bak
(does both tasks in one move)

Now use "sudo update-grub" to recreate the menu.lst - this is the only way to get the script to pick up the correct UUID's this time and forever after.  

If you skip the above steps and do NOT delete/recreate menu.lst you set yourself up for
pain later.  e.g. It you just try to use "update-grub" (without first deleting 
menu.lst) you will see that it constantly picks up the OLD UUID's from somewhere.

You have to DELETE menu.lst and only THEN update-grub.  Copy back any customisations like
splashscreen etc from the backup you made.

Job done.  You now have a complete clone of your drive using dd:
- you have changed the UUID's on the clone HDD partitions so they are again unique won't clash with the original HDD when both drives are connected to the same PC 

- you have updated essential boot files so the clone HDD can boot independantly

Congrats

---

### Post by YigalB on 2007-06-23
I have two internal (IDE) disks (40GB - bootable, 20GB secondary, also bootable - but I rareky boot from it), and also external USB disk (160GB).
I want to clone the secondary disk into the USB disk, in such a way that I could restore from USB any time to the exact position.

What is the best and simple way to do that?

Thanks

---

### Post by tact on 2007-06-23
Assuming you have other things stored on the 160GB USB drive and don't want to format it or lose data on it - you could use dd (see command line below) to make a disk image.

```
dd if=partition_to_clone of=/home/username/what_you_name_it.img
```

This is not necessarily the easiest or best way.  Others may have other ideas.

---

### Post by YigalB on 2007-06-23
So if my 20GB hard drive is /dev/hdb, and the usb disk is mounted as /dev/sda1, does it mean the command will look like:

dd if=/dev/hdb of=/dev/da1/bckjune07.img ?

Just to make sure: 
If I will replace operands (dd if=/dev/da1/bckjune07.img of=/dev/hdb ) this will retrieve 100% of the original situation, including ability to boot from this disk?

One more question: if disk size is 20GB, but I only use 10GB as for now, what will be the image size?

---

### Post by tact on 2007-06-24
> **YigalB said:**
> So if my 20GB hard drive is /dev/hdb, and the usb disk is mounted as /dev/sda1, does it mean the command will look like:

dd if=/dev/hdb of=/dev/da1/bckjune07.img ?

Just to make sure: 
If I will replace operands (dd if=/dev/da1/bckjune07.img of=/dev/hdb ) this will retrieve 100% of the original situation, including ability to boot from this disk?

One more question: if disk size is 20GB, but I only use 10GB as for now, what will be the image size?

Yes you seem to have it pretty right (except for a typo?  in two places sda1 has become da1 in what you write above.) 

Correcting the typo your example would be:

(Backup)
dd if=/dev/hdb of=/dev/sda1/bckjune07.img

(Restore)
dd if=/dev/sda1/bckjune07.img of=/dev/hdb


The size of the image will be 20GB.   Again a few warnings:
1.  get the if= and of= wrong you could potentially lose the data you want to back up.
2.  there is no progress indication so expect it to take some time and dont interrupt it.  :)
3.  be aware of file size limitations for some types of file system...  ie. if your USB drive is formatted FAT16 (which has a 4GB? maximum file size limitation) you wont be able to store your 20GB image there.

4.  the above is in no way exhaustive treatment of the subject.  I am no expert.  Do search on the "dd command" to verify everything.

5.  as mentioned earlier - there may be better solutions.  I just don't have experience to comment.

---

### Post by JerryK on 2007-06-25
I'm preparing to experiment with backing up a 100G partition.  It is mostly empty, so I am using gzip.  I have tried the following with a floppy disk with no problems.
Backup:
    gzip < /dev/fd0 > FlpTest1.gz
Restore:
    gunzip < FlpTest1.gz > /dev/fd0

The floppy had a lot of garbage in the unused blocks, so the compression was not too good.  I reformatted the floppy and the compression was MUCH better.  So, if your partition is not very full, gzip might be a good option.
Jerry K

---

### Post by YigalB on 2007-06-25
Floppy is just 1.44MB, so I assume your 100G was really empty!
So if my 20GB disk was bootable before, will it be bootable afterwards? 

I will try it from my USB disk.

---

### Post by tact on 2007-06-26
> **YigalB said:**
> Floppy is just 1.44MB, so I assume your 100G was really empty!
So if my 20GB disk was bootable before, will it be bootable afterwards? 

I will try it from my USB disk.

hehehe,,, I think he meant he did a test run - backing up a floppy disk and restoring it.   Nice and small for testing before trying to back up 100GB  :)

I dont think he meant he backed up 100GB HDD to a floppy.  :)

---

### Post by tact on 2007-06-26
I also did some testing with rsync.  It comes with ubuntu, already installed.

There is a graphical frontend for it in the ubuntu repositories called Grsync

What I did was take the 120GB backup HDD that I created using "dd" (which does entire disk clone)... then use (G)rsync to do some incremental backups...

It worked great.  Grsync only backed up files that were changed (different) between the original 120GB HDD and the clone drive.   Thus very fast to keep the clone up to date after its creation.

---

