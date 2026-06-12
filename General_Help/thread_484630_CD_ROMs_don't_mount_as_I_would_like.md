---
title: "CD ROMs don't mount as I would like"
date: 2007-06-26
forum: General Help
---

### Post by Nem Chua on 2007-06-26
Hello all,

I have a problem with Nautilus / Feisty Fawn: the CD drive only recognizes correctly a disk when it was present at boot-up.

On the desktop, it won't disappear if I eject, won't change names if I burn it, and any drive I insert afterwards is referred with the same name. :-k

I could have limited success with the command line but i actually have to reboot if I want to burn two different disks.

Did you ever come across this behaviour? What should I do?

Thanks for your support :) (or grief in case... :( )

Nem Chua

---

### Post by Nem Chua on 2007-07-05
It looks like it's gonna be grief.

I purged and reinstalled nautilus, no change.

I reinstalled gdm (how knows...?), but no change.

Could it be a cofiguration file I left on the old /home partition I kept from Dapper? I looked through *every* dot-file without finding any one that could evoke the CD driver.

Any one got any ideas

(I am ready to listen even to dumb ideas at this point)

I have a HP nx6310 (Intel Core Duo), with a @%^& TSSTcorp DVD/CDRW driver. It works fine under Windows, fine with Dapper --but I tasted the speed of Feisty with the Core duo now, no way i get back to Dapper!.

---

Here is a recap', if someone wants to help an Ubuntero alone in the Mekong delta, Vietnam. ;)

Watch out, big recap. I tried topost all the info I could grab.

```
~$ cat /etc/fstab | grep scd
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
~$ 
~$ wodim --devices
Beginning native device scan. This may take a while if devices are busy...
wodim: Overview of accessible drives (1 found) :
----------------------------------------------------------------------
0    dev='/dev/sr0'   rwrw-- :  'TSSTcorp'  'CDW/DVD TS-L462C'
----------------------------------------------------------------------
~$ 
~$ ls /dev |grep scd
lrwxrwxrwx 1 root root           4 2007-07-06 01:50 sr0 -> scd0
brw-rw---- 1 root cdrom    11,   0 2007-07-06 01:50 scd0
lrwxrwxrwx 1 root root           4 2007-07-06 01:50 dvd -> scd0
lrwxrwxrwx 1 root root           4 2007-07-06 01:50 cdrw -> scd0
lrwxrwxrwx 1 root root           4 2007-07-06 01:50 cdrom -> scd0
~$ 
~$ cdrecord -scanbus
scsibus0:
        0,0,0     0) 'TSSTcorp' 'CDW/DVD TS-L462C' 'HP10' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
~$ 
~$ cat /var/log/messages | grep -i CD-ROM
Jun 30 19:48:05 benFF kernel: [    4.376413] scsi 0:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
Jun 30 19:48:05 benFF kernel: [    6.999776] Uniform CD-ROM driver Revision: 3.20
Jul  2 07:11:59 benFF kernel: [    4.253113] scsi 0:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
Jul  2 07:11:59 benFF kernel: [    6.872867] Uniform CD-ROM driver Revision: 3.20
Jul  3 07:42:56 benFF kernel: [    6.676557] scsi 4:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
Jul  3 07:42:56 benFF kernel: [   16.421612] Uniform CD-ROM driver Revision: 3.20
Jul  3 10:03:32 benFF kernel: [    4.105220] scsi 0:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
Jul  3 10:03:32 benFF kernel: [    6.812796] Uniform CD-ROM driver Revision: 3.20
Jul  3 22:15:37 benFF kernel: [    4.170898] scsi 0:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
Jul  3 22:15:37 benFF kernel: [    4.187148] Uniform CD-ROM driver Revision: 3.20
Jul  4 12:04:30 benFF kernel: [    4.166687] scsi 0:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
Jul  4 12:04:30 benFF kernel: [    6.774362] Uniform CD-ROM driver Revision: 3.20
Jul  4 14:15:55 benFF kernel: [    4.005077] scsi 0:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
Jul  4 14:15:55 benFF kernel: [    6.732410] Uniform CD-ROM driver Revision: 3.20
Jul  5 17:07:29 benFF kernel: [    6.601305] scsi 4:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
Jul  5 17:07:29 benFF kernel: [   16.929301] Uniform CD-ROM driver Revision: 3.20
Jul  5 17:51:28 benFF kernel: [    6.357293] scsi 4:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
Jul  5 17:51:28 benFF kernel: [   16.633938] Uniform CD-ROM driver Revision: 3.20
Jul  5 18:12:46 benFF kernel: [    3.729671] scsi 0:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
Jul  5 18:12:46 benFF kernel: [    6.852561] Uniform CD-ROM driver Revision: 3.20
Jul  5 18:50:26 benFF kernel: [    4.252597] scsi 0:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
Jul  5 18:50:26 benFF kernel: [    6.824043] Uniform CD-ROM driver Revision: 3.20
~$ 
~$ cat /proc/sys/dev/cdrom/info
CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:             sr0
drive speed:            24
drive # of slots:       1
Can close tray:         1
Can open tray:          1
Can lock tray:          1
Can change speed:       1
Can select disk:        0
Can read multisession:  1
Can read MCN:           1
Reports media changed:  1
Can play audio:         1
Can write CD-R:         1
Can write CD-RW:        1
Can read DVD:           1
Can write DVD-R:        0
Can write DVD-RAM:      0
Can read MRW:           1
Can write MRW:          1
Can write RAM:          1


~$ lsmod | grep -i cdrom
cdrom                  37664  1 sr_mod

```

and mtab (with a liveCD in the drive: nada):
```
:~$ cat /etc/mtab
/dev/sda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/sda6 /home ext3 rw 0 0
/dev/sda2 /media/sda2 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda1 /windows vfat rw,utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
```

If I insert a blank CD ROM i get:```

$ sudo mount -a
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by minhtrietle on 2007-08-01
I got the same problem too man, maybe the magnetic field in the Delta is too great and it causes the damage to both the ubuntu OS and your optical drives.

just move to the beta or alpha areas, the field should be weaker.

may the force be with you, sour-ham.

---

### Post by fredj on 2007-08-01
Try to find updated firmware for your tsst drive and install it.

---

