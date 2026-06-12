---
title: "Cannot boot Ubuntu anymore"
date: 2013-12-17
forum: General Help
---

### Post by stanbrow on 2013-12-17
I have an Asus laptop that came with Windows 8 installed on it. I bought it about a year ago, and installed Ubuntu on it, in addition to Windows, and have been ahppily using it since then. A coupl;e of weeks agao, I did an apt-get dist-upgrade, and a bunch of stuff was updated. Shortly after that I changed the physical location of the machine, and neeeded to change the networking settings. I edited /etc/network/intrfaces, and tried to do a "service restart networking". I lost X, and could not get to a TTY, so I hard shut the machine down with the power switch.

After that, i could not boot into UBUNTU. I can boot imto Windows. I searched around and built a found boo-repair. I booted off of a 12.04 desktp 64 bit DVD taht I had a ran it. The results are on http:/paste.ubuntu.com/6575927/ but I still cannot boot into Ubuntu.

At this point, I have created a 13.10 64 bit desktop bootable USB stick. and have booted ino that. I think I have issues with my partion table. If I try to fsck my UBUNTU partion, while booted from the live USB stick, fack complains, and says something about a zeror length partiton.

When I run sfdik it says:
buntu@ubuntu:~/debug$ sudo sfdisk --no-reread -d /dev/sda > sfdisk.out

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

and it's output is:


# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        1, size=976773167, Id=ee
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0


I have atached a screenshot of gparted's view of things.

I have about a years worth of work into this machine at this point, and i would greatly apprecuate any advice as to how ro fix this problem, or at least get to the point that I can mount the UBUNTU partion and save my configurations and data.

BTW, I have tried booting in both UEFI mode, and what Asus calls CSM mode, if that helps. I beleive I originally installed in CSM mode.

---

### Post by dragonfly41 on 2013-12-17
The usual suggestion is to turn to testdisk as a recovery utility.  TestDisk is found in Ubuntu repo.

You have about one year's worth of data on your disk so you might consider it worthwhile
backing up this failed disk on a second fresh USB drive using your 13.10 64 bit desktop bootable USB stick.

Then using your bootable USB disk run testdisk on the cloned image.

With luck it might be something simpler like recovering superblock.

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

But if you have to scan your (unmounted) cloned drive to recover your legacy data remember that you need some 
additional disk space for your recovered files copied by testdisk.

Search this forum for testdisk usage advice.   And the testdisk forum.

[color=maroon]
[Later edit]
p.s. This info on your paste does suggest the theory of broken superblock ..

bad superblock on /dev/sda8

[/color]

---

### Post by stanbrow on 2013-12-17
Thnaks for the fast reply.

Let me provide a bit more data that I neglected to mention in my original post. 

If I could copy of the data, I would be happy re-installing. Howvwer, I cannot mount the Linux partion, and when I run fsck on it it fails saying that the filesystem is zero length.

I will look into testdisk, and the superblock repairs, as you sugested.

Thanks, again.

---

### Post by stanbrow on 2013-12-17
One more followup question. Looking at the superblock repair link you provided it seems to me that this would only pertain to the EXT4 Linux partiton, correct? 

I am thinking my partiton table may be corupt. and that is "one level up" from the suprerblock, correct?

What is the deal with the GNU partion table? This seems to be making certain tools that I have found that deal with partion tables unusable. Is this the normal way UBUNTU installs? Or did the boot-repair maybe change this?

---

### Post by dragonfly41 on 2013-12-17
Superblock repair refers only to linux partitions e.g. the main ubuntu partition /dev/sda8 (and the swap partition /dev/sda9)

