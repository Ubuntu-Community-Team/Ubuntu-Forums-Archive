---
title: "creating a disk image of the entire HDD"
date: 2008-04-30
forum: General Help
---

### Post by Ace_NoOne on 2008-04-30
Hello,

Is there a simple way to create an image of my entire HDD?
I need to resize the existing partitions, and want to make sure I have a full, easy-to-restore backup in case something goes wrong.

My laptop currently has the following partitions:[LIST]
[*]sda1: ntfs, 49.98 GiB
[*]sda2: ntfs, 9.86 GiB
[*]sda3: ext3fs, 14.03 GiB
[*]sda4: -extended-
[*]sda5: swap (v1), 674.57 MiB
[/LIST]
The first two partitions are from Windows XP, which need to be downsized so I can add some space to the Ubuntu partition(s). 

Also, I only have an NTFS-formatted external HDD - can I use that to store the image? (Not sure how reliable the Linux NTFS drivers are.)

Thanks!

---

### Post by KeyserSoze93 on 2008-04-30
run "man dd"

dd is a tool used for making exact copies of a file (or device file).

so you would use a command such as "dd if=/dev/MY_DRIVE of=backup.img"

i think it doesn't work with mounted drives though, so if you wanted to make an image of your root drive you would have to run it from a live CD like knoppix

---

### Post by Ace_NoOne on 2008-04-30
Thanks, Keyser.
I've thought about using dd, but I had hoped there'd be an easier solution - ideally creating a boot disc to automatically restore the entire HDD (all partitions) as it was before.

What do you think of [Partimage]("http://www.partimage.org/Main_Page")?

---

### Post by MyR on 2008-04-30
partimage is a good choice, it needs to be run from a livecd though.

peace

---

### Post by scorp123 on 2008-04-30
> **Ace_NoOne said:**
>  I need to resize the existing partitions, and want to make sure I have a full, easy-to-restore backup in case something goes wrong. You want partimage or mondo-rescue ... "dd" is not the solution here IMHO, because it is only capable of making 1:1 binary copies. In other words: If you use "dd" to copy a 50 GB partition then this copy will use exactly 50 GB of space somewhere ... and besides: It takes a really long time to copy so many GB's around.

As I wrote above ... I'd suggest e.g. partimage:
[http://www.partimage.org](http://www.partimage.org)

Or mondo-rescue:
[http://www.mondorescue.org/](http://www.mondorescue.org/)

---

### Post by CPSC Sam on 2008-05-10
I just setup a Windows machine and would like to create a backup image that I can use as a restore point. Based on [http://www.linuxweblog.com/dd-image]("http://www.linuxweblog.com/dd-image")


Using a LiveCD, where sda1 (NTFS drive) and sdb1 is my external (XFS).
> 
# fdisk -l /dev/sda

Dsik /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280

   Device Boot      Start      End      Blocks    Id  System
/dev/sda1   *           1    38912   312560608     7  HPFS/NTFS


To backup, I ran
> 
# dd if=/dev/sda conv=sync,noerror bs=64K | gzip -c > /mnt/sdb1/devPC.img.gz
4883925+1 records in
4883926+0 records out
320072974336 bytes (320 GB) copied, 6265.24 seconds, 51.1 MB/s


To restore the command would be:
> 
  # gunzip -c /mnt/sdb1/devPC.img.gz | dd of=/dev/sda conv=sync,noerror bs=64K 


Does anyone know if this will work correctly? I ask because my output file is 320072974336 bytes while my actual drive based on fdisk is 320072933376.

320072974336-320072933376 = 40,960 byte difference.

This has got me a little concerned. Will the restore command work?

---

### Post by ghost_ryder35 on 2008-05-10
> **scorp123 said:**
> You want partimage or mondo-rescue ... "dd" is not the solution here IMHO, **[COLOR=red]because it is only capable of making 1:1 binary copies[/COLOR]. In other words: If you use "dd" to copy a 50 GB partition then this copy will use exactly 50 GB of space somewhere** ... and besides: It takes a really long time to copy so many GB's around.
 
As I wrote above ... I'd suggest e.g. partimage:
[http://www.partimage.org](http://www.partimage.org)
 
Or mondo-rescue:
[http://www.mondorescue.org/](http://www.mondorescue.org/)
um... no... pipe it through gzip :)
```

# dd if=/dev/sda | gzip > /mnt/sda1/system_drive_backup.img.gz
 

```

---

### Post by scorp123 on 2008-05-10
> **ghost_ryder35 said:**
> um... no... pipe it through gzip :)
```

# dd if=/dev/sda | gzip > /mnt/sda1/system_drive_backup.img.gz 

``` That solves the problem of the image file occupying too much space, but it still does not prevent the problem that you're still copying bit by bit even empty sectors of your harddisk and that you'd have to write back those sectors bit by bit when you unpack all of this again. Also, using "gzip" on really large amounts of data like this could create very high CPU loads on some systems. Thus "dd" is still pretty far away from being "ideal" in any sense. Where "dd" shines is making backups of CD's, DVD's, floppies and boot sectors ... but entire HDD partitions? There are better solutions, really :)

---

### Post by Ace_NoOne on 2008-05-12
> **scorp123 said:**
> Thus "dd" is still pretty far away from being "ideal" in any sense. Where "dd" shines is making backups of CD's, DVD's, floppies and boot sectors ... but entire HDD partitions? There are better solutions, really :)
Those were my concerns as well.
I haven't gotten around trying PartImage yet - hopefully next week(end)...

PS: Sorry for the late response - I must have missed the e-mail notification.

---

