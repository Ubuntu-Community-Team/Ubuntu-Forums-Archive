---
title: "ZFS ist slow after Ubuntu upgrade to 22.04"
date: 2022-05-20
forum: General Help
---

### Post by exomor on 2022-05-20
Hello all,


I have a problem with my ZFS on my Ubuntu server and hope you can help me. 
I had configured a file server with ZFS on Linux under Ubuntu Server 20.04. 
I have 3x 6TB hard disks combined to a raidz1. This has worked so far wonderfully.


Since Ubuntu server 22.04 was released, I took the opportunity and installed Ubuntu server 22.04 as a software raid NEW. On this system I installed ZFS again and imported my pools created under Ubuntu 20.04. In doing so, I found that my data read speed dropped to about 70 MB/s instead of my usual 200-400 MB/s. 
At first I assumed a faulty installation or configuration of Ubuntu 22.04 or a faulty creation of the software raid. But unfortunately I had to find out that a reinstalled Ubuntu 22.04 version without softwareraid also only manages the ~70 MB/s. 
I had previously made a backup of my Ubuntu 20.04 and re-imported the pools there as a test. Lo and behold... no problem and full read speed.


Furthermore I noticed that when reading the disk with 
dd if=/dev/sdx of=/dev/null bs=1M status=progress 
all disks in the raidz1 array of the ZFS pool come to their full read speed. 


The ZFS configuration under Ubuntu 22.04 is the same as the configuration under 20.04.


I'm unfortunately running out of explanations for the speed loss and hope for your help.


Here is my system data:
- Ubuntu Server 22.04 as softwareraid
- I3-8100
- 32GB RAM
- 10Gbit network card
- ZFS Pool: 
         o Name: tank
         o Raid: raidz1 (3x 6TB)
         o Cache: NVME SSD 500GB as l2arc
I would be glad about any help.


Many greetings
exomor

---

### Post by DuckHook on 2022-05-21
Double layering is not recommended for ZFS. ZFS is designed to take sole control of the HDD(s) without other intervention, especially RAID. Besides, RAID is unnecessary with ZFS since ZFS is designed to do what software RAID does anyway.

However, I have little explanation for your diminished ZFS speed even when installed without RAID.

The only thing that comes to mind is that Jammy has not yet been optimized for ZFS and will need time to get the kinks worked out. Production environments are not good candidates for Jammy until at least its first point upgrade in August. Frankly, I would not upgrade even then. If Focal is running smoothly, I would leave the server running that.
> **exomor said:**
> Furthermore I noticed that when reading the disk with 
dd if=/dev/sdx of=/dev/null bs=1M status=progress 
all disks in the raidz1 array of the ZFS pool come to their full read speed.
You've narrowed the bottleneck down further to a probable ZFS/Jammy mismatch. dd bypasses the filesystem. That's likely why it does things at full speed.

Thinking about it a bit more: perhaps the problem is a different (more current) ZFS version in Jammy. The usual procedure is to upgrade the ZFS pool, but this is a very hazardous process. Such updates are one&#8209;way and cannot be reversed. It would commit you to Jammy with no ability to recover to Focal. All in all, not something that I would do if I were in your shoes.

---

### Post by exomor on 2022-05-22
Hello,


Thank you for your detailed feedback. 
I do not have ZFS on root. My ZFS takes care of the HDDs alone. 
What I have in addition combined as a raid with Ubuntu are my two boot disks, which are not managed by ZFS. However, the software raid of my boot disks is (tested) not causal for the slow read speed. 


Regarding the explanatory approach with Jammy:
A friend of mine has also upgraded his Ubuntu with ZFS. 
With him everything works perfectly with full speed. 
The only existing difference is that he upgraded his existing system from 20.04 to 22.04, and I did a fresh install of Ubuntu 22.04. 


Can this also be related to Jammy? Are there any other explanations if the situation just described can rule out Jammy as the source of the error?


I had done the upgrade of the ZFS pool right after the reinstallation of ubuntu.... I noticed the error with the reading speed only later. It is annoying now, but the upgrade of the ZFS pool can be excluded as a solution. 


Greetings

---

### Post by #&amp;thj^% on 2022-05-22
> **exomor said:**
> 
Can this also be related to Jammy?  I noticed the error with the reading speed only later. It is annoying now, but the upgrade of the ZFS pool can be excluded as a solution. 


Greetings

Just trouble shooting a bit here.
Is the Pool healthy? 
```
zpool status
```
Do you have IO error messages in the Kernel logs? 
```
dmesg -T
```
Also can you show this as well.
```
apt policy zfsutils-linux
```

---

### Post by exomor on 2022-05-22
Hello,

the pool is healthy:
>  pool: tank state: ONLINE
  scan: scrub repaired 0B in 08:35:15 with 0 errors on Tue May 17 03:42:20 2022
config:


        NAME                                         STATE     READ WRITE CKSUM
        zhome                                        ONLINE       0     0     0
          raidz1-0                                   ONLINE       0     0     0
            wwn-diskIDDisk1                    ONLINE       0     0     0
            wwn-diskIDDisk2                     ONLINE       0     0     0
            wwn-diskIDDisk3                     ONLINE       0     0     0
        cache
          nvme-diskIDDiskNVME1  ONLINE       0     0     0


errors: No known data errors


In the output from the kernel logs are some Errors, but no IO Errors:
> ACPI Error: Aborting method \_SB.PCI0.SAT0.PRT4._GTF due to previous error (AE_NOT_FOUND) (20210730/psparse-529)
ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.PRT2._GTF.DSSP], AE_NOT_FOUND (20210730/psargs-330)


this is the output of the policy command:
> 
zfsutils-linux:
  Installed: 2.1.2-1ubuntu3
  Candidate: 2.1.2-1ubuntu3
  Version table:
 *** 2.1.2-1ubuntu3 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        100 /var/lib/dpkg/status


---

### Post by #&amp;thj^% on 2022-05-22
One other than you also see the performance speed drop, Bug Filed: [https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1969281](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1969281)
wouldn't hurt to add yourself to that bug.

---

### Post by exomor on 2022-05-22
cool, thanks for the link!

---

