---
title: "I/O error ssd"
date: 2012-12-18
forum: General Help
---

### Post by then_dude on 2012-12-18
Hello,  my pc hangs two times today...  when i switched to another console, ctrl alt F3; I could not shut it down by terminal... I had to reboot hard.   But the terminal showed that there were I/O errors on the sda; which is my SDD boot disk.   I wonder what can be the problem for this?   i will run an update for the firmware, but i wonder if this would solve the problem. can anybody helps me out   thanks

---

### Post by d4rk0wl on 2012-12-18
I have run into similar problems while I was using an SSD boot disk. Turns out my problems were hardware related. What type of SSD do you have?

Try this:
Boot off of the Ubuntu like CD and select "Try Ubuntu" option

Open a terminal and find the disk you are having problems with, just to double check if you are running multiple drives
```
sudo fdisk -l
```

Now once you have located the problem disk (sda) run
```
sudo fsck -y /dev/sda
```

fsck will scan the drive for errors and -y will make it non-interactive.

I know it may sound odd scanning an SSD for block errors, but I went through the same headaches and this is what helped me in my problems. :sad:

---

### Post by pqwoerituytrueiwoq on 2012-12-19
it is probably failing
backup everything of value

---

### Post by then_dude on 2012-12-19
thanks guys,


[LIST=1]
[*]i backuped everything
[*]i have already updated the firmware
[*]i have started ubuntu from live cd and run the commands. But i have an ssd that has multiple partitions,  one primair ext4, then a swap(ext4) and another ext4 in a logical partition.  i could not run fsck /dev/sda, but i could run in it  /dev/sda1 ..
[/LIST]
this is the ouput 


**ubuntu@ubuntu:~$ sudo fdisk -l**

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005fb98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    94699519    47348736   83  Linux
/dev/sda2        94701566   125044735    15171585    5  Extended
/dev/sda5       122220544   125044735     1412096   82  Linux swap / Solaris
/dev/sda6        94701568   122218495    13758464   83  Linux

Partition table entries are not in disk order


**ubuntu@ubuntu:~$ sudo fsck -y  /dev/sda1**
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
/dev/sda1: clean, 349504/2959712 files, 10539973/11837184 blocks



after a force i got


**ubuntu@ubuntu:~$ sudo fsck  -y  /dev/sda1 -f**
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 349504/2959712 files (0.4% non-contiguous), 10539973/11837184 blocks



i guess the ssd is still ok ? it has 258 days of running... 
the disk is a crucial m4 64gb 



thanks

---

### Post by then_dude on 2012-12-22
anybody ?   today the pc hangs, could not even get into other consoles, so tapping ctrl-alt-f(3-4-5-6) didn't do a thing....  thanks

---

### Post by d4rk0wl on 2012-12-23
Hmm, that is odd. 

Why do you have so many partitions on the drive? Since everything is backed up maybe you should attempt a multi-pass re-formatting of the drive. 

This sounds a lot like the problems I was having, I ended up just ditching the SSD and buying a new mechanical drive.

Sorry for the late reply, I have not been here.

Regards,
d4rk0wl

---

### Post by then_dude on 2012-12-24
indeed that's odd...  1)what is the most intensive program to run a checkdisk ?   2)i have multiple partitions because i'm running multiple os on startup... maybe that's not the best choice.   3)what kind of harddisk did you buy ? an enterprise edition ?   thanks

---

### Post by d4rk0wl on 2012-12-25
The reasons you may be experiencing an issue is because you have multiple os's on the SSD. I know that windows does not like to play happy with Linux. 

I had an OTZ Petrol, but I ditched it for a Seagate 1TB drive. Was actually surprised on the performance of the TB compared to the SSD, it actually kept up really nice.

Since then I have gotten two more drive, (500GB each) One is dedicated to Kubuntu, the other to Windows 7 and the TB drive is my media drive so I can have all my tunes on both OS's 

regards,
d4rk0wl

---

### Post by then_dude on 2012-12-27
hello d4rk0wl   i do have multiple OS on the ssd, but they are all linux distro's,  i have updated the bios, and no freezig until so far.   the smart info of the ssd says everything is fine...  can anybody give me the name of a software that checks the ssd on error's, please refer me to the most powerfull software. (under ubuntu offcourse)  thanks a lot kind regards

