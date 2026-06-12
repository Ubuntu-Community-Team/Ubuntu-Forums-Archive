---
title: "Bad partition table problem"
date: 2014-11-03
forum: General Help
---

### Post by far on 2014-11-03
Hello Community.

I am so to speak, deep in Sh...

I use a dual-boot Lenovo Thinkpad T430 (win 8 / Ubuntu 14.04), with 2 hard drives: one with the operating systems and one for data which has 2 partitions (NTFS and EXT4). 

Today, I amlost had a stroke (ok, I'm barely 30 but with it was such a shock...) when I saw the data disk did not mount and had many strange partitions instead of the usual 2... This is an image of the paritions on the disk done by running  ```
parted /dev/sdab
```:

```
Model: ATA HGST HTS725050A7 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 1      4194kB  8389kB  4194kB               BOTA0     msftdata
 2      8389kB  12.6MB  4194kB               BOTA1     msftdata
 3      12.6MB  33.6MB  21.0MB               EFS       msftdata
 4      33.6MB  41.9MB  8389kB               PARAM     msftdata
 5      41.9MB  50.3MB  8389kB               BOOT      msftdata
 6      50.3MB  58.7MB  8389kB               RECOVERY  msftdata
 7      58.7MB  92.3MB  33.6MB               RADIO     msftdata
 8      92.3MB  1166MB  1074MB               CACHE     msftdata
 9      1166MB  2777MB  1611MB               SYSTEM    msftdata
10      2777MB  3364MB  587MB                HIDDEN    msftdata
11      3364MB  3372MB  8389kB               OTA       msftdata
12      3372MB  15.8GB  12.4GB               USERDATA  msftdata

```

Nothing to do with the 2 partitions I expected to see!!!!

I assume there is something wrong with my partition table and I am confident my data is still there somewhere, but how to recover it ????

There is a glint of hope when I run TestDisk (see screenshot with link below) but I don't know how to proceed then:

[https://www.dropbox.com/s/keiruzei2srr7yf/Screenshot%20from%202014-11-03%2021%3A56%3A46.png](https://www.dropbox.com/s/keiruzei2srr7yf/Screenshot%20from%202014-11-03%2021%3A56%3A46.png)

When I try the "list files" with Testdisk, it returns "No file found, filesystem may be damaged."

Some background:
LAst week I had a problem with my Android phone (my /data partition was corrupted and could not be mounted) which lead me to dig deep into the world of file sytems to try and rescue the data I thought was lost...So I copied an  image of the faulty /data partition and tried to analyse with TestDisk and parted. I must have done something wrong then because my disk has the partitions of an android device !! 

If you know anything about a way to recover the data in my disk, please let me know. It is urgent, I have 500 Gb if important data in there. I'd be immensely grateful for any tips.

Cheers

---

### Post by Mark Phelps on 2014-11-03
> I have 500 Gb if important data in there. 

Ouch!! Would help if you told us (1) what filesystems were on the drive before you reformatted it, and (2) what filesystems you need to examine to recover files.  Why? Because, in my experience doing data recovery, Windows tools work best for Windows filesystems, and Linux tools work best for Linux filesystems.

---

### Post by oldfred on 2014-11-03
I do not know Android, but the partition names are not familar, so are they typical of Android?
If so, did you dd your Android over the top of your data? 

       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by far on 2014-11-04
Hi Mark and Oldfred !

Thank you very much for these inputs!

@Mark:
The drive was formatted with 1 NTFS and 1 EXT4 partitions. I think the problems has to do with partition table, but could you recommend a tool to recover the EXT4 data? 
I was able to access the files on the NTFS partiton with TestDisk, but impossible to access that of the EXT4 partition ("No file found, filesystem may be damaged")...

@Oldfred:
Yes, the partitions name are typical of Android, and yes, I used dd to copy the image of my Android memory to an image file (on that corrupt EXT4 partition by the way...) ! How did you figure out?? I used the command dd inside an android shell (adb) with as "of=" argument the destination file on that EXT4 partition. Have I done something wrong ? I was able to access the partitions (both NTFS and EXT4) after I used the dd command at least once, before it failed...

What gives me hope is that I could see my files on the NTFS partition with TestDisk, it makes me believe this in only a partition table problem. However if it is, I have no idea how to fix the partition table...

Thank you very much in advance for your help, it feels so good to be not alone!

---

### Post by dragonfly41 on 2014-11-04
I would not give up on TestDisk

> 
I was able to access the files on the NTFS partition with TestDisk, but impossible to access that of the EXT4 partition ("No file found, filesystem may be damaged")...


It is one of the best tools for recovery of EXT* partitions and that EXT4 partition seems to be your focus.

Read up more on the "deep search" feature of TestDisk and you may need to look for "superblocks recovery" ..

Search the TestDisk forum for examples of "deep search" .. e.g.

[http://forum.cgsecurity.org/phpBB3/post12076.html#p12076](http://forum.cgsecurity.org/phpBB3/post12076.html#p12076)

---

### Post by LostFarmer on 2014-11-04
> dd inside an android shell (adb) with as "of=" argument the destination file on that EXT4 partition Do you remember the exact command ? It would help to know.
Was the data hdd partitioned with MBR or GPT ?

'oldfred"--does ubuntu have 'xxd' installed so one can pipe the output of 'dd' to see it in text ?  I'm thinking may need to see the raw data of the MBR, and maybe the first sectors of a GPT partitioning.

---

### Post by oldfred on 2014-11-04
I try not to use dd much, I am too prone to typos. :)

Your of= should have been a file not the drive. like of=android.data

This shows MBR & partition table of sda:
 sudo dd if=/dev/sda bs=512 count=1 | hexdump -C


 read a sector, if sector 0 should be same hex data as dd above:
sudo hdparm --read-sector  115330572 /dev/sda

Do not know details of internal structures of MBR and gpt. gpt does have a backup partition table at end of drive and fixparts can restore the partition table.

If you overwrote with dd all the data where dd was written is gone, it even copies 0 data space. But only that part of drive. If smaller then the data on rest of drive is there somewhere.

---

### Post by far on 2014-11-04
Hi Oldfred and LostFarmer

the command I used with dd was something like: 

```
adb shell dd if=/dev/block/mmcblk0p12 | pv > /media/far/SharedData_Ext41/TEmp/mmcblk0p12_formatted.img 
```

where  SharedData_Ext41 is the name of that EXT4 partition of the disk that seems to be gone. I'm realizing now the output was done with > instead of "of=" and it did write it to a .img file, not a drive. I should mention that the operation was successful and my .img file (~12Gb) was created at that location.

I know I shouldn't have messed with double edged swords like dd, but it was the only way I found to copy my disk image...

I will try to use TestDisk again as  "dragonfly41" mentions, and follow the tips of oldfred. I'll let you know as soon as possible.

In the meantime, please let me know what you think. 

Thank you guys!

---

### Post by far on 2014-11-04
Has anyone checked the partitions found in TestDisk on the screenshot:

> **far said:**
> 

[https://www.dropbox.com/s/keiruzei2srr7yf/Screenshot%20from%202014-11-03%2021%3A56%3A46.png](https://www.dropbox.com/s/keiruzei2srr7yf/Screenshot%20from%202014-11-03%2021%3A56%3A46.png)



THere should be 2 partitions and there are 3: I can't make sense of the middle one...

And by the way, here is the output of the command 

```
sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C
```

suggested by Oldfred:

```
far@T430-Ubuntu1404:~$ sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
512 bytes (512 B) copied*
000001b0  00 00 00 00 00 00 00 00  d9 cb e9 85 00 00 00 00  |................|
000001c0  01 00 ee fe ff ff 01 00  00 00 2f 60 38 3a 00 00  |........../`8:..|
, 2.21539 s, 0.2 kB/s
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

I think the partiion table of the disk was GPT.

Hope this will help...

---

### Post by LostFarmer on 2014-11-04
```
000001c0  01 00 [COLOR=#006400]*ee*[/COLOR] fe ff ff 01 00  00 00 **2f 60 38 3a** 00 00 
```  That does show a [COLOR=#006400]*protective MBR*[/COLOR] , required for EFI partitioning with a **sector count of 500g**.  That is all correct.

I must have miss looked at your first posting of the 'testdisk' dropbox link, was thinking it looked same as the parted output. 

When you ran 'testdisk' about the 4th window one can make a selection for EFI/GPT and other types of partitions, did you select EFI/GPT ?  If not you MUST or it likely make a MBR partioning with EFI and make a mess (do not know for sure).

The output looks good, the middle partition you would disregard.  The other 2 just hi-light one at a time and use the left/right arrow keys to  place a **P **rimary at the beginning of each partition.
it will look something like below. (mine)
```
 **P** MS Data                145467392  252164095  106696704 [other storage]
```
 Then select write ,OK,Quite.  

There still might be a problem or 'testdisk' (I think) would let you list the files on the linux partition.

I think the dd command you used was fine, but i am not great at linux commands.  Do know it did NOT write to /dev/sdb or the protected partition info would have the wrong partition size, something else happened.

before trying to fix with 'testdisk' would like to see output of ```
sudo dd if=/dev/sdb bs=512 count=2 skip=1 | hexdump -C

``` that will read the current entries of the GPT partition table , first 4 entries.

Only took me 4 hrs to write the above.

---

### Post by oldfred on 2014-11-05
Only additional question is was drive gpt before copying the Android data?
LostFarmer shows that MBR is showing 500GB protective MBR so it would seem that is from before the dd copy?

Do you have a backup gpt partition table at end of drive?

I might use fixparts to view partitions, but not write with the w so it does not update unless sure it is correct.
       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by far on 2014-11-05
Thanks LostFarmer, it's nice to feel I'm not alone and you're still around to help!

Yes, I always used EFI/GPT in testDisk.

Before I write a partition table with TestDisk as you suggested, could you  check the output of  your command?

```
far@T430-Ubuntu1404:~$ sudo dd if=/dev/sdb bs=512 count=2 skip=1 | hexdump -C
00000000  45 46 49 20 50 41 52 54  00 00 01 00 5c 00 00 00  |EFI PART....\...|
00000010  f5 f7 f2 76 00 00 00 00  01 00 00 00 00 00 00 00  |...v............|
00000020  2f 60 38 3a 00 00 00 00  22 00 00 00 00 00 00 00  |/`8:....".......|
00000030  de 9f d5 01 00 00 00 00  41 4e 44 52 4f 49 44 20  |........ANDROID |
00000040  4d 4d 43 20 44 49 53 4b  02 00 00 00 00 00 00 00  |MMC DISK........|
00000050  80 00 00 00 80 00 00 00  5d a1 66 dd 00 00 00 00  |........].f.....|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200  a2 a0 d0 eb e5 b9 33 44  87 c0 68 b6 b7 26 99 c7  |......3D..h..&..|
00000210  41 4e 44 52 4f 49 44 20  42 4f 54 41 30 00 00 00  |ANDROID BOTA0...|
00000220  00 20 00 00 00 00 00 00  ff 3f 00 00 00 00 00 00  |. .......?......|
00000230  00 00 00 00 00 00 00 00  42 00 4f 00 54 00 41 00  |........B.O.T.A.|
00000240  30 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |0...............|
00000250  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000280  a2 a0 d0 eb e5 b9 33 44  87 c0 68 b6 b7 26 99 c7  |......3D..h..&..|
00000290  41 4e 44 52 4f 49 44 20  42 4f 54 41 31 00 00 00  |ANDROID BOTA1...|
000002a0  00 40 00 00 00 00 00 00  ff 5f 00 00 00 00 00 00  |.@......._......|
000002b0  00 00 00 00 00 00 00 00  42 00 4f 00 54 00 41 00  |........B.O.T.A.|
000002c0  31 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |1...............|
000002d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000300  a2 a0 d0 eb e5 b9 33 44  87 c0 68 b6 b7 26 99 c7  |......3D..h..&..|
00000310  41 4e 44 52 4f 49 44 20  45 46 53 00 00 00 00 00  |ANDROID EFS.....|
00000320  00 60 00 00 00 00 00 00  ff ff 00 00 00 00 00 00  |.`..............|
00000330  00 00 00 00 00 00 00 00  45 00 46 00 53 00 00 00  |........E.F.S...|
00000340  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000380  a2 a0 d0 eb e5 b9 33 44  87 c0 68 b6 b7 26 99 c7  |......3D..h..&..|
00000390  41 4e 44 52 4f 49 44 20  50 41 52 41 4d 00 00 00  |ANDROID PARAM...|
000003a0  00 00 01 00 00 00 00 00  ff 3f 01 00 00 00 00 00  |.........?......|
000003b0  00 00 00 00 00 00 00 00  50 00 41 00 52 00 41 00  |........P.A.R.A.|
000003c0  4d 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |M...............|
000003d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
2+0 records in
2+0 records out
1024 bytes (1.0 kB) copied, 0.000848454 s, 1.2 MB/s
00000400

```

Does that tell you anything?

---

### Post by far on 2014-11-05
Hi OldFred

fixparts shows the following:

```
far@T430-Ubuntu1404:~$ sudo fixparts /dev/sdb
[sudo] password for far: 
FixParts 0.8.8

Loading MBR data from /dev/sdb

This disk appears to be a GPT disk. Use GNU Parted or GPT fdisk on it!
Exiting!

```

It now says the disk has a GPT disk !! I thought it was MBR !! If I use  gdisk instead (which it is claimed should be used with GPT table) I have:

```

far@T430-Ubuntu1404:~$ sudo gdisk /dev/sdb
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

```

---

### Post by oldfred on 2014-11-05
Does this show the same Android partitions?
Does Android use gpt and your dd converted it?

 sudo gdisk -l /dev/sda

And before using testdisk you must be sure which it is or it may restore incorrectly & in effect corrupt it more.

---

### Post by dragonfly41 on 2014-11-05
I use MBR not GPT so I can't comment much further

but read more here on recovering original MBR ..

[http://askubuntu.com/questions/239967/accidentally-partitioned-drive-from-mbr-to-guid](http://askubuntu.com/questions/239967/accidentally-partitioned-drive-from-mbr-to-guid)

note the usual advice is to _clone_ your disk onto another disk before trying recovery in 
case of a disaster as you dig yourself deeper and deeper into a hole.

---

### Post by LostFarmer on 2014-11-05
You do have a GPT partitioned disk, for GPT it is required to have a protective MBR entire.  

You main GPT partition data is wrong. Both the GPT header (offset ***00 to***60) and the partition info starting at offset ***200. There would be several more sectors of partition info.
There is a backup copy of the GPT header and partition info at the end of disk.  The last sector contains the GPT header with the partition info starts at 32 sectors before the last. (on mine anyway)

If you want to look at that data; sudo fdisk -l (small L) to get the last sector.  Must remember that fdisk and dd counts the beginning sector different. fdisk first sector =1, dd first sector =0 

sudo dd if=/dev/sda bs=512 count=1 skip=(last sector # -1 from fdisk) | hexdump -C  will display backup GPT header

sudo dd if=/dev/sda bs=512 count=1 skip=(last sector # -33 from fdisk) | hexdump -C  will display backup GPT partition info.  with 'count=1 will only display the first 4 partitions, your case it should only have 2.

If the backup looks like it is good , you could use 'gdisk' with options from the (r) recovery & transformation menu 'b and e' . The ? will display the menu and options.  [http://rodsbooks.com/gdisk/repairing.html](http://rodsbooks.com/gdisk/repairing.html)


I am sure one can run gdisk with the options to see what the backup has and if it is not correct just press option (q) to quite, if it looks good press (w) to Write the backup to primary GPT. instead of the use of 'dd'.

I do know some of my instructions are not very good.


  Would say that what ever program you used to check the  Android image wrote the GPT to the Data hdd for some reason.  What program's' did you use ?

---

### Post by far on 2014-11-06
I have to admit I am a bit lost and confused...My knowledge of patition tables is very limited :( You guys seem to be real experts and it is sometimes difficult to understand...

So I backed up the partion table and made a disk image of the hard disk. Then I tried writing a new partition (recovered) table using TestDisk following the suggestion of OldFarmer yesterday, however this did not allow me to mount any of the 2 partitions. Finally, I ran  "deep search" in TestDisk (as suggested by DragonFly41 earlier) and this is what I get as output: 

[https://www.dropbox.com/s/qya9gb1yt11q5vs/testdisk%20after%20deep%20search.png?dl=0](https://www.dropbox.com/s/qya9gb1yt11q5vs/testdisk%20after%20deep%20search.png?dl=0)

and the detail: of the deep search: 

[https://www.dropbox.com/s/zc86z7zkh343uyj/testdisk%20after%20deepsearch%20details.png?dl=0](https://www.dropbox.com/s/zc86z7zkh343uyj/testdisk%20after%20deepsearch%20details.png?dl=0)

.. a very funny result !!!

TestDisk sitll tells me "No file found, filesystem may be damaged." when trying to view the files on the EXT4 partition (I did recover the files on the other partition by the way).

With the information I provided, does someone have an idea if it is indeed a partition table problem, or is it rather the data on the EXT4 partition that is corrupt? In the latter case, is there a way to format the faulty partition and recover the files (with foremost for example)? 


PS: @ I used parted and  TestDisk to check my Android disk image. If I understand well, I should look for that backup GPT table at the end on the disk : I didn't find a way to view it with gdisk, It seems I can only tell it to "use main GPT header (rebuilding backup)". I will try that later, in the mean time, here is the output of  "sudo gdisk -l /dev/sdb" if it can help:

```
far@T430-Ubuntu1404:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2014ACD0-DB93-E246-99E3-E5F40C0EA9A2
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2029 sectors (1014.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       512002047   244.1 GiB   0700  
   2       512002048       976773119   221.6 GiB   0700 
```

---

### Post by dragonfly41 on 2014-11-06
> 
and the detail: of the deep search: 

[https://www.dropbox.com/s/zc86z7zkh3...tails.png?dl=0]("https://www.dropbox.com/s/zc86z7zkh343uyj/testdisk%20after%20deepsearch%20details.png?dl=0")

.. a very funny result !!!


The testdisk "deep search" output says ...

Structure: Ok. Use Up/Down Arrow keys to select partition.

Follow that instruction as given for all the partitions named [SharedData_Ext4].

Then for each partition selected by running through the list use the Key "P" to list files which can be recovered.

Some of the partitions will not be valid but you will need to skip through all of them (from my memory) to locate those with files for recovery.

[later edit]

Here are more details .. step by step guide ...

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

and you have reached this step ..

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search)

---

### Post by LostFarmer on 2014-11-06
Sometime between your post #12 and now the partition table has been rewritten, and the program should have updated the backup.

Can you now mount and read the NTFS partition correctly ?  The linux partition ?

What errors if any do you get ?

> I didn't find a way to view it with gdisk, It seems I can only tell it to "use main GPT header (rebuilding backup)  Gdisk will not view the raw data,  you would select option (b) and (e), then press (p), if the printed partition table looks good would then (w)rite it to disk or (q)uite to abort.

---

### Post by oldfred on 2014-11-06
Since your Android image was 12GB, the first 12GB of the ext4 partition was overwritten. So that data is totally gone and probably so much of partition structure that only photorec may be able to recover some of you data in the ext4 partition.

I have used photorec.  A long slow process and it only recovers by file type or extension. You can auto rename photos & mp3 as they have internal data. I had to look at each text file to see which was which. And I had saved my text files many times. It recovered all the deleted copies. I did have a somewhat older backup and had to compare each backup text file to recovered text file and see if I could tell if I added or deleted data. 

         [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)

---

