---
title: "restore ddrescue img of LVM HDD with errors"
date: 2014-01-28
forum: General Help
---

### Post by a-arjan on 2014-01-28
I had an LVM VG consisting of 2 HDD (2TB and 3 TB) which I added to the VG without partition. In this VG I had 2 LV's. It ran for about a year and a half without problems.
Then smartd started sending me mails about errors on the 3TB disk. Searched the internet and found the program gnu ddrescue. Started to clone de faulty drive. initially very quick then slower and slower with more errors in syslog. ddrescue ran for about a month and finally it was down to a few b/s. 2800GB is recovered but still 10.000 errors on the disk. I figured this is as much as I could get back. made a copy of the ddrescue image and the 2 TB HDD so I have something to play with and the option to try again. In the ddrescue manual  the program ddrescuelog is mentioned [COLOR=#000000]to generate a badblocks file to use with e2fsck. I couldn't figure out how to use this and I have the option to roll back so I decided to try e2fsck with the options -f -y on the LV that I wanted to rescue. Lots of files are rescued (lost+found on the filesystem also contains many entries), but also  some of the files that appear to be there don't work.
[/COLOR]Now for the question: How do I invoke ddrescuelog? I am lost with al the different numbers and kinds (logical extend, PE, sector, block, superblock etc).
This is wat I know for now:
 - 2 hdd without partition in the VG ("opslag").
- 1 LV needs saving("/dev/opslag/data")
- PE size 4,00 MiB
- 2 TB HDD without errors completely used for the LV with the following output from pvdisplay -m
[COLOR=#F5F5F5][FONT=Monaco]O[/FONT][/COLOR]>   --- Physical volume ---  PV Name               /dev/sdd
  VG Name               opslag
  PV Size               1,82 TiB / not usable 1,09 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              476932
  Free PE               0
  Allocated PE          476932
  PV UUID               j1bo3V-oqBt-fZ0K-oruK-CqAJ-ox0s-ORcugj

  --- Physical Segments ---
  Physical extent 0 to 476931:
    Logical volume    /dev/opslag/data
    Logical extents  523397 to 1000328

- 3 TB HDD with errors (ddrescue logfile) of which only a part is used for the LV to be recovered. pvdisplay -m output

>  --- Physical volume ---  PV Name               /dev/sdc
  VG Name               opslag
  PV Size               2,73 TiB / not usable 472,00 KiB
  Allocatable           yes 
  PE Size               4,00 MiB
  Total PE              715397
  Free PE               192000
  Allocated PE          523397
  PV UUID               xDG2jt-i4FK-15jP-lHjl-dYco-iy56-aSfsas
   
  --- Physical Segments ---
  Physical extent 0 to 191999:
    FREE
  Physical extent 192000 to 715396:
    Logical volume    /dev/opslag/data
    Logical extents    0 to 523396

the filesystem of /dev/opslag/data is ext4. I don't know how to find the blocksize or more information about the filesystem.
The command to recreate the faulty disk was "ddrescue --force /dev/sde /dev/sdc /xx/xx/logfile"
I assume i have to invoke ddrescuelog with a command similar to "[COLOR=#000000]ddrescuelog -l- -b512 -i63b -o0 -s9767457b -b4096 logfile > badblocks1".
Just don't know what to fill in for [/COLOR][COLOR=#000000]block size, input position, output position  and the other options.
And a final question: once i figure out how to get te correct badblocks file, can I just run "[/COLOR][COLOR=#000000]e2fsck -v -f -L badblocks1 /dev/..." on the filesystem [/COLOR][COLOR=#000000]which I tried to repair with "e2fsck -f -y" or is it better to start with new copies of the 2 disks?
Thanks for your reply.
Regards,
Arjan

[/COLOR][COLOR=#000000]

[/COLOR]

---

