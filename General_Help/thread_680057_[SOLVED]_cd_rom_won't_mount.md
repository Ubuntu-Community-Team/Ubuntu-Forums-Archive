---
title: "[SOLVED] cd rom won't mount"
date: 2008-01-27
forum: General Help
---

### Post by phatjonny on 2008-01-27
I used a live CD to install Feisty 7.04 about six months ago.  I am very happy with everything.  Just the other day I tried to play a CD for the first time - nothing. :confused:

Obviously I don't need to use the CD ROM much, but it would be nice to have the option...

Cheers for the help..

---

### Post by Mikecore on 2008-01-27
when you say you tried to play a cd what do you mean? an audio.

---

### Post by phatjonny on 2008-01-28
yes an audio, nor could I access photographs from a disc

Thanks

---

### Post by Mikecore on 2008-01-28
open at terminal and type

```

sudo mount /media/cdrom

```

see if it mounts then. ( don't forget to insert a cdrom first )

---

### Post by phatjonny on 2008-01-29
Please have some patience with my ineptness!!!

I stuck a working CD-R in the drive, and here is the embarrassing bit, tried that command in both a terminal and then a console window.  I am a bit of a GUI guy and didn't really know which I should use (I 'm thinking terminal but then you were pretty clear about that!!) but will try again if given another pointer.

Both times it said there was no media in the drive...:(

---

### Post by phatjonny on 2008-01-30
Any ideas?

---

### Post by phatjonny on 2008-01-31
:confused:

---

### Post by polmir on 2008-01-31
put your cd with photographs to CD-rom
 type in terminal 
```
mount /media/cdrom
cd /media/cdrom
ls -l
```
please post out of command

---

### Post by phatjonny on 2008-02-13
Thanks for that Polmir,:)

This is what I got after running that command....

john@john-laptop:~$ mount /media/cdrom

mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

john@john-laptop:~$ cd /media/cdrom
john@john-laptop:/media/cdrom$ ls -l
total 0
john@john-laptop:/media/cdrom$ 


I'm afraid it is all double Dutch to me...:confused:

---

### Post by polmir on 2008-02-13
What is Your code page and locale?
What is code page name folder of cd (language)?
type in terminal
```
locale
```
```
cat /etc/fstab 
```
```
dmesg | tail
```
and post output of it.

---

### Post by phatjonny on 2008-02-16
Dear polmir,

Thanks again for your help.  Here is the output. I spent a year teaching in Bydgoszcz a long time ago... 

john@john-laptop:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
john@john-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=238cb44f-5014-4e75-8351-937545aae09f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d1c51a89-d1e4-47be-a6ac-481ecc22b2ee none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
john@john-laptop:~$ dmesg | tail
[ 6396.700000] hdc: drive not ready for command
[ 6396.700000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[ 6396.700000] ide: failed opcode was: unknown
[ 6396.700000] hdc: drive not ready for command
[ 6396.700000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[ 6396.700000] ide: failed opcode was: unknown
[ 6396.700000] hdc: drive not ready for command
[ 6396.700000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[ 6396.700000] ide: failed opcode was: unknown
[ 6396.700000] hdc: drive not ready for command
john@john-laptop:~$ 

Again it's all :confused: to me.

---

### Post by polmir on 2008-02-17
try this in Your /etc/fstab```

/dev/hdc   /media/cdrom0   udf,iso9660     user,noauto,utf8    0 0
```


edit ps:
I am from Kraków

---

### Post by phatjonny on 2008-02-17
[QUOTE=polmir;4347360]try this in Your /etc/fstab```

/dev/hdc   /media/cdrom0   udf,iso9660     user,noauto,utf8    0 0
```


OK, I found the above folder, should I just copy that bit of code and leave it in the folder too, or should I run it in a terminal window?

---

### Post by polmir on 2008-02-17
Add this red elements to Your fstab file.
```
sudo gedit /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0  0
# /dev/hda1
UUID=238cb44f-5014-4e75-8351-937545aae09f / ext3 defaults,errors=remount-ro  0 1
# /dev/hda5
UUID=d1c51a89-d1e4-47be-a6ac-481ecc22b2ee  none  swap sw 0 0
[COLOR="Red"]#[/COLOR]/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0  /media/floppy0  auto rw,user,noauto  0 0

[COLOR="Red"]/dev/hdc  /media/cdrom0   udf,iso9660  user,noauto,utf8 0 0
[/COLOR]
```

---

### Post by pemur1 on 2008-02-17
polmir, I'm hoping you can help me with this problem also. I'm using Ubuntu 7.10. This is what came up from your previous instructions:

root@XXXXXX-desktop:~# locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

root@XXXXXX-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bee1a3ca-7187-4e6e-8873-883d8e3e6433 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0c333f6c-a4fb-450b-973a-4bb478274173 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

root@XXXXXX-desktop:~# dmesg | tail
[   32.144000] NET: Registered protocol family 10
[   32.144000] lo: Disabled Privacy Extensions
[   32.148000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   42.264000] eth0: no IPv6 routers present
[  758.900000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  758.900000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  758.900000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  759.252000] [drm] Setting GART location based on new memory map
[  759.252000] [drm] Loading R200 Microcode
[  759.252000] [drm] writeback test succeeded in 1 usecs

---

### Post by polmir on 2008-02-18
```

#/etc/fstab:static file system information.
#
#<file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=bee1a3ca-7187-4e6e-8873-883d8e3e6433 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=0c333f6c-a4fb-450b-973a-4bb478274173 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto,exec,[COLOR="Red"]utf8[/COLOR] 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto,exec,[COLOR="Red"]utf8[/COLOR] 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0

```

---

### Post by addisor on 2008-02-18
Cheers man, just edited my etc/fstab to look at correct dvd drive access, now works again.

---

### Post by phatjonny on 2008-02-19
Dear Polmir

Have done as suggested and now the music CD is recognized and visible to the player, but it just won't play. Maybe I have a defective drive or something.

Still get told this when I try to mount a CD-ROM...

john@john-laptop:~$ sudo mount /media/cdrom
Password:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

john@john-laptop:~$ 



But hey, thanks for the help.:)

---

### Post by strabes on 2008-02-19
I'm surprised nobody has recommended that you upgrade to gutsy. Gutsy is far superior to feisty, especially in hardware.

---

### Post by phatjonny on 2008-02-20
That seems to have done the trick!

I just used the update manager to upgrade so I hope I have no future problems waiting for me...

Thanks to all for their help and suggestions

---

### Post by guga31bb on 2008-05-12
i'm running hardy with a similar problem. here's some output (there is currently a cd in the drive)

$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

$cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=749678b8-fb8b-437b-abc0-1a18a3394237 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d2ac1b27-8f4e-43cd-a578-2efa764f8123 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

$ dmesg | tail
[   88.416473] [drm] Setting GART location based on new memory map
[   88.416491] [drm] Loading R200 Microcode
[   88.416549] [drm] writeback test succeeded in 2 usecs
[  123.644448] NET: Registered protocol family 10
[  123.646082] lo: Disabled Privacy Extensions
[  123.648380] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.364525] eth1: no IPv6 routers present
[   53.494295] NET: Registered protocol family 17
[   53.885295] ieee80211_crypt: registered algorithm 'WEP'
[  163.242402] eth1: no IPv6 routers present

$ mount /media/cdrom0
mount: No medium found

i'd appreciate any help...

---

