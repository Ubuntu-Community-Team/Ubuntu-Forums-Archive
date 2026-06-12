---
title: "Uable to mount 7.8 GB Volume"
date: 2016-10-02
forum: General Help
---

### Post by Douglas_H_Campbell on 2016-10-02
After a recent automatic update I can't access a 7.8 GB Drive.  Info I get is as follows:

  	 	 	 	   [SIZE=2]****************************[/SIZE]
 [SIZE=2]Error mounting /dev/sdb1 at /media/doug/DC4E524B4E521E98: [/SIZE] 
 [SIZE=2]Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,[/SIZE]
 [SIZE=2]uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb1" [/SIZE] 
 [SIZE=2]"/media/doug/DC4E524B4E521E98"' exited with non-zero exit status 21: [/SIZE] 
 [SIZE=2]mount: according to mtab, /dev/sdb1 is already mounted on [/SIZE] 
 [SIZE=2]/media/doug/DC4E524B4E521E98[/SIZE]
 [SIZE=2]****************************[/SIZE]
 

 [SIZE=2]Error when getting information for file '/media/doug/DC4E524B4E521E98': [/SIZE] 
 [SIZE=2]No such file or directory[/SIZE]
 [SIZE=2]****************************

Any suggestions to fix this problem?  Thanks.  Doug
[/SIZE]

---

### Post by yancek on 2016-10-02
Run:  sudo blkid to see if you have a partition with that UUID:  [SIZE=2]DC4E524B4E521E98

Since it is an ntfs partition, is this just  a data partition or a windows OS?  If an OS, did you do a full shutdown and not hibernate?
[/SIZE]

---

### Post by Jimysbil on 2016-10-02
1) Do you mean 'After a recent Windows automatic update' ??
2) Is this a USB Stick or a partition on your Hard Disk??

According to the UUID it seems your partition type should be NTFS.
If your filesystem is OK you probably have a hibernated system as yancek reported.

If you have Dual boot with Windows boot into Windows, open a command prompt (as Administrator) and type:
```
powercfg /h off
```

You could also try to mount your partition as read-only and check if you can mount it in order to see the files inside from ubuntu.
Open a terminal and type:
```
sudo su
mkdir -p /mnt/mnt
mount -t ntfs -o ro /dev/sdb1 /mnt/mnt
```

---

### Post by Douglas_H_Campbell on 2016-10-03
1) Yes, this was a Ubuntu auto update.
2) This is a USB device

It was full shutdown.   sudo blkid shows as follows:

                        [SIZE=2]doug@doug-Ubuntu:~$  sudo blkid [/SIZE] 
 [SIZE=2]/dev/sda1: LABEL="RESERVED" UUID="6EB5-18D1" TYPE="vfat" PARTUUID="1e3e3b0c-01" [/SIZE] 
 [SIZE=2]/dev/sda2: UUID="8C2A36D52A36BC50" TYPE="ntfs" PARTUUID="1e3e3b0c-02" [/SIZE] 
 [SIZE=2]/dev/sda4: LABEL="DATA" UUID="DA24B96624B945F3" TYPE="ntfs" PARTUUID="1e3e3b0c-04" [/SIZE] 
 [SIZE=2]/dev/sda5: UUID="a9e6bd0b-58e5-4678-b9ff-4d39e6bd6a75" TYPE="swap" PARTUUID="1e3e3b0c-05" [/SIZE] 
 [SIZE=2]/dev/sda6: UUID="a3d6a623-cd71-455e-a272-376cfb96b1bf" TYPE="ext4" PARTUUID="1e3e3b0c-06" [/SIZE] 
 [SIZE=2]/dev/sda7: UUID="7e62a13a-41af-46da-b32d-a15239d3b595" TYPE="ext4" PARTUUID="1e3e3b0c-07" [/SIZE] 
 [SIZE=2]/dev/sdb1: UUID="DC4E524B4E521E98" TYPE="ntfs" PARTUUID="56be28e2-01" [/SIZE] 
 [SIZE=2]doug@doug-Ubuntu:~$ [/SIZE] 
  
********************************
Result from running.
sudo su
mkdir -p /mnt/mnt
mount -t ntfs -o ro /dev/sdb1 /mnt/mnt

Is this:

******************






    [sudo] password for doug:  
 root@doug-Ubuntu:/home/doug# sudo su  
 root@doug-Ubuntu:/home/doug# mkdir -p /mnt/mnt  
 root@doug-Ubuntu:/home/doug# mount -t ntfs -o ro /dev/sdb1 /mnt/mnt  

