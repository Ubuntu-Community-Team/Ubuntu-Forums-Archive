---
title: "Broken ext3 on 1.5TB mdadm raid5, HELP!"
date: 2007-09-29
forum: General Help
---

### Post by deebo32 on 2007-09-29
I had my raid5 running fine on ubuntu 7.04 server install for days, then suddenly last night my log had these entries in syslog

```

Sep 29 07:22:35 sb32 kernel: [24157.236000] EXT3-fs error (device md0): ext3_find_entry: reading directory #88555521 offset 0
Sep 29 07:22:35 sb32 kernel: [24157.240000] EXT3-fs error (device md0): ext3_find_entry: reading directory #88555521 offset 0

```

i rebooted the computer because the forcedeth nic had failed (yet again), and after the reboot, the raid5 didnt come back up

my raid5 consists of sda1 -> sdd1 500GB each

after i got the md0 device up finally (its rebuilding), the ext3 fs seems to be totally broken, i couldnt mount it so i tried fsck:

```

root@sb32:~# fsck.ext3 -n -f -v /dev/md0
e2fsck 1.40-WIP (14-Nov-2006)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

i tried all the superblocks i wrote down when i created the raid but none of them work

ive also tried gpart but it doesnt do ext3 so its pretty useless for me

so im looking for software that would help me analyze the problem and tell me if theres something to do

ANY help appreciated, the raid is full of stuff i just cant loose!

---

### Post by deebo32 on 2007-09-29
i found some working superblocks with testdisk, but im not really sure what i should do here

i get lots of these running fsck

```

Block bitmap for group 2770 is not in group.  (block 23658496)
Relocate<y>? yes

Inode bitmap for group 2770 is not in group.  (block 23658497)
Relocate<y>? yes

Inode table for group 2770 is not in group.  (block 23658498)
WARNING: SEVERE DATA LOSS POSSIBLE.
Relocate<y>? yes

```

---

### Post by deebo32 on 2007-09-29
it seems that all the inode tables got fried in one single reboot somehow, oh well, back to 4x 500G mounts instead of this raid crap with "parity"

---

### Post by deebo32 on 2007-09-29
ok this seems to be a serious issue so ill just post a small writeup here

using a msi nforce 430 motherboard with onboard 1Gbit nic and a s939 3800+ x2 i did the following

1) fdisk /dev/sd[a-d] 
 - all partitions full size 'fd' type (linux raid auto)

2) mdadm --create
- raid5, 4 devices, sda1 sdb1 sdc1 sdd1

3) wait for it to rebuild

4) create mdadm.conf from the data of the drive

5) start filling the drive from another computer on the network via samba

6) noticed forcedeth driver errors, looked up, suggestion was to increase the interrupt cycles, so i did and rebooted

7) couple days pass, no problems

8) i copy more stuff to the raid and forcedeth hangs under big load (~70MB/s over 1Gbit lan)

9) i swith to local terminal, increase the interrupt cycles in /etc/modprobe.d/options again and reboot

10) raid doesnt work after reboot so i mdadm -A it, and it starts rebuilding, i think this is weird but let it finish

11) whole ext3 is corrupted, totally, all inode tables are borked

12) i loose my data and decide to ditch mdadm and raid5 and go for 4x 500GB ext3 shares instead

and this is how the problem reproduced

1) i was copying stuff over the network (via samba) to the new /dev/sda1 when forcedeth hung again, but this time i got output to the local terminal, the sata controller had reset, it couldnt be brought back up so i rebooted

2) journal was fixed and the drive was ok, i disabled the forcedeth device and installed another NIC

3) everything is ok

so it seems that somehow forcedeth hanging resulted in a problem with samba and the sata controller and mdadm didnt notify me fast enough that the sata controller had failed, and when it rebuilt itself it basically rebuilt 4 discs worth of random crap, resulting in the corruption of a 1.5TB raid5 volume

all i can say is ill never use forcedeth again :)

---

### Post by expatCM on 2007-09-30
Yes, I know it is not identical but there are some similarities ...
[http://ubuntuforums.org/showthread.php?t=553591](http://ubuntuforums.org/showthread.php?t=553591)

Seems for some reason that there are problems with writing and deleting large amounts of data on large volumes.  Don't ask me why ...  I just know that it is a major problem and an invitation to keep proper backups on DVD's :(

---

