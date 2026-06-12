---
title: "RAID1 array with a RAID0 array as member becomes degraded after reboot"
date: 2013-08-27
forum: General Help
---

### Post by runesvend on 2013-08-27
Hi

I have a one 2 TB HDD (sdb) and two 1 TB HDDs (sdc and sdd) on my system that I've combined into a single 2 TB RAID1 array like so:

```
rune@rune-desktop:~$ cat /proc/mdstat 
Personalities : [raid0] [linear] [multipath] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sdd1[1] sdc1[0]
      1953522688 blocks super 1.2 512k chunks
      
md2 : active raid1 md0[2] sdb1[0]
      1953382488 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

```

My two 1 TB harddrives are sdd and sdc, and I've combined them into a 2 TB RAID0 array called md0. I've then created a 2 TB RAID1 array that consists of my 2 TB harddrive, called sdb, and the 2 TB RAID0 array, md0.

I can get this up and running without problems like you see above. But when I reboot I get a message at the boot loader screen saying "WARNING: degraded RAID devices detected", and upon logging in and checking mdstat it says the following:

```
rune@rune-desktop:~$ cat /proc/mdstat 
Personalities : [raid0] [linear] [multipath] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sdd1[1] sdc1[0]
      1953522688 blocks super 1.2 512k chunks
      
md2 : active (auto-read-only) raid1 sdb1[0]
      1953382488 blocks super 1.2 [2/1] [U_]
      
unused devices: <none>

```

So for some reason the RAID0 device md0 is not added as a member of the RAID1 device md2 after rebooting.

This can be fixed easily by running

```
sudo mdadm /dev/md2 --add /dev/md0
```

at which point it works fine again, and the content of /proc/mdstat is what you see at the top.

I don't understand why this happens, can anyone help me out?

Here is the content/output of some relevant config files and commands:

```
rune@rune-desktop:~$ cat /etc/mdadm/mdadm.conf
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
MAILADDR runesvend@gmail.com

# definitions of existing MD arrays
#ARRAY /dev/md/1 metadata=1.2 UUID=99a58381:f109c9cb:e5bf2507:2d8bbd40 name=runescomp:1
ARRAY /dev/md0 UUID=4d8bea96:08136ba8:75029197:fe2e2a4b
ARRAY /dev/md2 UUID=494e7219:c094f19f:97e26ffa:e09020d3

#DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1

#ARRAY /dev/md0 devices=/dev/sdc1,/dev/sdd1
#ARRAY /dev/md2 devices=/dev/sdb1,/dev/md0


# This file was auto-generated on Sat, 09 Jun 2012 21:31:11 +0200
# by mkconf $Id$

```

```
rune@rune-desktop:~$ sudo sfdisk -luS

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/32/32 (instead of 9729/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      1024  41944063   41943040  83  Linux
/dev/sda2      41944064 152107007  110162944  83  Linux
/dev/sda3     152107008 156301311    4194304  82  Linux swap / Solaris
/dev/sda4             0         -          0   0  Empty

Disk /dev/sdb: 243201 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/81/63 (instead of 243201/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1          2048 3907029167 3907027120  83  Linux
		end: (c,h,s) expected (1023,80,63) found (513,80,63)
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

Disk /dev/sdc: 121601 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/81/63 (instead of 121601/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1          2048 1953525167 1953523120  83  Linux
		end: (c,h,s) expected (1023,80,63) found (769,80,63)
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty

Disk /dev/sdd: 121601 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/81/63 (instead of 121601/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdd1          2048 1953525167 1953523120  83  Linux
		end: (c,h,s) expected (1023,80,63) found (769,80,63)
/dev/sdd2             0         -          0   0  Empty
/dev/sdd3             0         -          0   0  Empty
/dev/sdd4             0         -          0   0  Empty

Disk /dev/sde: 31130 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sde1            63 500118191  500118129  83  Linux
/dev/sde2             0         -          0   0  Empty
/dev/sde3             0         -          0   0  Empty
/dev/sde4             0         -          0   0  Empty

Disk /dev/md2: 488345622 cylinders, 2 heads, 4 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/md2: unrecognized partition table type
No partitions found

Disk /dev/md0: 488380672 cylinders, 2 heads, 4 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/md0: unrecognized partition table type
No partitions found

Disk /dev/mapper/cryptswap1: 261 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/mapper/cryptswap1: unrecognized partition table type
No partitions found

```

