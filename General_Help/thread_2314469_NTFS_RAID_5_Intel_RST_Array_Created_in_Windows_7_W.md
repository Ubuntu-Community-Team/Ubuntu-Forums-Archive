---
title: "NTFS RAID 5 Intel RST Array Created in Windows 7 Will Not Automount in Xubuntu"
date: 2016-02-21
forum: General Help
---

### Post by duggers on 2016-02-21
I've seen this question asked many times, but not really seen any satisfactory answers. Who knows, there may not be a way, but this is Linux after all...


Background:

I created a Windows 7 PC with a RAID5 array of 4 x 3TB in RAID5 mode using the Intel RST tools. NTFS format and GPT of course. All was well with the world.


I decided to change to Linux, and installed Xubuntu 15.10 and mdadm v3.3 having read that it is now the chosen method for both fakeraid and software raid in Linux, and dmraid should no longer be used as it isn't being maintained.


In Xubuntu, my 4 member array is recognized by the command *mdadm --assemble --scan* at which point I can see the mount point in the file manager and access the files. However all my attempts to get the array to automount at boot have failed, and for now I resorted to running the above command at boot to get the array recognized. Not only does this cause problems with applications that autostart on boot because the paths aren't yet available, but also I've noticed that the array is resyncing way too regularly:


/proc/mdstat is as follows:


Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 

md126 : active raid5 sdb[3] sdc[2] sdd[1] sde[0]

      8790736896 blocks super external:/md127/0 level 5, 64k chunk, algorithm 0 [4/4] [UUUU]

      [==>..................]  resync = 13.5% (397555464/2930245760) finish=323.8min speed=130341K/sec

      

md127 : inactive sde[3](S) sdb[2](S) sdc[1](S) sdd[0](S)

      12612 blocks super external:imsm

If I don't run *mdadm --assemble --scan* at boot then there are no md devices at all in the dev directory so nothing to mount.


I ran *mdadm --detail --scan >> /etc/mdadm/mdadm.conf *to add the following entry to mdadm.conf, which looked as though it should start the array, being that there is a container and an array within the container, but no cigar.


# mdadm.conf

#

# Please refer to mdadm.conf(5) for information about this file.

#

# by default (built-in), scan all partitions (/proc/partitions) and all

# containers for MD superblocks. alternatively, specify devices to scan, using

# wildcards if desired.

#DEVICE partitions containers

# auto-create devices with Debian standard permissions

CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system

HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts

MAILADDR root

# definitions of existing MD arrays

ARRAY /dev/md/imsm0 metadata=imsm UUID=fa564a5c:9be13809:7c6ea277:5b529137
ARRAY /dev/md/Media_0 container=/dev/md/imsm0 member=0 UUID=a53a23c8:dec5b19f:9a155dc7:6db758f6

I understand that my array is NTFS, but is there no way to get it mounted properly at boot with an entry in fstab without completely rebuilding the array in ext file format?

---

