---
title: "I am trying to create a partition to install windows aongside ubuntu"
date: 2015-06-21
forum: General Help
---

### Post by ben-123463 on 2015-06-21
I have tryed to create a new partition to install windows alongside ubuntu however i got this error

```
[SUP]GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize
[/SUP]
[SUP]Libparted 2.3[/SUP]

[TABLE]
[TR]
[TD="colspan: 2"][SUP] **Shrink /dev/sda1 from 692.69 GiB to 300.63 GiB**  00:48:59    ( ERROR ) [/SUP][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][SUP] calibrate /dev/sda1  00:00:00    ( SUCCESS ) [/SUP][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][SUP] [I]path: /dev/sda1
start: 2048
end: 1452673023
size: 1452670976 (692.69 GiB)[/I] [/SUP][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"][SUP] check file system on /dev/sda1 for errors and (if possible) fix them  00:00:40    ( SUCCESS ) [/SUP][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][SUP] ***e2fsck -f -y -v -C 0 /dev/sda1*** [/SUP][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][SUP] [I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
                                                                               
      893341 inodes used (1.97%, out of 45400064)
        4263 non-contiguous files (0.5%)
         889 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 827461/1040/5
    50434361 blocks used (27.77%, out of 181583872)
           0 bad blocks
          19 large files

      692100 regular files
      116217 directories
          57 character device files
          25 block device files
           1 fifo
          31 links
       84922 symbolic links (64734 fast symbolic links)
          10 sockets
------------
      893363 files
[/I] [/SUP][/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"][SUP] [I]e2fsck 1.42.9 (4-Feb-2014)
[/I] [/SUP][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"][SUP] shrink file system  00:48:19    ( ERROR ) [/SUP][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][SUP] ***resize2fs -p /dev/sda1 315229184K*** [/SUP][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][TABLE]
[TR]
[TD="colspan: 2"][SUP] [I]Resizing the filesystem on /dev/sda1 to 78807296 (4k) blocks.
Begin pass 2 (max = 18288836)
Relocating blocks             XXXXXXXXXXXXXXXXXXXXXXXXXXX-------------[/I] [/SUP][/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="colspan: 2"][SUP] [I]resize2fs 1.42.9 (4-Feb-2014)
resize2fs: Attempt to read block from filesystem resulted in short read while trying to resize /dev/sda1
Please run 'e2fsck -fy /dev/sda1' to fix the filesystem
after the aborted resize operation.
[/I] [/SUP][/TD]
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
[SUP]========================================[/SUP]
[TABLE]
[TR]
[TD="colspan: 2"][SUP] **Create Primary Partition #1 (ntfs, 392.06 GiB) on /dev/sda** [/SUP][/TD]
[/TR]
[/TABLE]
[SUP]========================================[/SUP]


```

Can someone tell me how to fix this

---

### Post by yancek on 2015-06-21
What happened when you ran the command suggested? 
> [I]Please run 'e2fsck -fy /dev/sda1' to fix the filesystem
after the aborted resize operation[/I]

---

### Post by oldfred on 2015-06-21
Are you running from live installer, DVD or flash drive?

Did you run the e2fsck as suggested, from live installer?
OR:
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

