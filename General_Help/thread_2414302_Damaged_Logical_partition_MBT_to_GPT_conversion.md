---
title: "Damaged Logical partition MBT to GPT conversion"
date: 2019-03-08
forum: General Help
---

### Post by kasak730 on 2019-03-08
I had tried to convert my HDD from MBR to GPT, and like an idiot converted every partition separately not
knowing I only had to convert the whole disk at once. I had seen a few tutorials where people were using 
Parted to convert the MBR. Below is a printout of my partitions before the destruction:
 

```


fdisk -l /dev/sda

Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start      End         Size        Type      File system  Flags
 2      2048s      39063551s   39061504s   primary   ext4         boot
 3      39067646s  650115071s  611047426s  extended
 5      39067648s  468023295s  428955648s  logical   ext4
Partition 3 does not start on physical sector boundary.

```

So to explain exactly what I did. I wanted to rid my system of the MBR 4 Primary partition limitation. Here
is a overview of each partiton was and usage: sda2 /, sda3 extended , & sda5 /home. Converting sda2 was
no problem. I ran into my issues when I got to sda3. I had tried converting (dev/sda3 204.6G extended) from
beginning to end (39067646s-650115071s) thinking this would include everything in the (dev/sda5 /home 86.8G logical)
partition. What I am left with is 2 partitions. Partition sda2 is fine with no issues, sda3 looks to have
absorbed  sda5. I can no longer access these files from sda5. I know all my files are still there because I
used photorec to dump sda3 to an external sdd, then dd'd a complete copy of sda3 to another hdd. All the files
are still on the drive because when I used photorec for recovery, it dumped all files into whole bunch of directories
incrementally named "recup_dir...", but for the least they are there.

Somewhere in this process it seems as the partitions shifted a bit; Original sda2 / is now sda1 with everything
intact. Original partition sda3 is now sda2.

When running cfdisk on the sda2, I can see it shows as having a sub-partition of 86.8G which is exactly what my
original /home partition was. It lists it as "Free space" however which confuses me a bit.


```

cfdisk /dev/sda2
 Disk: /dev/sda2
                                        Size: 291.4 GiB, 312856282112 bytes, 611047426 sectors
                                                  Label: dos, identifier: 0x00000000

    Device              Boot                     Start               End           Sectors          Size        Id Type
>>  /dev/sda2p1                                      2         428955649         428955648        204.6G        83 Linux
    Free space                               428955650         611047425         182091776         86.8G

```


Also, taking a look with gdisk it shows as the MBR "protective", and GPT only "present". Not sure if this should like like this

```

gdisk /dev/sda
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

```



All in all, what Id like to do ideally, would be to just recover my /home partition with the same folder names and file structure. 
Once I have accomplished this I plan to format the whole drive and start fresh, it would be a huge loss to not be able to recover
all my files. Any and all help would be greatly appreciated.


Here is the exact commands I had used while converting:

```

#COMMANDS USED


parted /dev/sda
unit s


mktable gpt
        i #for ignore
          #yes to continue
        i #for ignore
    

Parted /dev/sda
unit s
mkpart     
    #partition name >blank
    #filesystem type >ext4
    #start >2048s 
    #end >39063551s
    i #for ignore


mkpart "" home 39067646s 650115071s

set 1 legacy_boot on 

partprobe


```

A before and after of partitions:


```

#Before conversion

fdisk -l /dev/sda

Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start      End         Size        Type      File system  Flags
 2      2048s      39063551s   39061504s   primary   ext4         boot
 3      39067646s  650115071s  611047426s  extended
 5      39067648s  468023295s  428955648s  logical   ext4
Partition 3 does not start on physical sector boundary.



#After conversion

fdisk -l /dev/sda

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 4DC051BC-5700-489A-8E0B-919A562986E4

Device         Start       End   Sectors   Size Type
/dev/sda1       2048  39063551  39061504  18.6G EFI System
/dev/sda2   39067646 650115071 611047426 291.4G Linux filesystem

```

---

### Post by oldfred on 2019-03-08
Have you reviewed gdisk's conversion suggestions?
I would create an image of drive and work on the image, that way any errors in trying to fix it does not then totally destroy it.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

Do you have a backup of your MBR partition table?
It looks like you could restore that.
Some have been able to totally create the backup table that sfdisk creates if they know exact start and size of partitions which it does look like you know.

Change any examples from sdc to your drive.
Not sure how translation of logical partitions in an extended works. There are some rules about at least one sector between partitions, but not sure if MBR or gpt or both.

On your copy I might try fsck first.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdc1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdc1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdc1

It looks like you copy also put boot flag on / partition. You cannot have that.
With gpt you must either have an ESP - efi system partition as FAT32 or a bios_grub partition as unformatted for grub to install. If just data drive you do not need either, but I like to put both on all drives, just so I can have an install on that drive without having to totally reconfigure drive.

---

### Post by kasak730 on 2019-03-08
Thanks for a quick response. I will check to see if I have a backup of the MBR table as suggested a bit later when I get home. As far as e2fsck, I have read into this and have tried using it on an image with a few different arguments, to no avail. Although, your examples are a bit different than those I had tried, so I will try again using your examples. For the boot flag being on the / I forgot to mention how this came to be. So, after using the above commands to convert to GPT, sda2 / is now sda1 with everything intact, and what was partition sda3 is now sda2. I believe I had used gdisk for this to create a FAT 200MiB ESP on  partition sda3. Then I aligned it to sector 2048, once I had done this  sda3 disappeared and I only has sda1 with EFI with boot flag. I also have. I will try these things when I get home and will update as to the outcome.

---

### Post by oldfred on 2019-03-08
If you redid partitions after conversion, it will be more difficult or impossible to recover.
If deeper search in testdisk showed files, best to copy those immediately.
If you have to use photorec, you only get files by type or just the extension, and you have to rename. Took me weeks to compare many txt files with old backup to see which had newer of older data.

---

### Post by kasak730 on 2019-03-16
@olfred Thank you for you assistance.    I was finally able to sole this via another forum  [https://www.linuxquestions.org/questions/showthread.php?p=5974577#post5974577](https://www.linuxquestions.org/questions/showthread.php?p=5974577#post5974577)

---

