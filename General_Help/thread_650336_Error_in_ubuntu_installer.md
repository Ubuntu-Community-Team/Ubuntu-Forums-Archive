---
title: "Error in ubuntu installer"
date: 2007-12-26
forum: General Help
---

### Post by padmanabhanj on 2007-12-26
Iam creating live come install cd of debian, i followed the url to create the llive cd "https://help.ubuntu.com/community/LiveCDCustomization". Then Iam trying to install the live Cd using ubiquity, while at the time of new partition using  manual partitioning i got an error like" ???????", But it is installing without any error by edit partition if i have ext3 partition. any body give me a idea to rectify the error please!

I dont know exactly where the problem is? but when i compared the partman of ubuntu and to my distro is "logical" was not there

This is mydistro partman:

parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 733
parted_server: Opening infifo
/lib/partman/free_space/50new/do_option: IN: NEW_PARTITION =[COLOR="Red"]dev=sda ext2 141968332800-145069263359 Beginning[/COLOR]
parted_server: Read command: NEW_PARTITION
parted_server: command_new_partition()
parted_server: Note =dev=sda as changed
parted_server: Opening outfifo
parted_server: Expected: part_type file_system id position length
parted_server: Line 1801. CRITICAL ERROR!!! EXITING.
/lib/partman/free_space/50new/do_option: error_handler: exception with type
/lib/partman/free_space/50new/do_option: error_handler: reading message
/lib/partman/free_space/50new/do_option: error_handler: reading options
/lib/partman/free_space/50new/do_option: IN: unhandled







This has been the partman of ubuntu:

parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 428
parted_server: Opening infifo
/lib/partman/free_space/50new/do_option: IN: NEW_PARTITION =[COLOR="Red"]dev=sda Logical ext2 137970846720-145069263359 Beginning 7098000000[/COLOR]
parted_server: Read command: NEW_PARTITION
parted_server: command_new_partition()
parted_server: Note =dev=sda as changed
parted_server: Opening outfifo
parted_server: requested partition with type Logical
parted_server: requested partition with file system ext2
parted_server: OUT: OK
parted_server: OUT: 12 137970878976-145069263359 7098384384 logical ext2 /dev/sda12
The difference is iam not getting the "Logical" variable, while creating the new partition. can any body tell me, where i have to rectify, for this problem?

and my mtab file is

/dev/sda12 / ext3 rw,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/dev/hda /media/cdrom0 iso9660 ro 0 0
/dev/loop0 /rofs squashfs ro 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
/dev/sda1 /mnt/disk[sda1] ext3 rw 0 0
/dev/sda2 /mnt/disk[sda2] ext3 rw 0 0
/dev/sda6 /mnt/disk[sda6] ext3 rw 0 0
/dev/sda7 /mnt/disk[sda7] ext3 rw 0 0
/dev/sda8 /mnt/disk[sda8] ext3 rw 0 0
/dev/sda9 /mnt/disk[sda9] ext3 rw 0 0
/dev/sda10 /mnt/disk[sda10] ext3 rw 0 0
/dev/sda11 /mnt/disk[sda11] ext3 rw 0 0
/dev/sda12 /mnt/disk[sda12] ext3 rw 0 0

and ubuntu mtab file is 

proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.20-15-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.20-15-generic/volatile tmpfs rw,mode=0755 0 0
/dev/bus/usb /proc/bus/usb none rw,bind 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/disk[sda1] ext3 rw,noexec,nosuid,nodev 0 0

 root filesystem of my live sits 
on /dev/sda12 / ext3 rw,errors=remount-ro 0 0 (anyone, tell me what might be the problem?)[IMG]http://usera.imagecave.com/padmanabhanj/Screenshot-2.png[/IMG][IMG]http://usera.imagecave.com/padmanabhanj/Screenshot-3.png[/IMG]

---

### Post by Sef on 2007-12-26
Closed. [Double Post.]("http://ubuntuforums.org/showthread.php?t=650339")

---

