---
title: "Moved * boot partition to swap on accident"
date: 2015-05-04
forum: General Help
---

### Post by highspider on 2015-05-04
The PC is still running and will stay On. 
right now as I'm typing this. NO way im I turning it off.
Since I'm not sure exactly what I did and don't want to make things worse I'm asking 
I'm sure its a simple fix.  But I would rather ask.  
Some how I made the swap partition the boot partition

and all my extended partition in /dev/sda2/ have disappered in gnome-disks

the way the hard is suppose to be set up.
/dev/sda2 is extended with /dev/sda5 swap (empty), /dev/sda6 (ubuntu fs) and /dev/sda7 encrypted file (empty)  

/dev/sda3 is XP NTFS
/dev/sda4 is NTFS storage (both were untouched) 

sudo fdisk -l
Device     Boot     Start        End    Sectors   Size Id Type
/dev/sda2     2046     71327743   71325698   34G  5 Extended
/dev/sda3    71327744   126527487     55199744    26.3G  7 HPFS/NTFS/exFAT
/dev/sda4    126527944   1953520064   1826992121   871.2G  7 HPFS/NTFS/exFAT
/dev/sda5  *    62943232     71327743    8384512   4G   82 Linux swap / Solaris 
/dev/sda6    2048   54556671     54554624   26G   83 Linux
/dev/sda7    54558720   62943231      8384512       4G 83 Linux

and here is screen shot of gnome-disks

 [ATTACH=CONFIG]261773[/ATTACH]


How do change my Files system back to the way it should be 
where /dev/sda2/ is extended and has my linux partitions in it sda5 sda6 sda7

---

### Post by grahammechanical on 2015-05-04
If this is correct

> the way the hard is suppose to be set up.
/dev/sda2 is extended with /dev/sda5 swap (empty), /dev/sda6 (ubuntu fs) and /dev/sda7 encrypted file (empty)  

I do not think that you had a boot partition. so, I do not think that you changed the boot partition to a swap partition. What I think you have done (not that it helps in anyway), is you have deleted the extended partition that was holding the logical partitions of sad5, sda6, & sda7.

I am assuming that sda 3 and sda4 are primary partitions. 

The Disks utility shows an extended partition as a long band sitting over the logical partitions that are in the extended partition. Disks does that on my system but not on your system. So, I conclude that you have deleted the extended partition and with it the logical partitions inside it.

If you can still access your data files, I would start backing them up somewhere if I was you.

Regards.

---

### Post by highspider on 2015-05-04
----------------------------------------------------------------------------------------------------------------------------------------

I would have asked for help sooner but I felt like such a Lame for doing something so stupid!
know my stupidity is immortalized on this website! 

----------------------------------------------------------------------------------------------------------------------------------------

some how I selected make swap the [ ]boot partition which some how erased my extend partition table. that's what I meant by made swap the boot partition. there was never extend partition 
by it self just like a container box around /dev/sda5 /dev/sda6 /dev/sda7  However, /dev/sda2 does show up now as unknown partition type which should be the extend.  So yes its gone.  I didn't delete though I just made swap the [ ]boot and it died.  

I installed gparted  (with out ever using it) and it says warning! 

Partition(s) 3 on /dev/sdb have been written, but we have been unable to inform the kernel of the change, 
probably because it/they are in use.  As a result, the old partition(s) will remain in use. 
 
You should reboot now before making further changes.

and shows the whole disk as being not-allocated.
gnome-disks Like the screen shot shows all partition types Unknown and file system as they really are  (that what scares me about losing /dev/sda4)

So they are still there for now.  I do not have an other drive to back up on too.
I could transfer my files to /dev/sda4 but I don't know what reboot would do.
I think I need to manually enter partition tables some how/where I just don't know how that's done because I know Start End sectors for all my partitions
 
[COLOR=#000000]How do manually enter partition info [/COLOR][COLOR=#000000]Start Stop Sectors.
[/COLOR]
[COLOR=#000000]/dev/sda2 2046 71327743   Extended[/COLOR]
[COLOR=#000000]/dev/sda3 71327744 126527487   HPFS/NTFS/exFAT[/COLOR]
[COLOR=#000000]/dev/sda4 126527944 1953520064  HPFS/NTFS/exFAT[/COLOR]
[COLOR=#000000]/dev/sda5 62943232 71327743 Swap [/COLOR]
[COLOR=#000000]/dev/sda6 2048 54556671  Linux[/COLOR]
[COLOR=#000000]/dev/sda7 54558720 62943231 Linux[/COLOR]

-------------------------------- right now fdisk -l --------------------------------------------

/dev/sda2            2046   71327743   71325698    34G ee GPT   <- (what the opps) Needs fixed
/dev/sda3        71327744  126527487   55199744  26.3G  7 HPFS/NTFS/exFAT      should be fine wasn't extend partition
/dev/sda4       126527944 1953520064 1826992121 871.2G  7 HPFS/NTFS/exFAT  should be fine wasn't extend partition

--------------------------------------------------------------------------------------------------

I can still mount all my partitions and use them  I'm just screwed if the computer goes off.
I think I will have to buy backup hard drive since my files are way too many and large for DVD's or Pen drives
Well as long as lighting don't strike the power out in the next 4-7 standard delivery time days then I should be ok.

--------------------------------------------------------------------------------------------------------------------------------------

there should be away to edit the MBR master boot record and just specify where on the partitions (sectors) are on the disk and then 
add EBR extended boot record to sda2.   Its a binary file so its not like I can just gedit on it.

---

### Post by oldfred on 2015-05-04
Somehow with gparted or several other commands you move boot flag to sda5, the swap partition.
But grub does not use boot flag. Windows has to have boot flag on partition with boot files when using the Windows boot loader. It really should only have a boot flag on a primary NTFS partition with the Windows boot files. For some Linux only systems a boot flag is still required as BIOS checks before even loading MBR if a partition has a boot flag. So we always suggest one.

Somehow you also changed extended partition to be sda2 and include the first partition on drive. Partitions do not have to be in order on drive and if repartitioning often physical order does not match number order. That can  be reset, but in past broke booting as partition number was critical for booting, but now UUID is usually used.

If you have gpt signatures on drive you may want to review with fixparts.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by highspider on 2015-05-05
Thank for the response.  

I marking this as solved because I believe I have enough info now to fix my extended partition; however, I will wait to reboot till I can back my info up.  
I'm still confused on why its making use sector 2048 as start sector of my type 5 extended partitions beginning when before it was start sector 2046.  And I need sleep to finish testing what i've done.

---

### Post by oldfred on 2015-05-05
All new partitioning software starts at sector 2048 for first partition. 
But you must have changed the first partition to be inside an extended partition and the extended partition must be a sector or two in front or actually start of actual sector must be a sector or two after the start of the extended partition. 
So extended partition start became 2046. If an SSD or new 4K drive you want first partition you write into to start at 2048 and all others to have start sectors that can be divided by 8. You do not write into the extended, just into the logical partitions inside the extended.

Part of why I prefer gpt, but you can only use gpt with new UEFI systems if dual booting with Windows as Windows only boots from gpt partitioned drives with UEFI.
But if only Linux on a drive, you can use gpt and I have since 10.10 booting in BIOS mode on a BIOS only system. Windows XP was on another MBR drive, so no issues.

---

### Post by highspider on 2015-05-11
I found a much better way of recovering lost data 

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
```
sudo apt-get install testdisk
```

I was able to recover most of my data from the lost partitions.

---

