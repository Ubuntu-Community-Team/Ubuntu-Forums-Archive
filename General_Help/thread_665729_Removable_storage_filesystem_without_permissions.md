---
title: "Removable storage: filesystem without permissions?"
date: 2008-01-12
forum: General Help
---

### Post by xtreme- on 2008-01-12
Hi all,

I have an external hard-drive and I'm looking for a way to avoid permission-inconveniences (especially for write-permissions).
The problem is that the creator (owner) is by default the only one getting write permissions to directories and files, and that the owner is changing as the hard drive is plugged into different computers.
I believe that the ID of the creator is used, not the name - the name would however have little meaning on different computers.

The point is just that I think file permissions are of little use on removable storage; anyone having root access on any computer can just connect the storage to that computer and change permissions.
Or do you find any use in file permissions on removable storage (if it has one user)?

So I was just wondering if there is a way to get a "permission-free" filesystem or have Linux ignore the file permissions?
I know vfat could be used since it does not support file permissions, but it also makes too strict restrictions on file sizes (2 GB?) and names (case-insensitive).

Thank you for any help on this!;)

---

### Post by erpo on 2008-01-13
I agree. Permissions on removable media serve no useful purpose for most desktop users.

IIRC, FAT32 has a 4GB file size limit (this is usually the big problem) and a 2TB filesystem size limit. You could try formatting the media with NTFS, which does not have low file size limits like FAT32 does.

If you don't want to use NTFS, you could try running the command

```

sudo chmod -R 777 /mount/point

```

each time you mount the removable media. That way all directories will be readable and writable by everyone.

---

### Post by capink on 2008-01-13
> **xtreme- said:**
> 
I know vfat could be used since it does not support file permissions, but it also makes too strict restrictions on file sizes (2 GB?) and names (case-insensitive).



This size limit for files is actually 4GB which is OK for most files. Another advantage of vfat is that it can be accessed from almost all OSs without needing to install additional drivers  ( I don't know if mac can access vfat out of box ).

---

### Post by chochem on 2008-01-16
I actually searched for a way to change the ownership of my new external HD to my main user on my laptop but it seems that might be a dumb idea, then.

 It came formatted as FAT32 and assured to be working with mac and windows. I booted into windows and formatted it to NTFS (something gparted apparently is yet unable/unwilling to do) and when I booted into ubuntu, it appeared as belonging to root with 777 permissions. I don't know if this tied to NTFS but it contrasts to a small 40 Gb shared FAT32 partition on my primary HD I used to have which was mounted as belonging to root and with no write access for my user. NTFS should also be readable in all major OSes (including Mac) so it may be a solution.

---

