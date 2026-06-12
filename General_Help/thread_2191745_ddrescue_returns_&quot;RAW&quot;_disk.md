---
title: "ddrescue returns &quot;RAW&quot; disk"
date: 2013-12-04
forum: General Help
---

### Post by ben40 on 2013-12-04
Hello and sorry for my bad english ..

Here's the first time I have to use ddrescue because of a windows NTFS failing drive with 4 partitions, having much errors ..
I am using this syntax to copy data : [COLOR=#000000][FONT=CourierNew]ddrescue -d -f -n /dev/sda /dev/sdd /dd.log

having :
[/FONT][/COLOR]     sda=wd 500go sectorsize=512 bytes (old damaged drive)
     sdd=wd 500go sectorsize=4kb ( new drive, see the sectorsize difference )[COLOR=#000000][FONT=CourierNew]
[/FONT][/COLOR]
Process isn't over yet .. taking almost two days on the errors sectors ( +2497 ), less than 2gigs remaining to copy

I interrupted the process one time ..
Fdisk does see the partions of sdb, but partition magic or windows aren't able to see them ( see the disk as unformated, raw disk )
and sdd4 is not seen in /dev directory
Testdisk says : number of bytes per sector mismatches 512 (ntfs) != 4096 (HD)

So here are my questions :
    - Is the sector size difference a huge problem in this copy ? How can I correct this ?
    - Is there any way to mount those partitions without having to continue the process ?
    - Do I have to complete the ddrescue process ?
    - Why do fdisk see partitions and not gparted?
    - Is there any similar program which can complete this, escaping error sectors, just copying files according to the MBR ?


Here is what testdisk sees of sda : [http://i.snag.gy/3hRMz.jpg](http://i.snag.gy/3hRMz.jpg)
Here is what testdisk sees of sdd : [http://i.snag.gy/zvI7C.jpg](http://i.snag.gy/zvI7C.jpg) ( note multiple records .. )
Here is what he purpose to do on sdd : [http://i.snag.gy/R1imo.jpg](http://i.snag.gy/R1imo.jpg) ( I have to delete two partitions in order it to be okay, and I'm not okay with that, due to the time it took to copy data via ddrescue )

I later connected the backup drive sdd to another external case, and guess what, the drive & partition fully worked  :)


Thanks in advance, 
Regards
Ben

---

