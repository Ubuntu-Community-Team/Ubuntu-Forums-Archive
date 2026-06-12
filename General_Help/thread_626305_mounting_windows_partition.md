---
title: "mounting windows partition"
date: 2007-11-28
forum: General Help
---

### Post by miteshanand1729 on 2007-11-28
I have dual boot system with xp and gusty.Earlier xp partition was mounted in gusty but after update yesterday my xp mounted partition gone and i can able to mount it again.My fstab is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=aa99fd68-d93f-4aa6-8a1c-622d4994ff93 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=D490E35290E33A1E /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=40784B26784B1A54 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=22C893AEC8937F2B /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=cfcc37ac-d9a5-49a7-a569-c460cca30430 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0




Please tell me how to remount it again....???

---

### Post by sirgogo on 2007-11-28
You can do it using the GUI rather than the terminal, sometimes.

Does your disk show up in Places --> Computer ? Or the Filesystem --> media --> ?

Let me know, because you can just right click and click mount if that stuff works.

---

### Post by miteshanand1729 on 2007-11-28
> **sirgogo said:**
> You can do it using the GUI rather than the terminal, sometimes.

Does your disk show up in Places --> Computer ? Or the Filesystem --> media --> ?

Let me know, because you can just right click and click mount if that stuff works.
no... in Places --> Computer ? Or the Filesystem --> media --> no option of mount on right click...

---

### Post by teryowen on 2007-11-29
Have you tried just the good old mount commands

sudo mount /dev/sda1 /media/sda1
sudo mount /dev/sda5 /media/sda5
sudo mount /dev/sda6 /media/sda6

---

### Post by miteshanand1729 on 2007-11-29
solved... after couple times of restarting and loging in both xp and ubuntu it sloved.Now xp partition is mounting automatically even my fstab is same as earliar ... i don't know how... thanx for help...

---

### Post by namanbagga on 2007-11-29
[FONT="Arial"][SIZE="5"]Gutsy has NTFS writing,thus you need to shut-down windows properly to detect your NTFS partition.I'm sure you would have hibernated or would have shut Windows down improperly[/SIZE][/FONT]

---

