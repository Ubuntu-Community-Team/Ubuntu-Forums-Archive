---
title: "Help Mounting &quot;WINDOWS&quot;"
date: 2015-07-09
forum: General Help
---

### Post by noah23 on 2015-07-09
[SIZE=3]Hello, im failry new to Ubantu.Ive been having problems with Windows 8.Everytime i try to log in it freezes. Im trying to use Ubantu to recover some of my files but , when i click on "WINDOWS" it gives me this error:[/SIZE][FONT=arial narrow][SIZE=1][/SIZE][/FONT][SIZE=3][/SIZE] Unable to access “WINDOWS” Error mounting /dev/sda4 at /media/ubuntu/WINDOWS: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda4" "/media/ubuntu/WINDOWS"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

[FONT=arial][SIZE=3]I typed fdisk -l and it came up as GPT type.[/SIZE][/FONT][SIZE=3][FONT=arial]Under sda1. Now when i type "fdisk -l" into the command lines it doesnt do anything beside show me a bunch of command for fdisk. I tried to mount using "mount -t ntsf-3g /dev/sda/media/disk -o force[/FONT][/SIZE]" [FONT=arial][SIZE=3]and itll show a bunch of commands for mount wtf and it says i need to specify the name so ill type "/dev/sda1" and itll say:Permission Denied. HELP  please and thank you for reading this if you did god bless.[/SIZE][/FONT]


PS: i running it off a live usb im usuing the most recent desktop version14.04 or something. Also my motherboard is uefi boot. Another string f command i used that i forgot described my drive as "ntfs"

---

### Post by Vladlenin5000 on 2015-07-09
Hi and welcome.

You can't use Linux like in the "old times" for that purpose because Windows 8 by default keep its partitions hibernated and therefore they can't be mounted by another OS.
The error message told you just that.

PS - Please avoid "religious imbued expressions" like "god bless". I know you mean good but that's offensive for many people. I'm one of them.

---

### Post by grahammechanical on 2015-07-09
There might be some advice here that could help you

[http://www.webupd8.org/2015/06/workarounds-for-not-being-able-to-mount.html](http://www.webupd8.org/2015/06/workarounds-for-not-being-able-to-mount.html)

Regards

[URL="http://www.webupd8.org/2015/06/workarounds-for-not-being-able-to-mount.html"]
[/URL]

---