```
rune@rune-desktop:~$ sudo blkid
/dev/sda1: UUID="53d93e82-bd1a-4b17-b657-d8694c5adb68" TYPE="ext4" 
/dev/sda2: UUID="4d5c45de-7e2d-4b06-88cc-9c9ad79a3784" TYPE="ext4" 
/dev/sdb1: UUID="494e7219-c094-f19f-97e2-6ffae09020d3" UUID_SUB="96a9e998-62e2-4e41-3666-063053208eec" LABEL="rune-desktop:2" TYPE="linux_raid_member" 
/dev/sdc1: UUID="4d8bea96-0813-6ba8-7502-9197fe2e2a4b" UUID_SUB="f67f0a5d-8bb8-3a6d-2203-3ee9b1cb4b63" LABEL="rune-desktop:0" TYPE="linux_raid_member" 
/dev/sdd1: UUID="4d8bea96-0813-6ba8-7502-9197fe2e2a4b" UUID_SUB="051a379b-f8fb-6a72-47a8-dac0e8194f5f" LABEL="rune-desktop:0" TYPE="linux_raid_member" 
/dev/sde1: LABEL="home" UUID="5250b4cd-738d-4768-96ec-d075e78d7524" TYPE="ext4" 
/dev/md2: UUID="a5e937e4-0f48-407c-ac1e-c0dbf9e5c15a" TYPE="crypto_LUKS" 
/dev/md0: UUID="494e7219-c094-f19f-97e2-6ffae09020d3" UUID_SUB="84e912ab-9064-cc61-e0cd-97b421e50d77" LABEL="rune-desktop:2" TYPE="linux_raid_member" 
/dev/mapper/cryptswap1: UUID="f979ceda-2aa3-46a0-a4be-ef05e9698564" TYPE="swap" 

```

```
rune@rune-desktop:~$ grep "md" /var/log/syslog
Aug 27 19:45:03 rune-desktop kernel: [    1.948073] md: bind<sdb1>
Aug 27 19:45:03 rune-desktop kernel: [    1.957798] md: bind<sdc1>
Aug 27 19:45:03 rune-desktop kernel: [    2.032624] md: bind<sdd1>
Aug 27 19:45:03 rune-desktop kernel: [    2.034058] md: raid0 personality registered for level 0
Aug 27 19:45:03 rune-desktop kernel: [    2.034154] md/raid0:md0: md_size is 3907045376 sectors.
Aug 27 19:45:03 rune-desktop kernel: [    2.034156] md: RAID0 configuration for md0 - 1 zone
Aug 27 19:45:03 rune-desktop kernel: [    2.034157] md: zone0=[sdc1/sdd1]
Aug 27 19:45:03 rune-desktop kernel: [    2.034166] md0: detected capacity change from 0 to 2000407232512
Aug 27 19:45:03 rune-desktop kernel: [    2.035447]  md0: unknown partition table
Aug 27 19:45:03 rune-desktop kernel: [    2.227531] md: linear personality registered for level -1
Aug 27 19:45:03 rune-desktop kernel: [    2.228822] md: multipath personality registered for level -4
Aug 27 19:45:03 rune-desktop kernel: [    2.231223] md: raid1 personality registered for level 1
Aug 27 19:45:03 rune-desktop kernel: [    2.476808] md: raid6 personality registered for level 6
Aug 27 19:45:03 rune-desktop kernel: [    2.476810] md: raid5 personality registered for level 5
Aug 27 19:45:03 rune-desktop kernel: [    2.476811] md: raid4 personality registered for level 4
Aug 27 19:45:03 rune-desktop kernel: [    2.481027] md: raid10 personality registered for level 10
Aug 27 19:45:03 rune-desktop kernel: [    2.519924] md/raid1:md2: active with 1 out of 2 mirrors
Aug 27 19:45:03 rune-desktop kernel: [    2.519950] md2: detected capacity change from 0 to 2000263667712
Aug 27 19:45:03 rune-desktop kernel: [    2.556584]  md2: unknown partition table
Aug 27 19:45:04 rune-desktop mdadm[1649]: DegradedArray event detected on md device /dev/md2
Aug 27 19:45:04 rune-desktop mdadm[1649]: DeviceDisappeared event detected on md device /dev/md0, component device Wrong-Level
Aug 27 19:45:05 rune-desktop dbus[694]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Aug 27 19:45:05 rune-desktop dbus[694]: [system] Successfully activated service 'org.freedesktop.systemd1'
Aug 27 19:45:11 rune-desktop udisksd[2697]: Error creating watch for file /sys/devices/virtual/block/md0/md/sync_action: No such file or directory (g-file-error-quark, 4)
Aug 27 19:45:11 rune-desktop udisksd[2697]: Error creating watch for file /sys/devices/virtual/block/md0/md/degraded: No such file or directory (g-file-error-quark, 4)

```

