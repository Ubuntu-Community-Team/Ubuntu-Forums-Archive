---
title: "How to recover after using dd to image the wrong device."
date: 2021-11-30
forum: General Help
---

### Post by zoomiest2 on 2021-11-30
I have several external HDDs connected by USB on my laptop. (They were moderately backed up)

I was using dd to create a bootable USB and I specified the wrong device... now the HDD is named anaconda with a sub directory called EFI which has a sub directory called boot. I actually stopped the process before it went to far, BUT it seemed to have wiped out the file allocation table. :-({|=

On the basis that I don't think I wiped out ALL the data on this 3 TB HDD, do you recommend any way to recover the files? (any cool open source tools?)

---

### Post by oldfred on 2021-11-30
Since large drive, did you have multiple gpt partitions?
Was drive bootable, so it had an ESP as first partition?

You have totally lost whatever the dd wrote & almost for sure the partition table at beginning of the drive.
But gpt has a backup partition table. So that may let you restore partition table. 
Then whether a fsck will let you restore data not overwritten is a question.

What does this show?
sudo gdisk -l /dev/sdX #where sdX is your device like sda or nvme device if that.

And/or what does testdisk show?
If deeper search shows files by name, immediately copy them to another drive, you may not get another chance.
Then photorec can find files by type or extension, but not full name. That may take days on your drive. My much smaller drive took overnight & then since only by extension, I had weeks of work to figure out file names. Or now my backups are much better. And every text file, program has as second line the filename.

---

### Post by ActionParsnip on 2021-12-01
Use your backups

---

### Post by dragonfly41 on 2021-12-01
[COLOR=#000000]> And every text file, program has as second line the filename.

This set me thinking how I might prepare for such a photorec recovery event (other than the main advice to backup).
There are occasions when backups get out of date.

My search for an indexing strategy (to recover files using only metadata such as filesize - no filenames) unearthed
glimpse.

[/COLOR]glimpse

[http://manpages.ubuntu.com/manpages/bionic/man1/glimpseindex.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/glimpseindex.1.html)

Clearly file indexing has to be done *before* any such photorec recovery so this idea will not help the OP.

[P.S.] It seems on reading man glimpse  that this only applies to text files.

---

### Post by zoomiest2 on 2021-12-02
Thanks for your help. Here is the output:

> user@domain:~$ sudo gdisk -l /dev/sdb

GPT fdisk (gdisk) version 1.0.8                                                                 
                                                                                                
Partition table scan:                                                                           
  MBR: MBR only                                                                                 
  BSD: not present                                                                              
  APM: not present                                                                              
  GPT: present                                                                                  
                                                                                                
Found valid MBR and GPT. Which do you want to use?                                              
 1 - MBR                                                                                        
 2 - GPT                                                                                        
 3 - Create blank GPT


Your answer: 2

Using GPT and creating fresh protective MBR.
Warning! Main partition table overlaps the first partition by 34 blocks!
You will need to delete this partition or resize it in another utility.

Disk /dev/sdb: 7814037168 sectors, 3.6 TiB
Model: nal USB 3.0     
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): ACDC3C3A-0466-4000-BFF1-EC30AE25D81F
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 16420830
Partitions will be aligned on 8-sector boundaries
Total free space is 8390611 sectors (4.0 GiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   2           25372           47851   11.0 MiB    0700  ISOHybrid



---

### Post by oldfred on 2021-12-02
It is only showing an 11MB ISO hybrid partition. That is then what you overwrote, but no partition table shown.
ISO did overwrite the primary partition table. 
Do not know if you need to zero out the first 33 sectors so valid partition table data can be written rather than the ISO data. 

What does testdisk show?

---