I had delete all Ubuntu files from the USB device earlier, so that is why it shows nothing.

I am having trouble signing in on Windows as Administrator but will do so when I get things sorted out and run
"powercfg /h off".  

Thanks for the help.  Doug

---

### Post by Jimysbil on 2016-10-03
After the execution of the command:
```
mount -t ntfs -o ro /dev/sdb1 /mnt/mnt
```
and as long as it came without some error you should be able to see your files inside [COLOR=#ff8c00]/mnt/mnt[/COLOR] folder.

As for Windows you don't have to log in as Administrator but to execute a CMD prompt with right-click --> Run as Administrator and run the command:
```
powercfg /h off
```
in case your fastboot feature on windows in enabled.This will completely terminate your Windows OS and you will be able to mount your NTFS partitions without problem on linux.

I think everything should be normal according to the blkid results.Your device has one partition NTFS and probably not damaged.

You will know for sure if you run a [COLOR=#ff8c00]chkdsk[/COLOR] from inside Windows.

---

### Post by Douglas_H_Campbell on 2016-10-04
[INDENT]

After the execution of the command:
 	Code:
 	mount -t ntfs -o ro /dev/sdb1 /mnt/mnt 
I get:

*********************

  	 	 	 	   doug@doug-Ubuntu:~$ sudo mount -t ntfs -o ro /dev/sdb1 /mnt/mnt  
 [sudo] password for doug:  
 mount: according to mtab, /dev/sdb1 is already mounted on /mnt/mnt  
 

 doug@doug-Ubuntu:~$  
  
*************************

 [COLOR=#ff8c00]/mnt/mnt[/COLOR]  shows nothing.

***************************
After running "chkdsk e:" I get the following:

  	 	 	 	   [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]Microsoft Windows [Version 6.3.9600][/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]c) 2013 Microsoft Corporation. All rights reserved.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]C:\Windows\system32>chkdsk e:[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]the type of the file system is NTFS.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]WARNING!  F parameter not specified.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]running CHKDSK in read-only mode.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]Sage 1: Examining basic file system structure ...[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]1872 file records processed.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]File verfication completed.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]0 large file records processed.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]0 bad file records processed.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]Stage 2: Examining file name linkage ...[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]an nvalid filename Screenshot from 2016-08-08 12:07:39.png (66) was found in directory[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]151.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]All filenames for File 66 are invalid.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]Minor file name errors were detected in file 66.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]am invalid filename Screenshot from 2016-08-08 12:07:39.png.trashinfo (209) was[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]found in directory 150.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]All filenames for File 209 are invalid.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]Minor file name errors were detected in file 209.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]Index entry Screenshot from 2016-08-08 12:07:39.png.trashinfo in index $I30 of f[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]le 150 is incorrect.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]Index entry Screenshot from 2016-08-08 12:07:39.png in index $I30 of file 151 is[/SIZE][/FONT][/COLOR][/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]incorrect.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]1912 index entries processed.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]Index verification completed.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]Errors found.  CHKDSK cannot continue in read-only mode.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT] [LEFT][COLOR=#000000][FONT=Times New Roman][SIZE=3]:\Windows\system32>[/SIZE][/FONT][/COLOR][/LEFT] [LEFT]
[/LEFT]  Should I use "chkdsk e: /f" to fix the problem or something like "scandisk e: /nosave" before 
running "powercfg /h off"??  Then try Ubuntu again.


Thanks a lot.
Doug


[/INDENT]

---

### Post by Jimysbil on 2016-10-04
Does your USB have write protection??If it has some switch for write protection just push it to the oposite way.If not you are probably in trouble and your USB Stick in locked.

The command 'powercfg /h off' has nothing to do with 'chkdsk'.You have to run this command just ones in order to disable hibernation for windows.

If you don't have files you need inside your USB Stick , it would better if you was trying to create a new partition table for this device with gparted.

---

### Post by Douglas_H_Campbell on 2016-10-05
No, my USB doest not have write protection.

Okay, may try to use gparted.  Thanks for your help.

Doug

---

### Post by Douglas_H_Campbell on 2016-10-09
I decide to do a restore, back to before the last Ubuntu update.  When I did this the USB flash drive was okay.
Because the update was so large,I used the "partial upgrade" option rather then the "continue" option.  We're back to normal.  Thanks a million.  Doug

---