---

### Post by oldfred on 2012-12-28
I have two copies of Ubuntu on my 64GB SSD. It is a house brand Microcenter SSD.

Do you have AHCI enabled in BIOS? You need that to have trim work.

I did not enable trim originally and run this which trimmed system.

       fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

### Post by then_dude on 2012-12-29
thanks oldfred

 i have tried to follow the example, 

but when i type "sudo hdparm --fibmap tempfile" at the console, 
i get this output. So my tempfile is not one big file but is spread out...   anybody help ? 

thanks
 sudo hdparm --fibmap tempfile

tempfile: underlying filesystem: blocksize 4096, begins at LBA 2048; assuming 512 byte sectors
 byte_offset  begin_LBA    end_LBA    sectors
           0   30955520   30956543       1024
      524288   30960640   30961663       1024
     1048576   31066112   31072255       6144
     4194304   31049728   31057919       8192
     8388608   32245760   32278527      32768
    25165824   49956864   49989631      32768
    41943040   50022400   50038783      16384
    50331648   50055168   50059263       4096

---

### Post by oldfred on 2012-12-29
How big did you make the temp file?

It was supposed to be close to 4KB or one sector. 

If it is writing all over that is why it is slow and something is not configured correctly.

did you run the fstrim command?

---

### Post by dcstar on 2012-12-29
> **oldfred said:**
> 
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

TRIM misunderstanding seems to have now reached the "mess" stage.

The requirements and performance of TRIM vary wildly depending on the underlying SSD hardware - and because SSD hardware is changing so rapidly at this very moment what is written by people just a few months ago may not be valid - and may even be totally invalid and detrimental to newer hardware - so users just cannot depend at all on any of this old stuff that they read on the Internet.

Bottom-line is that some SSDs handle TRIM clean-up better than others, the more modern (and more expensive) SSDs seem to be far better than devices of just a few months ago and all these older "experiences" are basically invalid unless the exact same hardware is being referred to.

When SSDs evolve to the stage where existing data re-writes perform just as well as empty-block fresh writes then we can all leave this confusing era behind, until then just stick to the basics of only using TRIM enabled filesystems and let the SSD devices manage the best that they can with default setups.

---

### Post by then_dude on 2012-12-29
the file was 50Mb, that might be the problem. 

but when i read the last post... well then i all gets blurry for my eyes... 

i have put in the notion "discard" in the fstab file. should i leave it there  ?

thanks guys

---

### Post by oldfred on 2012-12-29
I still think you need AHCI in BIOS. 

       And you still need discard for trim and noatime to reduce writes. You can also use ext4 but turn journal off. I think that was about all I actually did. Some now say with the newer SSD, ext4 with journal should not really matter.

If using any newer version of gparted you should have alignment or first partition starts at sector 2048 and all partition starts are divisible by 8.

---

### Post by then_dude on 2012-12-30
thanks

 i have just found the option ahci in my bios, and it is enabled.

 the discard option i have already put in my fstab file. 

i have  typed in "sudo fdisk -l" to see where my partitions begin....


[LIST=1]
[*]the partitions begin not at a point which is /8, so how can i solve this problem.
[*]i can loose some partitions if necesairy
[*]i must still look up the notion noatime
[/LIST]




Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005fb98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5895    47348736   83  Linux
/dev/sda2            5895        7784    15171585    5  Extended
/dev/sda5            7608        7784     1412096   82  Linux swap / Solaris
/dev/sda6            5895        7608    13758464   83  Linux


thanks

---

### Post by Statia on 2012-12-30
> **oldfred said:**
> 
If using any newer version of gparted you should have alignment or first partition starts at sector 2048 and all partition starts are divisible by 8.

Don't newer versions of gparted take care of alignment automatically?
I think I read that somewhere.

(When I installed my system I didn't really understand alignment, didn't know how to calculate alignment for my system, so I just hoped gparted would indeed take care of it)

---

### Post by oldfred on 2012-12-30
My older drives are not aligned, but for them it does not matter. Gparted and Ubuntu installer then about 2 years ago changed to use 2048 as first sector (like Vista did). 

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?tit](http://ubuntuforums.org/showthread.php?tit)'s 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
 sudo parted /dev/sda unit s print

---

