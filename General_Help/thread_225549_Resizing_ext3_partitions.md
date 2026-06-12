---
title: "Resizing ext3 partitions"
date: 2006-07-29
forum: General Help
---

### Post by diamond on 2006-07-29
I have a few GB of unallocated space on my drive, right *before* my /dev/hda3 partition. I would like to expand the hda3 partition to use this space, but I can't figure out how to get GParted to do this.

Is it possible to expand a partition into space that is before it, or can you only do that with space after the partition?

---

### Post by Herman on 2006-07-29
There is a new version of GParted LiveCD expected to come out very soon which will include the functionality for 'moving' all file systems.

FAT32, and I think NTFS and Linux ext2 and swap areas have always been easy to 'move' for most partitioning software.
Linux 'journalling' filesystems like ext3 and reiserfs are fixed at the 'start point', or beginning but can easily be resized from the end.
They can be copied and pasted, but then they will be given a new partition number. 
If they get a new partition number if it's an operating system you just need to re-install grub and edit /etc/fstab with the new partition numbers.
Another solution is to copy  a partition to somewhere temporarily and delete the original, then paste the temporary copy where you really want it. Then it will be given the old partition number again and you can just boot it and use it as normal.
To see illustrations of what I'm talking about,[* Click Here*]("http://users.bigpond.net.au/hermanzone/p6.htm#Managing_My_Partitions_with_GParted").

I recommend [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") for this type of work. If you can wait a few days until GParted LiveCD version -0.3 comes out it will be easier for you. GParted LiveCD is free and it's less than around 30.0 mb to download. 
I am a big fan of GParted Live CD and I have been using it since the Alpha 3 version 0.0.9. 
Regards, Herman :D

---

### Post by mlind on 2006-07-29
Does evms tools contain anything that supports this?
When you're installing Ubuntu from scratch next time, consider using LVM. Expading and shrinking your partitions will be very easy then.

---

### Post by diamond on 2006-07-30
> **Herman said:**
> There is a new version of GParted LiveCD expected to come out very soon which will include the functionality for 'moving' all file systems.

FAT32, and I think NTFS and Linux ext2 and swap areas have always been easy to 'move' for most partitioning software.
Linux 'journalling' filesystems like ext3 and reiserfs are fixed at the 'start point', or beginning but can easily be resized from the end.
They can be copied and pasted, but then they will be given a new partition number. 
If they get a new partition number if it's an operating system you just need to re-install grub and edit /etc/fstab with the new partition numbers.
Another solution is to copy  a partition to somewhere temporarily and delete the original, then paste the temporary copy where you really want it. Then it will be given the old partition number again and you can just boot it and use it as normal.
To see illustrations of what I'm talking about,[* Click Here*]("http://users.bigpond.net.au/hermanzone/p6.htm#Managing_My_Partitions_with_GParted").

I recommend [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") for this type of work. If you can wait a few days until GParted LiveCD version -0.3 comes out it will be easier for you. GParted LiveCD is free and it's less than around 30.0 mb to download. 
I am a big fan of GParted Live CD and I have been using it since the Alpha 3 version 0.0.9. 
Regards, Herman :D

If it's only a few days, then yeah, I think I can wait. I'm currently using GParted LiveCD 0.2.5, and it's proven very valuable.

---

### Post by diamond on 2006-07-30
BTW, is it possible to re-install GRUB (and *just* GRUB) from the Ubuntu LiveCD? If so, how?

---

### Post by Herman on 2006-07-30
diamond, 
>  If it's only a few days, then yeah, I think I can wait. I'm currently using GParted LiveCD 0.2.5, and it's proven very valuable. I really don't know if it will be just a few days or a week or two. All I know is what information I can glean from [GParted News]("http://gparted.sourceforge.net/news.php"). New releases of GParted seem to come out fairly often though, so it could be anytime really.

    > BTW, is it possible to re-install GRUB (and *just* GRUB) from the Ubuntu LiveCD? If so, how? Yes, it's pretty easy, this is how I do it from a GRUB shell,
         Re-install Grub with a GRUB shell eg; with Live CD..........................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
Regards, Herman :D

---

### Post by diamond on 2006-07-30
> **Herman said:**
> diamond, 
 I really don't know if it will be just a few days or a week or two. All I know is what information I can glean from [GParted News]("http://gparted.sourceforge.net/news.php"). New releases of GParted seem to come out fairly often though, so it could be anytime really.

     Yes, it's pretty easy, this is how I do it from a GRUB shell,
         Re-install Grub with a GRUB shell eg; with Live CD..........................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
Regards, Herman :D

Now I'm having a problem copying the filesystem. GParted fails while checking the filesystem, claiming that it has been modified. I'm sorry I don't have the exact error; I had no way to save it while running from the GParted LiveCD.

Any idea what might cause this?

I'm also thinking of an alternative strategy: just create a new filesystem in the empty space, copy everything from my current filesystem, re-install GRUB and tell it to boot to the new partition, and (of course) update /etc/fstab in the new partition. Any chance that might work?

---

### Post by diamond on 2006-07-30
> **diamond said:**
> Now I'm having a problem copying the filesystem. GParted fails while checking the filesystem, claiming that it has been modified. I'm sorry I don't have the exact error; I had no way to save it while running from the GParted LiveCD.

Never mind. I forgot that I had to disable journaling on the filesystem (i.e., make it an ext2 filesystem) before doing anything to it. It's copying now.

Thank you so much for all of your help.

---

