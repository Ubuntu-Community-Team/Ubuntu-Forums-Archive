---
title: "Problem with grub2 | unknown filesystem, grub rescue"
date: 2013-10-23
forum: General Help
---

### Post by nike992 on 2013-10-23
hi all, my english is bad , but i think we can understand.

I have dual boot with Ubuntu 11.10 and Windows 7 .

I can't mount partition in Live mode.

I lost grub2 on start, and i get a message:  
```
error: unkown filesystem
grubrescue>
```

i try this commands, but for all "msdos" i get this message:
```
error: unkown filesystem
```
see picture[URL="http://fotkica.com/imgs3/1_62840295_Photo2420.jpg"]
http://fotkica.com/imgs3/1_62840295_Photo2420.jpg[/URL]

i was try ```
set boot=(hd0,msdos3)/boot/grub
``` , but error same again ```
error: unkown filesystem
```

When i try in live mode to return grub2, i write this ```
sudo fdisk -l
``` , and no read command.

I know my linux in instaled on sda3 partition, and i write this command
```
[COLOR=#000000][FONT=Monaco]sudo mount /dev/sda1 /mnt[/FONT][/COLOR]
```
and i get this answer
```
[COLOR=#000000][FONT=Monaco]mount: /dev/sda3: can't read superblock[/FONT][/COLOR]
```
and that's answer is same for all sda1/sda2/sda3/sda4/sda5


What to do?
please help me, i wan't to recover my data :(

Best regards, and thanks!

---

### Post by oldfred on 2013-10-23
First I might try this. Did you have any abnormal shutdown? Power failure or you turned off system while it was still writing?

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

