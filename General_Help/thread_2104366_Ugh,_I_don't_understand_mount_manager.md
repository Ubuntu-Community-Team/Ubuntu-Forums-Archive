---
title: "Ugh, I don't understand mount manager"
date: 2013-01-12
forum: General Help
---

### Post by palacequeen55 on 2013-01-12
[FONT="Comic Sans MS"][SIZE="2"][/SIZE][/FONT]
okay, I have mount manager on my computer which is totally linux.
It gives me what drives or disk I have on my computer. I've been trying since last month to mount my terabyte drive and have not been able to do it. When I went to fstab this is what I get 
UUID=efd874bf-9e82-4463-8934-5818d1ca7ae0	/boot	ext2	defaults	0	2
UUID=e069521e-6c94-4571-9670-880f1d3a0fc8	swap	swap	sw	0	0
UUID=69eb572e-8b94-44a1-9682-b6ea4ee9ac9b	/media/janet/69eb572e-8b94-44a1-9682-b6ea4ee9ac9b	ext4	defaults	0	0

I am totally clueless as to what this means.
I open mount manager and this is what I get:
Information about /dev/sdb:
Type: disk
Product: KINGSTON SNV425S
Size: 59.6Gb
Major: 8
Minor: 16

Informationm about  /dev/sdb1:  Information about /dev/sdb5:
Product: vollume (ext4)          Product: volume (swap)
File System; ext4                File System: swap
Label:                           Label:
Number of blocks: 0              Number of blocks: 0
Size: 55.6Gb                     Size: 4Gb
Vendor:                          Vendor:
Major: 8                         Major: 8
Minor: 17                        Minor: 21

And there's more, but before I continue, I just want to say that I have two hard drives and a ssd on my computer.
I am so new to code with linux. I just recently starting learning how to do things on the terminal. I just need help in mounting both my drives at startup and retrieve my terabyte drive. I had it before and now I don't, well.. I can't get to it. So can anyone help me?
Here's the rest of the info
Information about /dev/sda:
Type: disk
Product: SAMSUNG HD1035J
Size: 931.5Gb
Major: 8
Minor: 0
Information about /dev/sda1:  Information about ?dev/sda5:
Product: volume (ext2)        Product: Volume (LVM2_member)
File System: ext2             File system: LVM2_member
Label:                        Label:
Number of blocks: 0           Number of blocks: 0
Size: 243Mb                   Size: 931.3Gb
Vendor:                       Vendor:
Major: 8                      Major: 8
Minor: 1                      Minor: 5

This is the error message I get when I try to mount my hard drive:

Error mounting system-managed device /dev/sdb1: Command-line `mount "/media/janet/69eb572e-8b94-44a1-9682-b6ea4ee9ac9b"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by tgalati4 on 2013-01-12
Your terabyte drive is on /dev/sda.

```
sudo mkdir /media/myterabytedrivethatiamdesparatelytryingtomount
sudo mount /dev/sda1 /media/myterabyedrivethatiamdesparatelytryingtomount

```

---

### Post by bab1 on 2013-01-13
> **palacequeen55 said:**
> [FONT="Comic Sans MS"][SIZE="2"][/SIZE][/FONT]
okay, I have mount manager on my computer which is totally linux.
It gives me what drives or disk I have on my computer. I've been trying since last month to mount my terabyte drive and have not been able to do it. When I went to fstab this is what I get 
UUID=efd874bf-9e82-4463-8934-5818d1ca7ae0	/boot	ext2	defaults	0	2
UUID=e069521e-6c94-4571-9670-880f1d3a0fc8	swap	swap	sw	0	0
UUID=69eb572e-8b94-44a1-9682-b6ea4ee9ac9b	/media/janet/69eb572e-8b94-44a1-9682-b6ea4ee9ac9b	ext4	defaults	0	0

I am totally clueless as to what this means.

... I just want to say that I have two hard drives and a ssd on my computer.

I am so new to code with linux. I just recently starting learning how to do things on the terminal. I just need help in mounting both my drives at startup and retrieve my terabyte drive. I had it before and now I don't, well.. I can't get to it. So can anyone help me?
Sure.  We'll need some diagnostic info.  See below.> 

This is the error message I get when I try to mount my hard drive:

Error mounting system-managed device /dev/sdb1: Command-line `mount "/media/janet/69eb572e-8b94-44a1-9682-b6ea4ee9ac9b"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
The error can be as simple as a config error.  Let's look at the setup in a different way.  What do you get with this terminal command```
sudo blkid -c /dev/null -o list
```
...This should list all the partitions somewhat like this```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext3    system   /              fb80eecb-e0cf-49a2-9936-6e219d09a7e1
/dev/sda2  swap             <swap>         69e4c9c7-a439-416d-85a9-c79162983068
/dev/sda3  ext4             /home          46a258bf-6ace-4d52-b4d7-db47e7b3de7b
/dev/sda5  LVM2_member      (in use)       n3dccf-ro7l-Pbgk-Z3iw-CNVu-BnYq-Blv7we
/dev/mapper/WD1TB-share
           ext4             /smb/share     6034d512-779a-42a8-949c-7a6b99802d64
