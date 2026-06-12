---
title: "Formatting micro sd card with Gparted"
date: 2014-11-29
forum: General Help
---

### Post by nicoeoc on 2014-11-29
Hi, when trying to format my micro sd card I get the following error:[TABLE]
[TR]
[TD="colspan: 2"][B]

Create Primary Partition #1 (fat32, 3.64 GiB) in /dev/sdb[/B]  00:00:07    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]create empty partition  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][I]ruta: /dev/sdb1
inicio: 2048
fin: 7626751
tamaño: 7624704 (3.64 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]clear old file system signatures in /dev/sdb1  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]clear primary signatures  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]*wrote 68.00 KiB of zeros at byte offset 0*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]clear secondary signatures  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]*wrote 4.00 KiB of zeros at byte offset 3903844352*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]flush operating system cache of /dev/sdb  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]set partition type in /dev/sdb1  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]*new partition type: fat32*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"]create new file system fat32  00:00:06    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"]***mkdosfs -F32 -v -I -n "" /dev/sdb1***[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][I]mkdosfs 3.0.16 (01 Mar 2013)
/dev/sdb1 has 121 heads and 62 sectors per track,
logical sector size is 512,
using 0xf8 media descriptor, with 7624704 sectors;
file system has 2 32-bit FATs and 8 sectors per cluster.
FAT size is 7432 sectors, and provides 951226 clusters.
There are 32 reserved sectors.
Volume ID is 0c30191a, volume label .
[/I][/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"][I]mkdosfs: failed whilst writing FAT
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

How bad is it? is it going to survive? : (

---

### Post by sudodus on 2014-11-29
I have never seen that error. If you get the same error, if you repeat the attempt to create the file system, you may have problems with some bad sector on the drive. That might be checked and fixed for FAT32 using Windows (it is a proprietary file system owned by Microsoft).

But you can try if you can create a linux ext file system (ext2, ext3 or ext4) with gparted. Maybe you get some useful output (if there are errors). You can also check it afterwards with e2fsck
```
sudo e2fsck -fc /dev/sdxy
```

If still the same drive as before: x=b and y=1

You can also try using badblocks directly

```
sudo badblocks /dev/sdxy
``` and if bad blocks are found and marked, you might be able to create an ext file system.

Se the manual files

```
man e2fsck
``` and ```
man badblocks
```

---

### Post by nicoeoc on 2014-11-29
ext2 seems to work fine:

```
GParted 0.16.1 --enable-libparted-dmraid

Libparted 2.3

delete /dev/sdb1 (unknown, 3.64 GiB) from /dev/sdb  00:00:01    ( SUCCESS )
    	
calibrar /dev/sdb1  00:00:00    ( SUCCESS )
    	
path: /dev/sdb1
start: 2048
end: 7626751
size: 7624704 (3.64 GiB)
delete partition  00:00:01    ( SUCCESS )
========================================

Create primary partition #1 (ext2, 3.64 GiB) en /dev/sdb  00:00:28    ( SUCCESS )
    	
create empty partition  00:00:00    ( SUCCESS )
    	
path: /dev/sdb1
start: 2048
end: 7626751
size: 7624704 (3.64 GiB)
clear old file system signatures in /dev/sdb1  00:00:00    ( SUCCESS )
    	
clear primary signatures  00:00:00    ( SUCCESS )
    	
wrote 68.00 KiB of zeros at byte offset 0
clear secondary signatures  00:00:00    ( SUCCESS )
    	
wrote 4.00 KiB of zeros at byte offset 3903844352
flush operating system cache of /dev/sdb  00:00:00    ( SUCCESS )
set partition type in /dev/sdb1  00:00:00    ( SUCCESS )
    	
new partition type: ext2
create new file system ext2  00:00:28    ( SUCCESS )
    	
mkfs.ext2 -L "microsd" /dev/sdb1
    	
file system tag=microsd
OS type: Linux
block size=4096 (bitácora=2)
fragment size=4096 (bitácora=2)
Stride=0 blocks, Stripe width=0 blocks
238560 inodes, 953088 blocks
47654 blocks (5.00%) reserved for the super user
first data block=0
maximum number of file system blocks=977272832
30 group block
32768 blocks per group, 32768 fragments per group
7952 nodes-i per group
superblock backup saved in blocks: 
32768, 98304, 163840, 229376, 294912, 819200, 884736

Allocating group tables: done
writing tables for nodes-i: done
writing superblocks and accountable information of file system: done

mke2fs 1.42.8 (20-Jun-2013)

```

Then e2fsck:

```
~$ sudo e2fsck -fc /dev/sdb1
e2fsck 1.42.8 (20-Jun-2013)
checking damaged blocks (read only check):   0.00% done, 0done                                                 
microsd: Updating bad block inode.
Step 1: Verifying nodes-i, blocks and sizes
Error reading block 239 (Attempt to read block from filesystem resulted in short read) while getting following node-i for checking.  discard error<y>? 

```

Then I've messed with "y" and "n", getting a couple more block errors. Anyway what I understand then is that in order for me to get this in FAT32 I have to format it in Windows? the thing is I need it to work in a cellphone so ext is not what I need right?

By the way thanks for your time!

---

### Post by carlwsnyder on 2014-11-29
You should be able to use EXT2 on an Android phone, and for either Android or iOS, your phone should be perfectly able to format the card by itself.

---

### Post by nicoeoc on 2014-11-29
This whole thing is due to a "probably damaged sd card" error, I first tried to format it from the phone but nothing happened and the error message kept appearing. So now I'm trying to solve it here... and having formatted the card to ext2 hasn't solved the initial problem as the error message is still there, no surprise really as I got those block errors with e2fsck.

: (

---

### Post by sudodus on 2014-11-30
Now that we know there are bad blocks, I think the best solution is to borrow a Windows computer and format it to FAT32 and then treat it with chkdsk

```
chkdsk /r
``` or the corresponding graphical user interface.

>  chkdsk /r does the same thing as chkdsk /f only it also checks for bad sectors on the disk and recovers any readable information. Running chkdsk /r implies that also chkdsk /f is run.

  chkdsk /f only checks for disk errors, not bad sectors.
  Microsoft has a detailed page for [chkdsk]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true"). The following is a snippet explaining /f and /r parameters.[INDENT]   **Fixing disk errors:**
      Chkdsk corrects disk errors only if you specify the /f command-line   option. Chkdsk must be able to lock the drive to correct errors.   Because repairs usually change a disk's **file allocation table** and   sometimes cause a loss of data, chkdsk sends a confirmation message.
      **Finding physical disk errors:**
      Use the /r command-line option to find **physical disk errors** in the   file system.
 [/INDENT]


---

### Post by nicoeoc on 2014-12-06
I finally have formatted the sdcard through a friend's windows pc. Quick format didn't work so well as the sdcard wasn't recognized by my phone, I did slow format and now everything seems to be alright.

Thank you very much sudodus, and carl for the ext2 info.

---

### Post by sudodus on 2014-12-07
Congratulations :KS

---