---

### Post by SaturnusDJ on 2013-08-28
It is very likely that the raid 0 array isn't ready in time to participate as member in the raid 1 array.

If the raid 1 array contains your root filesystem (/) then I don't have anything ready to workaround this.

If the raid 1 array does not contain your root filesystem, I do have a way to workaround this.
**Part 1**: Disable auto assembly:
```
nano /lib/udev/rules.d/64-md-raid.rules
```
There put a # before the line saying
> ACTION=="add", RUN+="/sbin/mdadm --incremental $tempnode"


Then in /etc/mdadm/mdadm.conf comment out all ARRAY definitions.

Finally run
```
update-initramfs -u

```

Auto assembly is completely disabled now.

**Part 2**: Scripting the assembly.
We'll move the assembly to a later stage of the boot process, and make sure the second assembly run after the first has completed.
```
nano /etc/rc.local
```
Before the line saying 'exit 0' put these commands:
```
mdadm --assemble /dev/md0 --uuid=4d8bea96-0813-6ba8-7502-9197fe2e2a4b
mdadm --assemble /dev/md1 --uuid=494e7219-c094-f19f-97e2-6ffae09020d3

```

This should do it. If it still fails, insert a line between the two mdadm assemble commands and put 'wait 5' there.
The array won't be ready in time to be mounted by /etc/fstab, so you'll need to do the mount using this file also.

---

### Post by runesvend on 2013-08-28
Thank you very much!

This works perfectly. I didn't have to put anything between the two assemble commands in /etc/rc.local.

The content of md1 is actually encrypted, so I can't mount it via fstab anyway.

I do have one more question though.

When the array is assembled, in nautilus I see a "2 TB Encrypted" volume listed on the left. When I click this I am prompted for the decryption password, and it mounts. This is exactly what I want. Except I would really like if I could choose which folder it's mounted in myself. Right now it's mounted in /media/rune/c6120b3a-7bbd-4867-a6af-6cf783a6a451/ but I'd like to mount it in the location I used before I encrypted the device, which was /media/thesafe/. All my applications are configured to look for data in there.

Is it possible to specify somewhere that when md1 is mounted, it should be mounted in /media/thesafe, but not actually mount it until I click the "2 TB Encrypted" volume in nautilus and enter my password?

---

### Post by SaturnusDJ on 2013-08-28
Glad to hear it's working now.
I did a quick search and it looks like this mount behavior is not easy to manipulate. Your problem can be solved with the use of a symlink (ln command).

---

### Post by runesvend on 2013-08-28
> **SaturnusDJ said:**
> Glad to hear it's working now.
I did a quick search and it looks like this mount behavior is not easy to manipulate. Your problem can be solved with the use of a symlink (ln command).
Thanks! I will do that.

Now that I've got you I'd like to ask one last question, in hopes that you know something about it.

Is it possible to have Ubuntu pop up the "Enter password to unlock encrypted" volume when a program tries to access a file in /media/thesafe/?

Or is it necessary that I click the encrypted volume in nautilus manually, and enter the password to decrypt, before starting a program that wants to read/write files in /media/thesafe/?

---

