---
title: "Reformat from ext4 to swap - can I recover data?"
date: 2016-08-18
forum: General Help
---

### Post by LeadHop on 2016-08-18
I messed up and ended up formatting my main storage to swap through the terminal from a live usb. 

I meant to turn /dev/sda7 to swap but ended up turning /dev/sda5 to swap, which was my main storage.

Because I've been booting from a live disk the partition has not been touched; it hasn't even been mounted.

is there any way to recover the data from this partition?

---

### Post by oldfred on 2016-08-18
The live installer uses swap if found, do not reboot.
The gparted live ISO does not use swap so if you have shutdown only boot with it.

Use Disks and change back to ext4, do not format, just change type.
Underneath the partition display is a tiny gears icon.
Click on swap and then the gear icon. Use Edit partition not Format partition.
It should show as swap and offer all the formats available to change to.

---

### Post by LeadHop on 2016-08-18
thanks for the quick reply - using disks, it displays all the partitions but displays the ubuntu partition as unallocated free space and is uneditable.

running fdisk shows this though:

```
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1               63      80324      80262  39.2M de Dell Utility
/dev/sda2  *         81920   37269503   37187584  17.8G  7 HPFS/NTFS/exFAT
/dev/sda3         37269504  450111487  412841984 196.9G  7 HPFS/NTFS/exFAT
/dev/sda4        450113534 1465147391 1015033858   484G  5 Extended
/dev/sda5        450113536 1434427391  984313856 469.4G 83 Linux
/dev/sda6       1434429440 1452673580   18244141   8.7G 83 Linux
/dev/sda7       1452675072 1465147391   12472320     6G 82 Linux swap / Solaris
```

sda5 is the one that needs to be recovered from swap to ext4 but does not show on Disks.  Shows up on gparted and fdisk however.

[EDIT]: clicking the PLUS symbol next to the gears for the unallocated free space gives options to change the disk space w/o overwriting data but says cannot create new partition as there are four primary partitions already.  So it looks like it's doable somehow...

---

### Post by oldfred on 2016-08-18
Often changes are not seen until you reboot.
Or remount.
But now not sure what those changes would be.

But I hesitate to suggest reboot as the Ubuntu live installer mounts & uses swap. Probably both when you have two. And then your data may get overwritten.

If that is showing partition table correctly you can just get fdisk to re-write that back into partition table, so it should be saved? Only use fdisk for the older MBR(msdos), but not for newer gpt. Only the version of fdisk in 16.04 is updated to correctly see gpt partitioned drives.

       sudo fdisk /dev/sda 
   Press "w". That rewrites the partition table. Reboot (using Supergrub) so that the changes take effect.  
      Or to review partitions in detail:
 You can possibly repair a MBR partition with fdisk:
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk
q  # quit

---

### Post by LeadHop on 2016-08-19
yes after some googling I'm trying to just rename the partition table from swap to ext4...

how do you suggest I go about it?  

fdisk and command f brings up unknown command.

I'm thinking about trying this method:

[http://shearer.org/Ext4_recovery](http://shearer.org/Ext4_recovery)

```
 mkfs.ext4 -S /dev/YOUR_DEVICE
```

possibly.

The change from ext4 to swap was already done through a live install USB unfortunately so that's kind of already a done deal... just won't be rebooting until this matter is resolved.

---

### Post by oldfred on 2016-08-19
This is what man says about the -S option
man mkfs.ext4

>        -S     Write superblock and group descriptors only.  This is useful  if
              all  of the superblock and backup superblocks are corrupted, and
              a last-ditch recovery method is desired.  It  causes  mke2fs  to
              reinitialize  the  superblock  and  group descriptors, while not
              touching the inode table and the block and inode  bitmaps.   The
              e2fsck  program  should  be run immediately after this option is
              used, and there is no guarantee that any data will  be  salvage&#8208;
              able.   It  is critical to specify the correct filesystem block&#8208;
              size when using this option, or there is no chance of recovery.


Did any of the fdisk command work? p, v etc?

---

### Post by LeadHop on 2016-08-19
So it's been resolved, and from a cursory going over... it looks to be okay.  

Everything was run from a live boot USB.

I ran 

```
sudo mkfs.ext4 -S /dev/(YOUR sdaNUMBER HERE)
```

Which was quick and painless.

The resource I found also recommended running 

```
sudo fsck.ext4 -v /dev/sda5/
```

so I did and... ran into a bit of trouble.  It turned out my hard drive had a good amount of bad sectors and it prompted me to whether they should fix/clear certain things I had no idea what they're talking about. htree index, index_fl flag, dtime, etc etc. I had no idea what I was doing and started with going through each one individually but there were thousands... so i just held [y] for a good three minutes. Scary stuff.

I ended up having to reinstall ubuntu to the root partition in the end because something went wrong and it would no longer boot, just hang on the splash screen and send me to emergency, where all commands were not recognized.  But once I reinstalled and rebooted, everything seems to be fine.

Ubuntu somehow recognized the important files/folders and when I opened firefox, it brought it back up with all the tabs and add-ons.  I installed chrome, and it also brought up my old tabs with add-ons.  I remounted root to home in the other partition, rebooted, and everything seems to be peachy so far.  I won't know until I run into a file/folder I can't access later on down the road, because that bad sector's going to spring up on me some time.  I think I read something about looking into the "lost+found" folder later?

When I installed calibre, it even auto linked itself to my old calibre folder w/o prompt.  Idk how the reinstall just didn't wipe everything from the root folder.

For future readers, if you messed up like I did, try giving this a shot, but MAKE A BACKUP OF THE PARTITION.  I was out of options so I had to do everything in ink but if I had a spare drive I definitely would've made a disk image of the partition.

Also to people with related issues with ext4 - give this a reading over:  [https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

when I tried running

```
sudo mke2fs -n /dev/xxx
```

it gave me some big scary prompt about how it will mount the drive and could cause damage and I chickened out so I went with the first two bits of code up there that seemingly fixed everything.

I did make a backup of my root drive on to a disk; should i move over those files back over into the new root?

---

### Post by oldfred on 2016-08-19
The only files I might review would be any configuration files in /etc that you manually edited. I normally copy those like my 40_custom or fstab into a folder in /home so my backup of /home includes those settings. 
If you start copying files from previous install, you may get everything out of sync.

To avoid the having to press y, use the two pass version:
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by LeadHop on 2016-08-20
that's a new one - thanks!

---

