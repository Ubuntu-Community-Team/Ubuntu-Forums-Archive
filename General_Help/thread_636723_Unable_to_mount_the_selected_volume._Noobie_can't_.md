---
title: "Unable to mount the selected volume. Noobie can't mount (DVD R/RW)"
date: 2007-12-10
forum: General Help
---

### Post by panvorax on 2007-12-10
Could one of you out there please assist a total noob in his initiation into Linux. I am trying to access my DVD R/RW but I get.

 "Unable to mount the selected volume."

 This is helpfully appended with the details...

  "mount: no medium found
   mount: no medium found
   error: could not execute pmount"

 The drive is showing in the list of drives within the computer - file browser screen.
 No problem with my CD drive, cameras or flash drives.
 Another forum thread describes a similar problem but I was unable to extract a solution from that discussion. The person helping in that thread requested the results of... 
 sudo fdisk -1, which I then went and entered as well just to compare results. My results did not look much like this persons screen. Here's mine if it helps.

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

I'm very keen to give Bill the flick but I suspect this whole linux learning curve will keep Mr. Gates on at least one of my machines for a while to come.

---

