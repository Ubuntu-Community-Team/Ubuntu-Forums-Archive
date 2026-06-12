---
title: "Can't boot. Lucid Lynx, grub-rescue and rearranged partitions"
date: 2013-09-03
forum: General Help
---

### Post by supershin on 2013-09-03
Hi,

I have Dual boot system with Lucid Lynx and few other ext4 partitions installed on a computer with a separate home partition that they all share. I accidentally enter Windows Recovery, couldn't quit and had to hard reboot(it froze). Grub-rescue came up on booting.

I searched around and restored grub2 by re-installing from a Lucid Lynx live cd. However I get Linux disk drive for /home is not yet ready or not present. I searched some more, in Gparted home partition is unallocated, so I ran:

sudo fdisk -l  (not on affected pc so can't copy-paste)
/dev/sda1 hidden w95 fat32 (lba)  [win recovery]
/dev/sda2 ntfs/exfat    [think win7]
/dev/sda3 w95 ext'd(lba) [logical partition]
/dev/sda5 ntfs/exfat  [d drive for win7]
/dev/sda6 linux [lucid lynx]
/dev/sda7 linux [mythbuntu]
/dev/sda8 swap

One linux os is missing. 


cat /etc/fstab:
/ was on /dev/sda9 during installation uuid=d3bc          ext4     errors=remount-ro 0 1
/home was on /dev/sda8 during installation uuid=9106   ext4     defaults               0 2 
swap was on /dev/sda10 during installation uuid=91ec   swap    sw                       0 0

So it looks like somehow swap is where my home should be.

sudo blkid:
sda1 label="recovery" uuid= ac5d   vfat
sda2 os                   uuid=c360    ntfs
sda5 d drive             uuid=b8cc    ntfs
sda6 lucid                uuid=0ab7    ext4 
sda7 uuid=d3bc    ext4
sda8 uuid=91ec    swap


I just want to get back my home partition without destroying the windows install and d drive. Can someone help me please?

---

### Post by oldfred on 2013-09-03
I am surprised it shows some Linux partitions. Generally the vendor recovery seems to rewrite partition table first and Linux is lost.
But many have fully restored it with testdisk. Best if you know start and size of partition as testdisk may show many options if drive was resized a lot. 
Testdisk is in the Ubuntu repository.

       [URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL]
 repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[URL="http://www.psychocats.net/ubuntucat/recoverdeletedfiles/"]http://www.psychocats.net/ubuntucat/recoverdeletedfiles/

      [/URL]
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

    [URL="http://www.psychocats.net/ubuntucat/recoverdeletedfiles/"]
[/URL]

[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

### Post by supershin on 2013-09-04
Can I quit testdisk after successfully running one of the commands without serious consequences(lose all data)? 

In other words say I need to stop before doing a deeper search, can I quit and redo the process another time? Just trying to figure out how much time has to be allocated to the recovery, its a 500GB hard drive so don't want to start and can't finish properly.

I have SystemRescueCD with testdisk on it or would you recommend Ubuntu LiveCD with testdisk?

---

### Post by oldfred on 2013-09-04
As long as version of testdisk is current or nearly so either should work. Just do not use old copies.

I think the deep search is more to look for files. What is it showing for partitions?

---

### Post by supershin on 2013-09-05
Teskdisk shows:

```
500GB / 465GiB [Hard drive is indeed a 500GB]
Current partition structure:

Partition                    Start              End                Size in sectors
1 P hid. Fat32 LBA          0  32 33      1911  254 63      30714232     [RECOVERY] 
2 * HPFS - NTFS       1912  0    1     17111 254 63      355299000   [OS]
3 E extended LBA     17112  0 62      60801 47 46        701866731               
5 L HPFS - NTFS      17112  1 1        40056  254 63     368611362  [D drive]
   X extended          40057  0  1       42384 91 11        37388999              
6 L Linux                 40057 11 19     42384 91 11        37388288    [Lucid Lynx]
   X extended          42384 91 12     44472 66 10        33542144
7 L Linux                42384 123 44    44472 66 10         33540096    [Myhtbuntu]
  X extended           60009  35 59    60801  47 46        12724224
8 L Linux swap         60009  68 28    60801 47 46         12722176

```

I don't recall having so many extended partitions. Thinking about it now, I believe I deleted that 'missing' linux os and allocated the space to home some months ago. Confirmed it below with it being marked D. So now 

Partitions I had: Recovery, OS, D drive, Home(ext4), Lucid Lynx, Mythbuntu, Swap.


```
Testdisk quick analyse:
* Fat32 LBA               0  32 33      1911  254 63        30714232     [RECOVERY]          15 GB/14 Gib    
P HPFS - NTFS      1912  0    1      17111 254 63      244188000     [OS]                  125 GB/ 116 GiB  
L HPFS - NTFS      17112  1 1        40056  254 63     368611362    [D drive]             188 GB/ 175 GiB  
L Linux              40057  1  1      54079 254 63       225279432         ReiserFS 3.6 with standard journal 115 GB/ 107 GiB   (My home partition judging from size ) 
D Linux              56630  1  1      6009 254 63         54299637        [centos]- the 'missing' os I deleted.  ext3 27 GB/ 25 GiB
D Linux swap     60009  68 28    60801 254 63        12735234          swap2 version 1, 6520 MB / 6218 MiB


```
Pressing P on my home partition gives: "Can't open filesystem. It seems damaged." I can press p and get a file listing for the cent-os which i deleted.



```
After pressing enter to continue:

Partition                    Start              End                Size in sectors
1 * Fat32 LBA          0  32 33         1911  254 63            30714232     [RECOVERY] 
2 P HPFS - NTFS      1912  0    1    17111 254 63           244188000    [OS]
3 E extended LBA     17112  0 1      54079 254 63          593890920     
5 L HPFS - NTFS      17112  1 1      40056  254 63        368611362     [D drive]
6 L Linux                40057 1 1        54079 254 63         225279432  
```


What are the next steps?  Really appreciate the assistance.

---

### Post by oldfred on 2013-09-05
Were you using a ReiserFS? That may be part of the complication? Different tools may be required and some file systems do not have all the tools.

Testdisk finds all your previous versions. So you often have to figure out which is the correct combination of partitions that does not overlap. All the logicals must be in the extended, so other extended partitions would not be valid. Your 3 looks like the entire rest of the partition so that would probably be the correct extended partition.

---

### Post by supershin on 2013-09-05
I probably experimented with it but I don't think I used it for my home partition. I guess the next step is to run deeper search. Will post the results once I get a chance to run it.

---

### Post by supershin on 2013-09-07
Edit: scroll right to see which ones I verified my files on.
After running deeper search:

```

1  FAT32 LBA          0  32  33      1911   254    63     30714232   RECOVERY	15GB / 14 GiB	
2  FAT32 LBA          0  32  33	     1912    91	27	30719992	NO NAME	FAT found using backup sector! 15GB/14GiB	
3  HPFS &#8211; NTFS  1912	0    1	   17111	254	63	244188000	OS	125 GB/ 116 GiB	 [COLOR="#FF0000"]**can view files**
[/COLOR]


4  FAT32 LBA       17112   0	1	18386  254	 52	20482864	NO NAME	FAT found using backup sector! 10487 MB/10001MiB	
5  HPFS &#8211; NTFS	17112   1	1	40056  254	 54	368611353	DATA	188 GB / 175 GB	no partition found - 
6  HPFS &#8211; NTFS	17112   1	1	  6800  254	 63	701863722	DATA	NTFS found using backup sector! 359GB/ 334GiB [COLOR="#FF0000"]**can view my files**[/COLOR]


7  HPFS &#8211; NTFS	17112   1	10	40056  254	 63	368611353		NTFS found using backup sector! 188GB/175GiB	can't open filesystem, it seems damaged
8  Linux              40057   1    1	54079  253 	 54	225279360		ReiserFS 3.6 with standard journal 115GB / 107GiB	can't open filesystem, it seems damaged
9  Linux           	40057  11  19	42384   91    3	37388280	LUCID LYNX	ext4 large file sparse superblock 19GB / 17GiB	old root partition


10  Linux 	        42163   44  58	44490  124  42	37388280	LUCID LYNX	ext4 large file sparse superblock recover 19GB / 17GiB	no file found, filesystem may be damaged
11  Linux            42384	  123 	44	44472  66	10	33540096		ext4 large file sparse superblock 17GB / 15GiB	[COLOR="#FF0000"]**lucid root partition**[/COLOR]


12  Linux  	        43192  151	32	45280  93	61	33540096		ext4 large file sparse superblock 17GB / 15GiB	no file found, filesystem may be damaged
13  Linux            43200	    61 62	45288   4	28	33540096		ext4 large file sparse superblock 17GB / 15GiB	no file found, filesystem may be damaged
14  Linux            44472	  98	43 	56629  215	34	195309568	 HOME  ext4 large file sparse superblock 99GB / 93GiB	[COLOR="#FF0000"]**can view my files in home partition**[/COLOR]


15  Linux 	       56630	  1     1	60009   35	55	54285832	CENT-OS	ext3 large file sparse superblock 27GB / 25GiB	
16  Linux swap     6009	 68   28	60801   47	30	12722160		swap2 version 1, 6513 MB/ 6211 MiB	
17  Linux swap    60624	  1	 1	60800  254	45	2843424		swap2 version 1, 1455 MB/ 1388 MiB	
18  Linux swap    60624	 29   14	60801   47	30	2844656		swap2 version 1, 1456 MB/ 1388 MiB	

```


On completing before results got:
```

	Following partitions can't be recovered:								
Partition	start				end			size in sectors	
Linux 	50494	131	6		62651	247	60	195309568	HOME
Linux 	50497	48	48		62654	165	39	195309568	HOME
Linux 	50497	146	18		62655	8	9	195309568	HOME
Linux 	50508	234	31		62666	96	22	195309568	HOME
Linux 	50509	77	1		62666	193	55	195309568	HOME
	EXT4 large file superblock Recover, 99GB / 93 GiB								

```


```

	found during scan but not in final results									
4	HPFS &#8211; NTFS	1912	0	1	17111	254	63	244188000	OS
14	Linux 	50494	131	6		62651	247	60	195309569	HOME
15	Linux 	50497	48	48		62654	165	39	195309570	HOME
16	Linux 	50497	146	18		62655	8	9	195309571	HOME
17	Linux 	50508	234	31		62666	96	22	195309572	HOME
18	Linux 	50509	77	1		62666	193	55	195309573	HOME

```


Thanks for your patience. Hope this helps, what's next?

---

### Post by oldfred on 2013-09-07
I do not think you need the files unless you do not have a backup and want to copy them.

But you should get a screen like this and the empty space should show as a D for deleted partition. Just undelete that. It is logical since it was in the extended partition.
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by supershin on 2013-09-08
Hi, I'm trying to change the partition to have it like this:

P FAT32 LBA	0	32	33		1911	254	63	                     30714232	  RECOVERY	15GB / 14 GiB
* HPFS &#8211; NTFS	1912	0	1		17111	254	63	        244188000	                   OS	125 GB/ 116 GiB

*HPFS &#8211; NTFS	17112	1	1		60800	254	63	701863722	D drive	NTFS found using backup sector! 359GB/ 334GiB realized its wrong one*
L HPFS &#8211; NTFS	17112	1	1		40056	254	54	368611353	D drive	188 GB / 175 GB
 																																		
L Linux 	                42384	123	44		44472	66	10	              33540096		            ext4 large file sparse superblock 17GB / 15GiB
L Linux          	44472	98	43		56629	215	34	                195309568	HOME	       ext4 large file sparse superblock 99GB / 93GiB
L Linux 	                56630	1	1		60009	35	55	                  54285832	CENT-OS	ext3 large file sparse superblock 27GB / 25GiB
 
Edit:
The only primary partitions I had was the recovery and OS and everything else was in an extended partition. 

I can't select an E for any partition. Are the flags ok, I get structure ok, but not sure if Recovery or OS should be *.

Can you help me?

---

### Post by oldfred on 2013-09-08
If you cannot recover since structure not ok,  then about all you can do is copy files from the deeper search. 
Not sure if anything else would work.

---

### Post by supershin on 2013-09-08
I got the structure to be ok and wrote the partition table to disk. Haven't tried booting as yet. Is there another procedure to be done before trying to boot?

I had grub2 on my Lucid Lynx root partition. Should I try booting and if I can't re-install grub via LiveCD?

---

### Post by supershin on 2013-09-08
AAAAAAHHHHHH!!!!! I decided to boot system rescue cd and check in gparted and now it says the entire drive is unallocated. The partition structure had said it was ok! Help me please.

---

### Post by oldfred on 2013-09-08
If NTFS or even ext4 partitions need chkdsk or fsck then gparted will have issues.

What does this show?
sudo parted -l
or 
sudo fdisk -lu

---

### Post by Bucky Ball on 2013-09-09
I can't see that anyone has mentioned that Lucid (10.04 LTS) has not been supported since April this year and running it, especially if connected to the net, is a bad idea for many reasons, not least of all that it hasn't received security updates since April and is therefore a vulnerable system if online.

Good luck. ;)

---

### Post by supershin on 2013-09-09
I loaded a ubuntu livecd and I can see my files. I didn't run a check disk or fsck. Should I run it and how do I run check disk for windows from a linux livecd? Or do I try booting windows?

```

parted -l
Error: Can't have a partition outside the disk!
Disk /dev/sda: 500GB
sector size: 512B/512B
partition table: unknown
disk flags: 

Warning: Unable to open /dev/sr0 read-write (read only system)
Error: /dev0/sr0: unrecognised disk label
This is my DVD drive I'm running the livecd from.



fdisk -lu

Disk /dev/sda: 500.1GB 500107862016 bytes, 976773168 sectors
units = sectors of 1 *512 = 512 bytes
Sector size: 512 bytes/512 bytes
IO size: 512 bytes/512 bytes

device	boot 	start	                      end	             blocks	  id	system
/dev//sda1		2048	                  30716279	          15357116	  c	W95 FAT32 (LBA)
/dev//sda2	  *	30716280	          274904279	122094000	  7	HPFS/NTFS/exFAT
/dev//sda3		274904280           976784129	         350393325	  f	W95 Ext'd (LBA)
/dev//sda5		274904343	          64351595	         184305676  7	HPFS/NTFS/exFAT
/dev//sda6		643516416	          680904695	18694140	 83	Linux
/dev//sda7		680906752	         714446847	       16770048	 83	Linux
/dev//sda8		714448896	          909758463	97654784	 83	Linux


```

---

### Post by oldfred on 2013-09-09
There is a bug in testdisk. It uses the old CHS - cylinders, heads, sectors. But in recalculating the end of the drive it sometimes rounds up and makes extended partition too large.

This will rewrite partition table correctly.

 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by supershin on 2013-09-09
What command am I looking to run with fixparts after running "fixparts /dev/sda" ?

---

### Post by oldfred on 2013-09-09
If you read the link on fixparts it gives all the commands. It really should just be p to review if it adjusted correctly and w to write the corrections.

---

### Post by supershin on 2013-09-09
Ah...I see. So Fixparts will adjust the extended partition when it writes the partition table to disk.

Reference link, showing Fixparts usage: [http://ubuntuforums.org/showthread.php?t=1728998](http://ubuntuforums.org/showthread.php?t=1728998)

---

### Post by supershin on 2013-09-09
```
After fixparts, fdisk output:
device                 start                   end            blocks       id       system
/dev//sda1		2048	              30716279	  15357116	    c	  W95 FAT32 (LBA)
/dev//sda2	*	30716280	      274904279	  122094000   7	  HPFS/NTFS/exFAT
**/dev//sda3		274904342	      909758463	  317427061   f	  W95 Ext'd (LBA)**
/dev//sda5		274904343	     643515695	  184305676   7	  HPFS/NTFS/exFAT
/dev//sda6		643516416	      680904695	  18694140	   83	   Linux
/dev//sda7		680906752	      714446847	  16770048	   83	   Linux
/dev//sda8		714448896	     909758463	  97654784	   83	   Linux

```

The extended partition is now corrected and I can see the structure in gparted. 

My OS partition has a warning on it: 
Unable to read the contents of this file system!
Because of this some operations may be unavailable

The cause might be a missing software package. The following list of software packages is required for ntfs support: ntfsprogs / ntfs-3g.


I assume that is how I'm running from systemrescue livecd, though not sure. What are the next steps? Running fsck or checkdisk?

---

### Post by oldfred on 2013-09-09
The not sure about systemrescue. But the old NTFS drivers and ntfsprogs drivers used to be two different things. They merged a couple of years ago and now are just ntfs-3g. But with some versions installing ntfsprogs uninstalls ntfs-3g. 
Would be much better if you upgrade to a new current version as then we have a better idea what is the real issue. Old drivers have old issues which now we have forgotten what those were.
If system is old then Lubuntu may be a better newer version. But my systems are from 2006 and run full Ubuntu but not Unity as I use gnome-panel to have the top & bottom panels not side panel with Unity.

You cannot repair NTFS from Linux anyway. You need a Windows repairCD or flash drive to run chkdsk. If Linux ext family needs filechecks then you run e2fsck from Ubuntu liveDVD or flash.

---

### Post by supershin on 2013-09-10
So to confirm I should run e2fsck from livecd to fix the linux partitions and then try to boot windows(have no repaircd) and run a checkdisk?

---

### Post by oldfred on 2013-09-10
Yes, some third party Windows repair tools may help with Windows issues. But better to have your own Windows repairCd you maike from your install.

 Third party chkdsk tools
Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)
May be able to run chkdsk from Hiren's boot CD. (mini xp.)
Hiren's Boot CD, and do a chkdsk on the XP

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

---

### Post by supershin on 2013-09-10
Thanks. I ran the e2fsck on the linux partitions and it completed successfully. On restart I got my grub menu and booted into windows and got to launch startup repair, from there I ran chkdsk in the command prompt. 

I just successfully started windows and got back to my desktop! Disk Management shows the partitions Extended partition contains the D drive partition only and the linux are primary. Which is kinda strange because fdisk showed the extended contained them as well. Will try booting linux.

Gparted shows the linux in the extended partition and fdisk results are the same as previous. I assume that is how it was given that Windows can't read ext. 

I can access my files in windows, d drive, linux and home and everything seems to be in good working order. Will run it for two days before marking the topic as solved.  In most posts I came across, it usually ends with the thread owner giving up, reformatting over the drive or some mishap occurring resulting in data loss. Glad this turned out extremely well.

Thank you very much, oldfred. I truly appreciate your wisdom and help.

---

### Post by oldfred on 2013-09-10
Please post this just to have documentation of sectors of your current partitions.

sudo fdisk -lu

---

### Post by supershin on 2013-09-12
OK will do later this week, but the extended partition didn't go to the end of the disk. I ended up with a unallocated partition at the end of the disk. However since my OSes and files are accessible and so far everything works, I'll just make it a primary partition and use it like that.

---

### Post by Bucky Ball on 2013-09-12
> **supershin said:**
> ... I'll just make it a primary partition and use it like that.

Jumping in but just a note on that. Depending on the setup, if you have four partitions on the one physical drive already, creating another primary won't be possible (and I mean if you have four partitions of any type already, a combination of primaries and extendeds). Better to expand the partition butting on to the free space into it. ;)

Just thought I'd mention it ...

---

### Post by supershin on 2013-09-15
Had tried expanding the extended partition in gparted but it won't. Don't know why. Still have it unallocated though. It'll be the 3rd primary if I do make it such so no worries there thanks :o

---

### Post by supershin on 2013-09-15
sudo fdisk -lu after the fixparts. 
```


/dev//sda1		2048	         30716279	15357116	c	W95 FAT32 (LBA)
/dev//sda2	*	30716280	274904279	122094000	7	HPFS/NTFS/exFAT
/dev//sda3		274904342	909758463	317427061	f	W95 Ext'd (LBA)
/dev//sda5		274904343	643515695	184305676	7	HPFS/NTFS/exFAT
/dev//sda6		643516416	680904695	18694140	83	Linux
/dev//sda7		680906752	714446847	16770048	83	Linux
/dev//sda8		714448896	909758463	97654784	83	Linux
```

There's an unallocated space after the extended partition, which I plan on making primary, since extended can't be resized to fill the space.

---

### Post by oldfred on 2013-09-15
Sometimes you cannot work on the extended or any partition in the extended from a liveCD since liveCD often mount swap that is in extended.  You have to click on swap and right click swap-off. So the extended is totally unmounted (no little key icons).

---

### Post by Bucky Ball on 2013-09-15
Yes, work from a Live CD to manipulate partitions is best (and the only way to resize the OS partition /). Right click and make sure all partitions are unmounted then fire away. Shouldn't be any issues.

---

### Post by supershin on 2013-10-06
Thank you very much oldfred :popcorn:. Thanks bucky, I'm marking this as solved since I successfully recovered =D>.

---

