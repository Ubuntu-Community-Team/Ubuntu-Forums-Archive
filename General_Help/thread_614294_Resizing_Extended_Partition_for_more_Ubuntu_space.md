---
title: "Resizing Extended Partition for more Ubuntu space?"
date: 2007-11-15
forum: General Help
---

### Post by csete on 2007-11-15
I recently installed Gutsy on my Dell E1505 by repartitioning and dual booting with Windows Vista.  That installation went very well.  I then decided I needed more swap space (for hibernation) and shrunk my Vista partition a bit more to get more space for Gutsy.  The problem I'm having is that I can't seem to resize the extended partition holding the Ubuntu data into the empty space before that partition.  I've tried parted, gparted and qtparted.  I've tried this using the Ubuntu live CD as well as Knoppix.  No matter what I try, the resize option will not enable for me.  What do I need to do to get this to work?  My partition information is shown below.  Note the gap between partitions 2 and 3.

Thanks,
Craig

GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            

Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  49.4MB  49.3MB  primary   fat16             
 2      49.4MB  81.4GB  81.4GB  primary   ntfs         boot 
 3      91.9GB  115GB   23.1GB  extended               lba  
 6      91.9GB  112GB   20.1GB  logical   ext3         boot 
 7      112GB   113GB   921MB   logical   linux-swap        
 5      113GB   115GB   2147MB  logical   fat32             
 4      115GB   120GB   4985MB  primary   fat32

---

### Post by mts-fi on 2007-11-16
I was having same problem when resizing windows partitions, using Gparted.

The trick was, as I can remember, to do something with that extra space before you can use it.

It's been long time since I did that, so I'm not sure if this helps you.
Gparted was the tool I used, thats for sure.

---

### Post by bingoUV on 2007-11-16
I assume that the "extended partition holding the Ubuntu data" that you want to resize is partition 6. If not , please correct me and stop reading this post. 

1. The logical partitions 5, 6 and 7 are "inside" extended partition 3. You have to first fix the extended partition 3.

2. Fixing extended partition means moving it about 10 GB backwards so that it starts where partition 2 ends. Now you will be able to resize the extended partition 3 so that it still ends at the place it ends now, but it is about 10GB bigger.
I don't know if gparted supports moving extended partition.

3. Now you can move partition 7 down so that it ends where partition 3 ends.

4. Now you can resize partition 6 so that it ends where partition 7 starts.

---

