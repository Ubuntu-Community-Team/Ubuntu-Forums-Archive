---
title: "Can't mount Luks partition: either superblock or partition table is corrupt"
date: 2016-12-12
forum: General Help
---

### Post by vcrpcant on 2016-12-12
Hi,

A disk I use for archiving some data suddenly doesn't mount anymore.

When I try with terminal, is says something like "either superblock or partition table is corrupt" (see attached screenshot).

When I try to mount it with the Gnome-Disk-Utility, I get this error:
"Error mounting /dev/dm-6 at /media/user1/3PAB: 
Command-line `mount -t "ext3" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-6" "/media/user1/3PAB"' exited with non-zero exit status 32: 
mount: wrong fs type, bad option, bad superblock on /dev/mapper/luks-c4ebeef5-7537-417e-b63b-fedc99561677, missing codepage or helper program, or other error

In some cases useful info is found in syslog - try
dmesg | tail or so.
(udisks-error-quark, 0)"

Also, syslog gives me this:
"Dec 12 15:12:44 d8d kernel: [   47.862779] EXT4-fs (dm-6): mounting ext3 file system using the ext4 subsystem
Dec 12 15:12:44 d8d kernel: [   47.863025] EXT4-fs (dm-6): bad geometry: block count 732566128 exceeds size of device (732565864 blocks)"

I don't understand why it says "mounting ext3 file system using the ext4 subsystem", when I know it's ext3 and "lsblk -f" confirms it.
Although fdisk states "Microsoft basic data" but I already searched google and know this is a bug.

I've tried "fsck" and "fsck -f" more than once both, but no luck.

Can somebody shed some light in here, please?

---

### Post by vcrpcant on 2016-12-14
Meanwhile, I've run testdisk:

/dev/sdg: LBA, HPA, LBA48, DCO support
/dev/sdg: size       5860531055 sectors
/dev/sdg: user_max   5860531055 sectors
/dev/sdg: native_max 5860533168 sectors
/dev/sdg: dco        5860533168 sectors
Using locale 'en_US.UTF-8'.


Wed Dec 14 01:02:53 2016
Command line: TestDisk /debug /log /dev/sdg

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 3.16.0-4-amd64 (#1 SMP Debian 3.16.36-1+deb8u2 (2016-10-19)) x86_64
Compiler: GCC 4.9
Compilation date: 2014-10-19T15:35:24
ext2fs lib: 1.42.12, ntfs lib: libntfs-3g, reiserfs lib: none, ewf lib: none
Hard disk list
Disk /dev/sdg - 3000 GB / 2794 GiB - CHS 364801 255 63, sector size=512 - ST3000DM001-1CH166, S/N:Z1F0R2CP, FW:CC43

/dev/sdg: Host Protected Area (HPA) present.
Partition table type (auto): EFI GPT
Disk /dev/sdg - 3000 GB / 2794 GiB - ST3000DM001-1CH166
Partition table type: EFI GPT

Analyse Disk /dev/sdg - 3000 GB / 2794 GiB - CHS 364801 255 63
hdr_size=92
hdr_lba_self=1
hdr_lba_alt=5860531054 (expected 5860531054)
hdr_lba_start=34
hdr_lba_end=5860531021
hdr_lba_table=2
hdr_entries=128
hdr_entsz=128
Current partition structure:
 1 P Unknown                     2048 5860531021 5860528974 [PABnew]

---

### Post by vcrpcant on 2016-12-18
It seems there's no solution for this :(

---

### Post by hamakei on 2017-01-25
I have more or less exactly the same problem.

"Error mounting /dev/dm-o at /media/hamakei/A113-ENC-P: Command-line 'mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-0" "/media/hamakei/A113-ENC-P" exited with non-zero status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/luks-UUID, missing codepage or helper program, or other error"

And fsck won't run, claiming that it doesn't have write access and I need to be root, even though I'm running it as sudo.

---

### Post by vcrpcant on 2017-09-01
I still haven't found the solution for this. 
And my disk is still awaiting for me to take some time to figure it out.
I have a backup of its data, but I lost some data from the time interval, about 10%.

But the same thing happened to other two disks this week and I thought that was strange and tried a different approach: 
I tried booting with a clone of the operative system I had in my backups from the time I last used that disks successfully (they are data disks I don't use much, but have important data).

Sometimes during the year I make some clones of my current operative system to another disk using clonezilla. 
That way, if I need to boot rapidly for some reason with a system similar of mine, I usually grab one of those cloned disks and solve my problem quickly.

So I tried that and the data showed up in the disks of this week just like before.
Unfortunatelly it didn't work on the disk that led me to create this topic because I didn't think about that at the time and tried to solve this by creating a new partition table.
So I think is something in my actual operative system (Debian 8) than is different from my previous one (Debian 7); or not the operative system itself, but the versions of some tools I've used on them, like fdisk, parted, LUKS crypt sofware, etc.

Just my two cents for anyone having this kind of problems in the future.

---

### Post by vcrpcant on 2017-09-04
I've found the cause of this in here:
[https://bbs.archlinux.org/viewtopic.php?id=171759](https://bbs.archlinux.org/viewtopic.php?id=171759)
Excerpts:
"I suspect you motherboard set a HPA - that's what some gigabyte motherboard tend to do (or used to, at least, someone convinved me a while ago this should no longer happen"
"max sectors = 5860531055/5860533168, HPA is enabled"
"what happened is that Gigabyte boards have a feature to backup the BIOS to the end of the primary HDD"
"It used to be buggy on some boards"

I still can't believe how on earth a f*ck*ng motherboard does this!!!! :evil:

I'm mad as hell and posting this in case anyone has the same problem!

I'll never again buy a Gigabyte motherboard in my life! Never!!! :evil:

---

### Post by vcrpcant on 2017-09-04
Read also this link, for more info on HDA and why it is a curse:
[https://forums.lime-technology.com/topic/10229-hpa-aka-why-are-two-identical-drives-different-sizes/](https://forums.lime-technology.com/topic/10229-hpa-aka-why-are-two-identical-drives-different-sizes/)

---

### Post by vcrpcant on 2017-09-06
For anyone facing a similar problem, don't make a partiton and at the same time create a filesystem like I did (mkpart primary ext3 2048s -1s).
This parted command is fine in normal conditions, but not in this cenario I had.
At most, I should have created an empty partition, not a filesystem, in order to preserve the LUKS header.

You can read the rest of the this story here:
[https://www.linuxquestions.org/questions/showthread.php?p=5756098#post5756098](https://www.linuxquestions.org/questions/showthread.php?p=5756098#post5756098)

---

### Post by vcrpcant on 2018-06-01
Now I know the solution for this situation was quite simple.
In fact, all I had to do was remove the HPA and the LUKS partition and data would come back after restarting the computer:

1st step - check if HPA is enabled:
hdparm -N /dev/sdx

/dev/sdx:
max sectors   = 78125000/78165360, HPA is enabled

2nd step - remove the HPA:
hdparm -N p"max number of sectors" /dev/sdx

example:
hdparm -N p78165360 /dev/sdx
78165360 = denominator from fraction above

done
restart

credits:
[https://superuser.com/questions/642637/harddrive-wipe-out-hidden-areas-like-hpa-and-dco-also-after-malware-infectio?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://superuser.com/questions/642637/harddrive-wipe-out-hidden-areas-like-hpa-and-dco-also-after-malware-infectio?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

see also DCO

---

### Post by cds60601 on 2018-06-02
Hey there fellow Luks-man ;)
You may wish to review my post here: [https://ubuntuforums.org/showthread.php?t=2392959](https://ubuntuforums.org/showthread.php?t=2392959)
There may be some bits you can use with your Luks setup. If not, it's at least some decent links to review as a "Just in case".

Cheers
Chris

---