Testdisk can repair partition table .. read here ..

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[http://geekyprojects.com/storage/how-to-repair-a-damaged-partition-table-or-mbr/](http://geekyprojects.com/storage/how-to-repair-a-damaged-partition-table-or-mbr/)

You don't explain where your important data is held .. in ubuntu (ext4) or in windows (ntfs) partitions?

Using your bootable USB can you navigate to any of the partitions? 

Perhaps look at clonezilla (running on your ext bootable USB) to clone your entire drive (or individual partitions) into another ext drive.

[http://www.clonezilla.org/downloads.php](http://www.clonezilla.org/downloads.php)

[http://www.clonezilla.org/downloads/download.php?branch=alternative#ubuntu-cpu-arch](http://www.clonezilla.org/downloads/download.php?branch=alternative#ubuntu-cpu-arch)
[URL="http://http://packages.ubuntu.com/search?keywords=linux-image-generic"]
http://packages.ubuntu.com/search?keywords=linux-image-generic[/URL]

---

### Post by stanbrow on 2013-12-17
Sorry, more clarifications.

I can boot into Windows, but not Ubuntu. The data is in the Ubuntu partiton. I cannot mount the UBUNTU partion from the live USB. I cannot fsck it either. 

So. I am thinking the clonzilla route cannot help me. I will try testdisk tonight.

IS the GPT the standard way of installing UBUNTU in this situation? I see on machines taht are 100% Linux, this does not seem to be done.

Given that I cannot fsck, or mount the partion (EXT4) does it make sense that this is a partion table issue?

---

### Post by stanbrow on 2013-12-17
Ok, here is an update. I di sudo fsck.ext4 -v /dev/sda8 and got the same message about a short read, and a zero length partition. So, I believe this points me to a bad partition table, and tot a superb lock issue.

Going to read up on test disk now.

---

### Post by spencer the great on 2013-12-17
Try booting your install disk, opening a terminal, and doing "grub-install /dev/sda" (or whatever device you installed grub on during your initial install) as root. This will install a GRUB bootloader to the hard-drive's MBR.
EDIT: Okay, this should probably be a last-resort thing, because perhaps it's just an error in the partition table.

---

### Post by oldfred on 2013-12-18
All new UEFI systems use gpt partitioning. 
I have an old BIOS system but all my new drives since 10.10 have been gpt partitioned and my working installs in my gpt drives. I still have one larger MBR drive but have hesitated to convert to gpt so far.

It still seems like a fsck issue. A simple fsck just checks to see if fsck needed. Better to run the full fsck.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda8 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda8
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda8

If partition table issue, try gdisk. It is in repository and is the fdisk for gpt partitioned drives.
sudo apt-get install gdisk
      
 sudo gdisk -l /dev/sda

      
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by stanbrow on 2013-12-24
I have been busy, and am just now geting back to this. Here are some obsevations.

It seems significant to me that gparted does not know the length of partiton 8. It does see that it is EXT4. Thiusis my Ubuntu partion.

I worked with testdisk fro a while, and thought ti was going to be the answer to my problem, but I woulnd up needing to do a full disk scan in it, and the resukts of that did not look useful to me.

So, Iam now woroing with disk. Here is what is shows for this partiton:

Command (? for help): i 
Partition number (1-9): 8
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: C96FB31A-A66E-47A1-8902-BB03E0A53FC7
First sector: 663824384 (at 316.5 GiB)
Last sector: 926679039 (at 441.9 GiB)
Partition size: 262854656 sectors (125.3 GiB)
Attribute flags: 0000000000000000
Partition name: ''

Here is what it prints as the partion table:
Command (? for help): p
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4AB3E32D-3D7C-4D98-A87D-FEA2AD4AE181
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3053 sectors (1.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  EFI system partition
   2          616448         1845247   600.0 MiB   2700  Basic data partition
   3         1845248         2107391   128.0 MiB   0C01  Microsoft reserved part
   4         2107392       329902079   156.3 GiB   0700  Basic data partition
   5       329902080       392816639   30.0 GiB    0700  Basic data partition
   6       392816640       663823359   129.2 GiB   0700  Basic data partition
   7       934830080       976773119   20.0 GiB    2700  Basic data partition
   8       663824384       926679039   125.3 GiB   0700  
   9       926679040       934830079   3.9 GiB     8200  

doing an "i" for another partion (2) I get:
Command (? for help): i 2
Partition number (1-9): 2
Partition GUID code: DE94BBA4-06D1-4D40-A16A-BFD50179D6AC (Windows RE)
Partition unique GUID: 09FAE88F-4B05-490F-91A6-EB4FA00F51FD
First sector: 616448 (at 301.0 MiB)
Last sector: 1845247 (at 901.0 MiB)
Partition size: 1228800 sectors (600.0 MiB)
Attribute flags: 0000000000000001
Partition name: 'Basic data partition'

Things I notice that are diferent. Partion 8 does ntohave a name. and all of it's flags are zero.

Are these important? Do I need to fix these?

---

### Post by oldfred on 2013-12-24
I usually label partitions, but with gpt there seem to be two different labels. Flags are just if needed for some special settings. I do not know much but standard data partitions would not have flags I would think. 
I just checked my original gpt drive, created with gparted to install 10.10. I have no flags and only some have labels.

---

