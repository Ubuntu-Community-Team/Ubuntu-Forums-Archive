---
title: "dual boot question"
date: 2014-01-06
forum: General Help
---

### Post by linuxn00b1 on 2014-01-06
greetings! 

I Just did a fresh install of win xp on it's own ntfs partition and linux mint 15 with ext4 root , /home, and swap partitions. I was wondering if I could install ext2read so I could keep my iTunes library on my /home partition? I plan on doing read only. Is this a good idea? I would just try it but I don't  want to corrupt any files. 

If this is a bad idea for iTunes, would it be ok for UpNp support? I use serviio to stream songs to a receiver and it would be nice to do no matter which OS is running.

---

### Post by cincibluer6 on 2014-01-07
If it's read only I doubt it would corrupt anything. That said, you should always have a backup anyway so at least back it up before giving it a go.

I remember briefly using a tool like that and it didn't work as intended but who knows, maybe it's been improved since then.

---

### Post by newbie-user on 2014-01-07
I'd recommend using windows to set up a separate ntfs partition for your itunes library. Then, from your home folder, symlink to that ntfs partition. That way you don't have to use any special software (ext2read) and you're sorta protected if your home directory gets hosed for whatever reason.

---

### Post by sudodus on 2014-01-07
A more common and tested solution is to have a ***separate data partition with the file system NTFS***. Such a partition is safe for data files to read and write from Windows as well as linux.

The only problem might be if you hibernate, and then start the other operating system. When the first OS wakes up, it might overwrite what you did from the other OS, so ***it is a bad idea to hibernate, when you have dual boot***.

---

### Post by Bucky Ball on 2014-01-07
> **newbie-user said:**
> I'd recommend using windows to set up a separate ntfs partition for your itunes library. Then, from your home folder, symlink to that ntfs partition.

^^^
This.

Also has the advantage, as mentioned, that either OS gets hosed your personal data is on a separate partition. You can simply reinstall the OS (but you will have sensible backups nonetheless, naturally ... ;))

The theory is:

```
ln -s 'location to link to' 'name of symlink'
```

... so your symlink, if your iTunes directory was on the NTFS partition you created and at the path /mnt/NTFS_partition/iTunes, would be something like:

```
ln -s /mnt/NTFS_partition/iTunes /home/<username>/Music/iTunes
```

You can use Win or Ubuntu (Gparted) to set up an NTFS partition. ;)

---

### Post by linuxn00b1 on 2014-01-07
Thank you for all the info! Sounds good but...


I read having too many partitions is no good?

I currently have xp partition, root partition, home folder partition and swap partition. 
Shrinking the home folder and symlinking sounds good but would 5 partitions on a 250gig drive be a problem?  Are there any limits with symink (slow read write times, bad for video)? Can I run a minimal home folder size and keep all my media accesed on the NTFS partition?

---

### Post by Bucky Ball on 2014-01-07
Unless you have an EFI install the limitation is four partitions per drive. These can be any combination of primary and extended partitions. You can put as many logical drives inside and extended partition as you like (or your hardware will handle). 

You currently have four partitions. Unless installed with EFI (both Win and Ubuntu) you are going to need to make some changes and create an extended partition as your fourth partition if you wish to create more partitions.

---

