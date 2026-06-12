---
title: "Unable to shrink LVM parition"
date: 2016-06-08
forum: General Help
---

### Post by tenet75 on 2016-06-08
Hello,

I am trying reduce a LVM partition from 200GB to 128GB for the purpose of being able to backup and clone it faster.  I came across this in my search:

[http://ubuntuforums.org/showthread.php?t=1537569](http://ubuntuforums.org/showthread.php?t=1537569)

When I get to the point of resizing the parition, I get the following messages:

```
root@kubuntu:~# resize2fs /dev/kubuntu-vg/root 128M
resize2fs 1.42.9 (4-Feb-2014)
resize2fs: New size smaller than minimum (2207281)

root@kubuntu:~# e2fsck -f -v -C 0 /dev/kubuntu-vg/root
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts
Pass 5: Checking group summary information                                     
                                                                
      274165 inodes used (2.14%, out of 12836864)
          89 non-contiguous files (0.0%)
         466 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 226751/26
     2871684 blocks used (5.60%, out of 51316736)
           0 bad blocks
           1 large file

      192078 regular files
       29152 directories
          57 character device files
          25 block device files
           0 fifos
          19 links
       52842 symbolic links (47296 fast symbolic links)
           2 sockets
------------
      274175 files



```

I'm scratching my head as I'm using less than 6% of the available blocks and 2% of available inodes, but can't shrink the partition.  What am I missing?

Some additional information:
This is a VHD that has been duplicated (so no concern about loss of data).
All of this was attempted using a live ISO image.

---

### Post by Dennis N on 2016-06-08
```
root@kubuntu:~# resize2fs /dev/kubuntu-vg/root 128M
```

Did you mean to resize to 128G?

---

### Post by tenet75 on 2016-06-09
Yeah, that might help. :D  I'll give that a try and see what happens.

---

### Post by tenet75 on 2016-06-09
That did the trick.  I guess I hadn't had enough coffee to notice I typed M instead of G. Thanks Dennis for catching that.

---

