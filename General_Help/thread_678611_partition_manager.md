---
title: "partition manager"
date: 2008-01-26
forum: General Help
---

### Post by xunil76 on 2008-01-26
are there any partition managers out there which will let me resize partitions on my secondary hard drive "non-destructively" (in the same fashion that Partition Magic for Windows works), without me having to logout of Ubuntu and boot into the partition manager?

i know that a partition resize should never be attempted on a mounted volume, but this will only need to be used on my secondary hard drive, and not on my boot drive, so i can unmount the partitions on that drive before attempting to resize them.

---

### Post by LaRoza on 2008-01-26
```

sudo aptitude install gparted

```

System->Administration->Partition <something>

---

### Post by xunil76 on 2008-01-26
i thought gparted had to be booted into from a boot disc, is that not the case?

---

### Post by jfinkels on 2008-01-26
As long as you're not attempting to resize a mounted partition (including the partition on which your operating system is running), it doesn't matter.

---

### Post by LaRoza on 2008-01-26
> **xunil76 said:**
> i thought gparted had to be booted into from a boot disc, is that not the case?

Nope. It is just handy on the live disk.

It works the same way installed, you just can't alter the / partition.

---

### Post by xunil76 on 2008-01-26
i see....cool

just bored @ work tonight and logged in via VNC, so there's not really any way for me to boot into another environment and keep my remote access.

but wow....it's taking a looooooong time to scan all my drives...is that normal?

largest partition is a little over 300GB

---

### Post by LaRoza on 2008-01-26
> **xunil76 said:**
> 
but wow....it's taking a looooooong time to scan all my drives...is that normal?

largest partition is a little over 300GB

Possibly...

It takes a while, but if it hangs, restart it.

---

### Post by xunil76 on 2008-01-26
ok, it scanned the drives, and i can see all my partitions, but it won't allow me to resize my NTFS partition.....and i have installed the NTFS configuration tool on my system, so it should be able to read/write to/from the NTFS partition......right?

i'm wanting to take some of the free space on the NTFS partition and add it to the larger FAT32 partition.....

[img]http://mysite.verizon.net/res0kd2j/gparted01.png[/img]

---

### Post by LaRoza on 2008-01-26
Unmount it.

(You have the same name as mine almost, /media/STORAGE)

---

### Post by PmDematagoda on 2008-01-26
Unfortunately Gparted still does not have the ability to edit NTFS partitions in anyway, i.e. move or resize them, but you can delete them.

You would have to use a partitioner that supports NTFS properly to make the changes.

---

### Post by LaRoza on 2008-01-26
> **PmDematagoda said:**
> Unfortunately Gparted still does not have the ability to edit NTFS partitions in anyway, i.e. move or resize them, but you can delete them.

You would have to use a partitioner that supports NTFS properly to make the changes.

I use GParted to resize NTFS all the time...

---

### Post by xunil76 on 2008-01-26
> **PmDematagoda said:**
> Unfortunately Gparted still does not have the ability to edit NTFS partitions in anyway, i.e. move or resize them, but you can delete them.

You would have to use a partitioner that supports NTFS properly to make the changes.

hmmm.....i could have sworn that i used a gparted boot disc to move some of that NTFS free space to create the larger FAT32 partition in the first place.....or does that only work when using the boot disk, and it doesn't work when booted into an OS?

i definitely want to be able to save the data on the NTFS drive, i just need to get it moved over to the FAT32 drive....but since the FAT32 drive's space is almost used up, i need to move some of the free space off the NTFS and onto the FAT32.

know of any good partition managers that will let me do this without having to boot from a boot disk?

---

### Post by xunil76 on 2008-01-26
> **LaRoza said:**
> I use GParted to resize NTFS all the time...

yeah, that's what i was thinking....but if i unmount the NTFS drive and resize it, does it preserve the data that's on the drive, assuming i leave enough free space to contain it all?

---

### Post by LaRoza on 2008-01-26
> **xunil76 said:**
> yeah, that's what i was thinking....but if i unmount the NTFS drive and resize it, does it preserve the data that's on the drive, assuming i leave enough free space to contain it all?

Yes. It just moves it if it is in the way.

---

### Post by PmDematagoda on 2008-01-26
> **LaRoza said:**
> I use GParted to resize NTFS all the time...

Using Gparted 0.3.3(Which is the latest GParted release) if you look in GParted>Show Features you will see that NTFS partitions cannot be resized, I tried it myself to no avail.

---

### Post by LaRoza on 2008-01-26
> **PmDematagoda said:**
> Using Gparted 0.3.3(Which is the latest GParted release) if you look in GParted>Show Features you will see that NTFS partitions cannot be resized, I tried it myself to no avail.

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

Something doesn't add up...

---

### Post by PmDematagoda on 2008-01-26
LaRoza, we both were rather wrong.

GParted has functionality with the installation of NTFSProgs but not natively.

For the OP, NTFSProgs can be installed using:-
```
sudo apt-get install ntfsprogs
```

---

### Post by LaRoza on 2008-01-26
> **PmDematagoda said:**
> LaRoza, we both were rather wrong.

GParted has functionality with the installation of NTFSProgs but not natively.


I guess that is on the LiveCD :) I haven't tried to use it installed on NTFS partitions before.

---

### Post by PmDematagoda on 2008-01-26
> **LaRoza said:**
> I guess that is on the LiveCD :) I haven't tried to use it installed on NTFS partitions before.

GParted must be having full functionality on the LiveCD whereas the normal GParted application needs those addons, at least this problem has taught us something:).

Thank you for providing the link to the GParted features page LaRoza, otherwise this would have taken more time:).

---

### Post by xunil76 on 2008-01-26
will it hurt anything to have NTFS Configuration Tool installed alongside ntfsprogs?

---

### Post by PmDematagoda on 2008-01-26
No, I am using ntfs-config alongside ntfsprogs and I do not face any problems.

---

### Post by xunil76 on 2008-01-26
well, i got ntfsprogs installed, closed/restarted gparted, and it gave me the option to resize the NTFS partition now, but it errors out when i try to reduce the size of the NTFS partition, with the error below:

[img]http://mysite.verizon.net/res0kd2j/gparted02.png[/img]

any idea why this is not working?

---

### Post by xunil76 on 2008-01-26
well, i figured out that it just didn't like the size i was specifying for the new partition, even though it was larger than what it had listed as the minimum size.....i just set it to take off a little less empty space than i tried before, and it worked fine....

---

