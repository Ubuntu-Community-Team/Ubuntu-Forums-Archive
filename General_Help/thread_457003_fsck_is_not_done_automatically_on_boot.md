---
title: "fsck is not done automatically on boot"
date: 2007-05-28
forum: General Help
---

### Post by emanuel.landeholm on 2007-05-28
Hi!

It seems that fsck does not check my partitions on boot. dmesg contains warnings about
max mount count reached. How do I enable fsck checking on boot?

Attached is my fstab. TIA!

---

### Post by LPomfrey on 2007-05-28
I can't seem to see your fstab entry in that post. :confused:

For fsck to check the disk at startup, the 6th column of the fstab entry for the partition you want checked needs to be set to something other than 0.

For example:
```
/dev/hda1 /home ext3 defaults 0 1
```
Would mean that /dev/hda1, which is mounted at /home and is an ext3 partition, would be checked first.

```
/dev/hda1 /home ext3 defaults 0 2
```
Would mean that /dev/hda1, which is mounted at /home and is an ext3 partition, would be checked second.

```
/dev/hda1 /home ext3 defaults 0 0
```
Would mean that /dev/hda1, which is mounted at /home and is an ext3 partition, would not be checked.

---

### Post by emanuel.landeholm on 2007-05-28
The forum complained about bad file type or something and I didn't have time enough to investigate so there was no attachment... I'll just cut&paste instead:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=70d27a1e-88e6-48c9-9e12-fa2108834ea5  /        ext3    defaults,noatime                           0 1
# /dev/hda1
UUID=c20a1e19-7f8a-4e37-b797-3ec71efc616b  /boot    ext2    defaults,noatime                           0 2
# /dev/hda6
UUID=64764b98-57da-4b96-bd14-1ea5839a9480  /tmp     ext3    defaults,noatime,user_xattr,data=writeback 0 2
# /dev/hda7
UUID=7cdc33b7-7db6-462e-9f91-7206c4547230  /var     ext3    defaults,noatime,user_xattr,data=writeback 0 2
# /dev/hda8
UUID=7c0bc9bf-d187-448c-bdf6-f5e57848d8a1  /usr     ext4dev defaults,noatime,user_xattr,data=writeback 0 2
# /dev/hda5
UUID=059198ab-818d-43f8-b84a-8510668cd08b  /opt     ext4dev defaults,noatime,user_xattr,data=writeback 0 2

# /dev/hdc1
UUID=bfa122b2-be76-4502-bf9c-05977a1f3525  /ext     ext4dev defaults,noatime,user_xattr,data=writeback 0 2
# /dev/hdc2
UUID=410b7dad-0e1b-43c2-a094-ccdda3cec895  /fc      ext3    defaults,noatime,user_xattr,data=writeback 0 2
# /dev/hdc3
UUID=1da00c5c-53ab-4505-a44d-2a4eaedfad87  /home    ext4dev defaults,noatime,user_xattr,data=writeback 0 2

# /dev/hdb1
UUID=A8041FA7041F7790                      /xp      ntfs-3g defaults,noatime,nls=utf8,umask=007,gid=46 0 0

# /dev/hda2
UUID=6886af73-3540-4bdf-83e3-415cc11aa991  swap     swap    defaults                                   0 0

/dev/hdd				   /media/cdrom0    udf,iso9660 user,noauto                    0 0

```

The relevant partitions have "0 2" at the last columns so I really don't understand why they're not fsckd.

---

### Post by ajgreeny on 2007-05-28
You can check your file system fsck status using the command:-
**sudo tune2fs -l /dev/hda2**
but change hda2 to whichever of your partitions you want to investigate.  sudo fdisk -l will tell you the correct naming of the partition for this command.

You can then change how often fsck is invoked using tune2fs with the command:-
**sudo tune2fs -c60 /dev/hda2**
which will make it happen every 60 boots.  Again, change the partition identifier to get the right one.

The ubuntu default is every 30 boots, but if you reboot often for whatever reason, that may be rather too often.  I have mine set for every 80 boots and no problems have ever occurred.  Look in **man tune2fs** for other options, eg monthly, etc. etc.

---

### Post by emanuel.landeholm on 2007-05-28
OK, the parameters on the filesys is not the problem. The problem is that fsck does not check the FS on boot.

This is what tune2fs -l has to say about one of the partitions:

```

jel@jel-desktop:~$ sudo tune2fs -l UUID=bfa122b2-be76-4502-bf9c-05977a1f3525
tune2fs 1.40-WIP (14-Nov-2006)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          bfa122b2-be76-4502-bf9c-05977a1f3525
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed directory hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              30523392
Block count:              61036951
Reserved block count:     3051847
Free blocks:              26123556
Free inodes:              30383630
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1009
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Tue May  1 21:42:17 2007
Last mount time:          Mon May 28 15:54:33 2007
Last write time:          Mon May 28 15:54:33 2007
Mount count:              52
Maximum mount count:      29
Last checked:             Wed May  9 12:11:02 2007
Check interval:           15552000 (6 months)
Next check after:         Mon Nov  5 11:11:02 2007
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      e680d895-523b-44d9-bfef-468bf28f7aa5
Journal backup:           inode blocks
jel@jel-desktop:~$ 

```

See how mount count exceeds max mount count?

---

### Post by emanuel.landeholm on 2007-05-28
I think it has something to do with ext4dev. The complaints about max mount count are for my ext4dev systems. But that still doesn't explain why they're not checked... I'm using e2fsprogs 1.40-WIP so my fsck should be able to handle ext4dev.

---

### Post by ajgreeny on 2007-05-28
I'm a bit baffled as to why your system is not doing the fsck, as it appears to have gone way beyond the Max mount count of 29.  Have you tried a manual fsck on reboot using:-
 **sudo shutdown -rF now**
This should mean that the system will reboot and check the filesystem on restart.  If not then something strange is going on and I can't help any further, I'm afraid.  I accept that it still will not tell you why the system does not do this automatically, but at least it may give you peace of mind that your filesystem is all OK.

---

### Post by emanuel.landeholm on 2007-05-28
Oh, I'm sure the partitions are OK. It just bugs me that fsck isn't checking them automatically.
I think I'll just go to single user and fsck manually.

Thanks for your reply!

---

### Post by emanuel.landeholm on 2007-05-29
Problem solved. fsck was looking for a program called fsck.ext4dev so I simply copied fsck.ext3 to fsck.ext4dev.

---