/dev/mapper/WD1TB-backup
           ext4             /smb/backup    feca7b78-95a0-427e-9fb6-d32fbe3a4d58

``` 
...The bottom 3 entries are for LVM volumes.

What do you get with this command```
sudo fdisk -l
```
...it should look something like this```
sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002d2a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19530752   83  Linux
/dev/sda2            2432        4377    15625216   82  Linux swap / Solaris
/dev/sda3            4377       28693   195312640   83  Linux
/dev/sda4           28693      121602   746291201    5  Extended
/dev/sda5           28693      121602   746291200   8e  Linux LVM

```

Post the output of the 2 commands and we can go from there.

FYI the /dev/sda or /dev/sdb naming can change.  That is why the UUID is used to ID the various partitions.  The UUID always stays the same for the partition.  But you don't need to mount these partitions at /media nor do you need to use the UUID as the mount point.  You could mount the partition at /mnt/data or /mnt/storage or whatever.

Once I can see the data we can start to unravel the mystery.  ;-)

---

### Post by palacequeen55 on 2013-01-13
okay, thanks for you help
this is what I got with the first command

/dev/sda1 efd874bf-9e82-4463-8934-5818d1ca7ae0  ext2 (not mounted)

/dev/sda5 IBvuiy-SX6e-pneU-NI1U-6atF-nTOJ-uPDKmr LVM2_member (in use)

/dev/sbd1 69eb572e-8b94-44a1-9682-bfea4ee9ac9b   ext4 (not mounted)

/dev/sdb5 e065521e-6c94-4571-9670-880f1d3a0fc8   swap  <swap>

/dev/mapper/ubuntu-root 6b03c57f-6caa-4be7-b605-2db53e189182 ext4 /

/dev/mapper/ubuntu-swap-1 92ca5174-38ae-43b1-b663-0bf71b5dd7c5 swap (not mounted)

fdisk -1
fdisk: invalid option --'1'
Usage:
fdisk [options] <disk>  change partition table
fdisk [options] -1 <disk> list partition table(s)
fdisk -s <partitions>    give partition size(s) in blocks

Options:
-b <size>   sector size (512, 1024, 2048 or 4096)
-c[=<mode>] compatible mode: 'dos' or 'nondos' (default)
-h          print this help text
-u [<unit>]  display units: 'cylinders' or 'sectors' (default)
-V          print program version
-C <number> specify the number of cylinders
-H <number> specify the number of heads
-S <number> specify the number of sectors per track

---

### Post by bab1 on 2013-01-13
> **palacequeen55 said:**
> okay, thanks for you help
this is what I got with the first command

/```
dev/sda1 efd874bf-9e82-4463-8934-5818d1ca7ae0  ext2 (not mounted)

/dev/sda5 IBvuiy-SX6e-pneU-NI1U-6atF-nTOJ-uPDKmr LVM2_member (in use)

/dev/sbd1 69eb572e-8b94-44a1-9682-bfea4ee9ac9b   ext4 (not mounted)

/dev/sdb5 e065521e-6c94-4571-9670-880f1d3a0fc8   swap  <swap>

/dev/mapper/ubuntu-root 6b03c57f-6caa-4be7-b605-2db53e189182 ext4 /

/dev/mapper/ubuntu-swap-1 92ca5174-38ae-43b1-b663-0bf71b5dd7c5 swap (not mounted)
```

fdisk -1```

fdisk: invalid option --'1'
Usage:
fdisk [options] <disk>  change partition table
fdisk [options] -1 <disk> list partition table(s)
fdisk -s <partitions>    give partition size(s) in blocks

Options:
-b <size>   sector size (512, 1024, 2048 or 4096)
-c[=<mode>] compatible mode: 'dos' or 'nondos' (default)
-h          print this help text
-u [<unit>]  display units: 'cylinders' or 'sectors' (default)
-V          print program version
-C <number> specify the number of cylinders
-H <number> specify the number of heads
-S <number> specify the number of sectors per track
```

First things first.  The command is ```
fdisk -l
```...that's a lowercase l (ell) not a one (1).

Please use the ```
 [/ code] blocks to enclose the text.  it makes it easier to read.  Clicking on the **[SIZE="3"]#[/SIZE]** icon at the top of the editor will also wrap the text in [code] blocks.

