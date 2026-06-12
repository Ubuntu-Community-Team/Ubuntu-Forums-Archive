---
title: "SD Card mounting read-only (on only one machine)"
date: 2015-06-09
forum: General Help
---

### Post by timothylegg on 2015-06-09
Hello,

I'm having a terrible problem.  I have a 32GB SD card that I need to attach for extra storage for an SDK I'm wanting to install.

I fdisk'd it with a type 83 partition and then I ran "mke2fs -j -L android /dev/sdc1".   All seemed to go well until I went to mount it.  It seemed to mount as a read-only filesystem, which was highly annoying and useless.

I have two machines, I attached it to a separate machine and formatted it using an identical method.  I manually mounted it and used touch to create a file and if seemed to write it.

I take the card back to the original machine and attach it and I get a rather verbose error.
[INDENT]
Error mounting /dev/sdc1 at /media/legg/android: Command-line `mount -t "ext3" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc1" "/media/legg/android"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/INDENT]

When I try manually mounting...

[INDENT]
# mount /dev/sdc1 temp
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/INDENT]


I know the drive works because I successfully backed up all the data from the card using the same card slot half an hour ago.  Any ideas why it's doing this? 

Tim Legg

---

### Post by drpjkurian on 2015-06-10
Hi
See this link [here]("https://www.linuxquestions.org/questions/linux-software-2/unable-to-mount-former-raid-hard-drive-4175523996/"), and [here]("https://bbs.archlinux.org/viewtopic.php?id=121577") It may help

---

