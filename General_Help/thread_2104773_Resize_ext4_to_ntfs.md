---
title: "Resize ext4 to ntfs"
date: 2013-01-14
forum: General Help
---

### Post by Longday on 2013-01-14
I have a dual boot laptop with 12.04 LTS and Win7.
Would like to reduce the ext4 space and increase the ntfs space.

With my past dual boot set up's I ended up fairly low for disk space on the Ubuntu side.
So this time I gave more space to the Linux side than before.

In hindsight I was too generous and would like to reduce the ext4 side by around 150Gb and increase ntfs by same amount.

So my question is, how can I do this using the live cd and the existing disk config below without reinstalling either OS?
Don't mind if the recovered space appears as seperate disk in Windows.

Present config: (sorry about the formatting)

                                          
/dev/sda1         fat16                  size 39.19  MiB          used 213.00 KiB          free 39.98 MiB  Dell   diag
/dev/sda2       ntfs                     size 19.81  GiB               used 12.72  GiB            free 7.09  GiB           boot
/dev/sda3    ntfs                      size 510.29 GiB                    used 331.28 GiB     free 179.02 Gib  win7
/dev/sda4    extended                        size 401.37 gib              used           -  free                      -
/dev/sda5    linux-swap size                      953.00 mib               used          - free                            -
/dev/sda6    ext4                             size 400.44 gib               used           28.07  GiB         free 372.36 GiB root

---

### Post by decrepit on 2013-01-14
basicaly, back up all data!!!
 start gparted from live cd, shrink the ext4 partition, create new ntfs partition.

---

### Post by wyliecoyoteuk on 2013-01-14
Try Parted Magic
[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

You may not be able to resize sda4 (extended partition) with an active partition in it, not sure, but if you can you would need to reduce sda6 and move sda5 and sda6 to the end of the partition.

---

### Post by TheFu on 2013-01-14
I would 
* backup your EXT4 partition to another disk ... backups are fantastic
* using gparted off a boot disc, delete the ext4 partition
* using windows tools, expand or create a new NTFS partition (this is a good idea on systems where both OSes must share disks)
* using gparted off a boot disc, create a new ext4 partition (20G should be 2x more than most people need for a desktop OS/apps)

In the future, I'd keep large files like music and videos on the NTFS "Data" partition.

If you are using Windows8, be aware that NTFS partitions aren't really unmounted between boots thanks to fastboot, so editing any files from Linux may cause corruption.  The NTFS drivers that recognize this aren't released yet.

---

### Post by c2tarun on 2013-01-14
all the above solutions are correct, but try re-sizing you ntfs partition first before deleting it. I remember it worked once for me. I was partitioning my memory card for android stuff.

---

### Post by TheFu on 2013-01-14
There is a resize2fs command. I've used it to make a file system larger, but never smaller. **man resize2fs** explains all. Going smaller works on unmounted file systems.  Going larger works on mounted file systems if the kernel supports it. This is the part that I've used - needed to add 20G to an email server but didn't want to take it offline first.  It worked multiple times.

---

### Post by Longday on 2013-01-14
Thanks for all the input.

What I was (am) hoping to do is shrink the ext4 partion down to 250Gb and create a new ntfs partion of 150gb in it's place.
My concerns were 1. if it is possible to shrink a root partion as I saw conflicting reports before I posted this thread and 2. if Windows would "see" the new ntfs partion in it's current position. 

If I have understood the above replies correctly the answer to 1. is possibly, while 2. is I will need to move them around slightly.

I do have a complete Linux back up so fairly happy on that side. 
Windows not quite as easy due to the amount of data and s/w and lack of system disks as Dell don't supply them with new machines any more.

Armed with the info from this thread I will find some time in the next couple of weeks to give this a go and mark it as solved when successfully completed.

Thanks again.

---

### Post by TheFu on 2013-01-14
The real key is to only use Windows partition tools for NTFS and only use Linux tools for non-NTFS stuff.  There are big changes happening  in HDDs and partitioning now, so this is important.

When you do partition stuff on Linux, always use **parted** or **gparted** now, **NOT fdisk**. fdisk (and cfdisk, sfdisk) are not always ready for GPT partitions and 4K sector HDDs.

Of course, having a good backup is **mandatory** before doing any of this stuff. backup, backup, backup.

---

### Post by Longday on 2013-01-23
O.K

All went very smoothly, simply and surprisingly quickly.
What I ended up doing was: 
1. Ran a Live CD and resized the ext4 partition (sda6) to around 200 Gib
2. Created a new logical ntfs partition (sda7) of around 200 Gib.

I did consider shrinking the extended partition and extending the primary ntfs (sda3) rather than creating a new logical drive but was warned by gparted that this could result in a failure of the PC to boot. 
I didn't want to get into a situation of having to try to reconfigure/locate Grub so opted for the above method, as the new data appearing on a 2nd disk in Windows was what I was aiming for.

Thanks for all the help.

---