What you have is still a little confusing to me.  So tray the *fdisk* command again and aslo provide the output of this command[CODE]cat /etc/fstab
```

---

### Post by palacequeen55 on 2013-01-13
okay, sorry my mistake.
I will make corrections
Thanks

---

### Post by palacequeen55 on 2013-01-20
Hi
This is what I got, sorry for the delay, I was away from my main computer
 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00071c34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
/dev/sda5          501760  1953523711   976510976   8e  Linux LVM

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000db0eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   116660223    58329088   83  Linux
/dev/sdb2       116662270   125044735     4191233    5  Extended
/dev/sdb5       116662272   125044735     4191232   82  Linux swap / Solaris

Disk /dev/mapper/ubuntu-root: 995.6 GB, 995606134784 bytes
255 heads, 63 sectors/track, 121042 cylinders, total 1944543232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 4290 MB, 4290772992 bytes
255 heads, 63 sectors/track, 521 cylinders, total 8380416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

Disk /dev/sdc: 8006 MB, 8006926336 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15638528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000baf98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62    15635593     7817766    c  W95 FAT32 (LBA)

second command
ubuntu@ubuntu:~$ sudo cat /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0

---

### Post by bab1 on 2013-01-20
> **palacequeen55 said:**
> Hi
This is what I got, sorry for the delay, I was away from my main computer
 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00071c34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
/dev/sda5          501760  1953523711   976510976   8e  Linux LVM

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000db0eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   116660223    58329088   83  Linux
/dev/sdb2       116662270   125044735     4191233    5  Extended
/dev/sdb5       116662272   125044735     4191232   82  Linux swap / Solaris

Disk /dev/mapper/ubuntu-root: 995.6 GB, 995606134784 bytes
255 heads, 63 sectors/track, 121042 cylinders, total 1944543232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 4290 MB, 4290772992 bytes
255 heads, 63 sectors/track, 521 cylinders, total 8380416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

Disk /dev/sdc: 8006 MB, 8006926336 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15638528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000baf98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62    15635593     7817766    c  W95 FAT32 (LBA)

second command
ubuntu@ubuntu:~$ sudo cat /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0

It appears that you aren't booting from the correct drive.  It looks like you are booted off the 8GB flash drive.  The /etc/fstab seems to show that.

Is the host (computer) capable of booting off the internal SDD?

The for some reason you have created Logical Volumes (LVM) for no logical reason.  This is troubling ***"Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table"***.  The same is true for the LVM /dev/mapper/ubuntu-swap.

How are you going to use the 1TB drive?  Where in the file system do you want to mount it?  

At this point I would seriously consider reformatting both the SSD (KINGSTON) and the HDD (SAMSUNG) and restoring the data from the backup.  You do have the data backed up, right?

The order in which you format the drives and re-install the OS could be important depending upon how you are going to use the HDD.

On last thing: [COLOR="Red"]Please use the [code] [/ code] blocks to enclose the text. it makes it easier to read. **[SIZE="3"]Clicking on the [SIZE="4"]#[/SIZE] icon at the top of the editor will also wrap the text in [code] blocks.[/SIZE]**[/COLOR]

If you don't understand this, ask.  I'm lazy and don't feel I should have to format this stuff so that I can read it.  So do your part; use the [code] blocks please.  ;-)

---

### Post by palacequeen55 on 2013-01-21
Okay
I don't understand what you mean by code blocks. And two, the terabyte drive has all my pictures, videos, movies, music and documents on it..so no I can't do a reinstall with that one. The hard drive has the operating system on it and I didn't realize that I created a LVM. That was by accident because I literally don't know what I'm doing. Like I said on previous post, my son build my computer from scratch and installed Ubuntu. I don't know anything about coding, so I am learning slowly what to do.
Also, I am using my flash drive to boot up my computer because I can't or don't know how to mount my hdd or my terabyte drive.

---

### Post by bab1 on 2013-01-21
> **palacequeen55 said:**
> Okay
I don't understand what you mean by code blocks. 
When you are replying to a post you are using the forum editor.  Along the top of the message box there are icons.  The third one from the right is a hash Icon (**[COLOR="Red"]#[/COLOR]**).  If you click on that icon it will add the code blocks and you can paste the data inside of them.> 

And two, the terabyte drive has all my pictures, videos, movies, music and documents on it..so no I can't do a reinstall with that one. The hard drive has the operating system on it and I didn't realize that I created a LVM. That was by accident because I literally don't know what I'm doing. Like I said on previous post, my son build my computer from scratch and installed Ubuntu. I don't know anything about coding, so I am learning slowly what to do.
Also, I am using my flash drive to boot up my computer because I can't or don't know how to mount my hdd or my terabyte drive.
Lets see if we can mount the 1TB drive.  Open a terminal (ctrl+alt+t) and past this command (at the prompt)```
sudo mkdir /mnt/tmp;sudo mount /dev/sda5 /mnt/tmp
```

If it doesn't return errors, see if you can find the media folder under the "file system" when you open the file manager (**not the mount manager**).  Look for the **mnt** folder ad then the **tmp** folder.  Your pics and stuff should be inside if the drive successfully is mounted.

If this doesn't work or you don't understand please ask questions.

[COLOR="Blue"]Edit:  This will not be permanent, but it will tell me that the data on the 1TB drive is still available.  [/COLOR]

---

