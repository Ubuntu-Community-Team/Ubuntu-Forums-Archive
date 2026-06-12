---
title: "Two partitions that look like root..."
date: 2013-09-08
forum: General Help
---

### Post by Da_Panther on 2013-09-08
I have two partitions that have the same content as a root partition would. One of them is clearly mounted at " / " mount point. The other is not mounted. It seems to be the same files, but with different "last accessed" dates. 

As far as I am concerned... I can delete this partition? it doesn't even seem to be the recovery files. And it's eating up 12gigs of physical space. 

Whats your take? heres my Parted print-out:

```
Model: ATA FUJITSU MHY2160B (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                  Flags
 1      20.5kB  210MB  210MB   fat32        EFI system partition  boot
 2      210MB   105GB  105GB   hfs+         Untitled
 3      105GB   105GB  1049kB
 4      105GB   117GB  11.7GB  ext4
 7      117GB   117GB  1049kB                                     bios_grub
 5      117GB   127GB  10.2GB  ext4
 6      127GB   131GB  4096MB
 8      131GB   160GB  29.1GB  ext4
```



The partition concerned here is /dev/sda4 ... My root mount is sda5, my /home is sda8 ... Swap is sda6 .... and I also have sda3 that is 1mb that I have no idea what it is. I am dual-booted with Mac OS X. 

What can I remove here?

Thanks!

And two more questions. Is cryptSwap necessary here? I doubt it since it is a personal home computer. And second, is it worth adding agument noatime to speed up the system?

---

### Post by Bashing-om on 2013-09-08
Da_Panther;
Look and see what the file system is mounting .. and compare the UUIDs just to make sure the extraneous "root" is indeed that.

```

cat /etc/fstab
sudo blkid

```
Might be of value to see what the file system is actually mounting;
```

cat /proc/mounts

```
If no listing, then yes it is safe to delete that partition. Though you might double check that there are no files in there you want to keep.
----
> 
and I also have sda3 that is 1mb that I have no idea what it is.
 that is the boot sector for UEFI code.
------------
cryptSwap: just another added layer that can cause problems. Unless you have a demonstrated need to the additional security.. best left alone .. Peruse this forum in respect to all the problems that might entail with cryptswap enabled. 
--------
noatime; may prove of value if you do a lot of write to disk, or a situation of high disk usage, as that option does reduce drive writes (time stamps not updated, for one thing).

[INDENT][INDENT]just my thoughts
[/INDENT][/INDENT]

---

### Post by Da_Panther on 2013-09-08
if cryptswap is already enabled from install, is there more chances of something going boom if I leave it on, or if I deactivate cryptswap? (btw, my extraneous root partition is gonna take a hike.)

And one more question: I now have 12gb free space before my bios_grub partition. I then have my root partition, swap, then /home partitions in that order. Is there any way to shuffle the bios_grub partition to the beginning of the allocated space, and then split the leftover free space between the root and /home partitions?

I would like to avoid if possible, re-installing everything. Thank you !

---

### Post by Bashing-om on 2013-09-08
Da_Panther;

well .. cryptswap can be removed .. a bit of a hassle . Like I have said .. if there is ever a problem, cryptswap adds a level of complexity that is often extremely difficult to overcome. I and many others do not understand how this encryption works.

[INDENT][INDENT]sometimes I just flat do not know
[/INDENT][/INDENT]

---

### Post by Da_Panther on 2013-09-11
Ok, so I removed cryptswap. I still have not been able to resolve my partitioning problem though. 
I want to shuffle partitions around so I can take my now-empty partition, and split its free space between the other root and home partition. Take a look at my partition table at the initial post :

/dev/sda4 is being suppressed. 
I want to put /dev/sda7 right after /dev/sda3
I then want to resize /dev/sda5 to use up all the unused space, then resize that down so I can move my swap space down a bit so I can give my /dev/sda8 a few more gigs.

I know thats a lot of moving around and every move incurs a risk of currupted files, but is there any way of doing this without doing a fresh install? Keep in mind I am dual-booted with OS X.

---

### Post by Bashing-om on 2013-09-11
Da_Panther; Hey.

A picture, to me in this case, is worth that thousand words.
Can you provide a screenshot from GParted of the current partitioning scheme ?

[INDENT][INDENT]what to do, what to do ?
[/INDENT][/INDENT]

---

### Post by Da_Panther on 2013-09-11
[ATTACH=CONFIG]246183[/ATTACH]


Here you go!

I know my partition map is a mess. it's an accumulation of going triple-boot, and multiple repartitionning beween triple-boot, single-boot then double-boot.

---

### Post by Bashing-om on 2013-09-11
Da_Panther; Welp ..

Here is a thought that would be much easier and less risky overall.

What I propose is above my level of comfort coping with ubunt's bios_grub boot sector. But to me this is the better approach to (RE)use that old sda4 space:

Copy sda7 (boot sector) to the existing sda3 1.00 MiB space;
I have no idea what utility - in ubuntu - to use to copy a boot sector's code.
I have not a clue how to tell bios that the boot code has been moved in GPT partitioning.

Once booting was assured: 
Delete the old sda7 - unallocated space;
Delete the old sda4 - unallocated space
Delete sda6 -swap - unallocated space

Re-create swap in that unallocated space that was sda3/4 on the left side of that space;

move sda5 (/) to the left to take up the remaining unallocated space that was sda3/4, minus swap usage on it's left end.
move sda8 (/home) to the left into the unallocated space that used to be swap.

I also like to keep just a tad of space between my partitions (1.00MiB) Just to make sure there are no overlapping boundries and as well a bit of room for error. When moving any partition leftward the hazard of corrupting the data is greater than moving to the right (Header info lost). Just be aware there is that increased risk.

Then again, I also like to keep a shared data partition .. mountable on a need to know basis !

That is what I would do .. find a means to move that boot sector !

[INDENT][INDENT][INDENT][INDENT]simpler is better
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Da_Panther on 2013-09-20
Anybody else have any ideas as to how to tackle this task? Thanks

---

