---
title: "Cannot Boot or Mount Ubuntu after Fedora Install"
date: 2008-06-09
forum: General Help
---

### Post by JustinAlf on 2008-06-09
I had a hard drive partitioned to 50 GB Ubuntu, and 20 Free.  I then installed Fedora on my 20 GB partition.  During installation, I set Ubuntu as my main boot, and told it to go to /dev/sda3, which is where it was.  Now, I can only boot from fedora.  I also cannot access the ubuntu partition from inside fedora, although it can see that it is 50 GB.  I need files off of this 50 GB partition.  Please help!!!!!!  Thanks.

---

### Post by JustinAlf on 2008-06-09
sorry for the quick bump, but I need help.

---

### Post by bingoUV on 2008-06-09
Boot into Fedora. do
```

su -
mkdir /media/Ubuntu
mount /dev/sda3 /media/Ubuntu
cd /media/Ubuntu

```

Read the files here. To be able to boot Ubuntu, 
```

cd /media/Ubuntu/boot/grub
su -
gedit menu.lst

```

Take the first entry, copy paste it in /boot/grub/grub.conf. Attach the files /media/Ubuntu/boot/grub/menu.lst and /boot/grub/grub.conf here if you have trouble.

---

### Post by JustinAlf on 2008-06-10
Thanks for the reply.  I am back and running on Ubuntu again.  For some reason, Fedora totally took over my grub, and wouldn't recognize Ubuntu.  I couldn't even mount ubuntu partition in Fedora.  So i installed another copy of ubuntu onto the first partition, then Grub returned to normal, and I fixed my problems that way.  But thank you so much for the reply.

---

### Post by blue_sun on 2008-12-17
I have the same problem as JustinAlf. I have Window XP on sda1, Ununtu 8.10 on sda2(/) and sda3(swap). Then I install Fedora 10 on sda4(extended), sda5(/). I cannot boot ubuntu. I try the code shown by bingoUV as follow

Boot into Fedora. do

Code:
su -
mkdir /media/Ubuntu
mount /dev/sda3 /media/Ubuntu
cd /media/UbuntuRead the files here. To be able to boot Ubuntu, 

Code:
cd /media/Ubuntu/boot/grub
su -
gedit menu.lst

However, it doesn't work. I didnt try the following staps cause I don't understand it.

"Take the first entry, copy paste it in /boot/grub/grub.conf. Attach the files /media/Ubuntu/boot/grub/menu.lst and /boot/grub/grub.conf here if you have trouble."

I need help. I am new to linux. Thank you!!!

---

### Post by caljohnsmith on 2008-12-17
Blue_sun, if you can open your Fedora's grub.conf file, then you can add an entry in it to load your Ubuntu's menu.lst. How about trying the following in Fedora:
```
su -
gedit /boot/grub/grub.conf
```
And then add at the bottom:
```
title Ubuntu Grub Menu
configfile (hd0,1)/boot/grub/menu.lst
```
Reboot, and then when you select "Ubuntu Grub Menu" from the Fedora Grub menu, you should get your Ubuntu Grub menu. How about giving that shot and let me know how it goes.

---

### Post by blue_sun on 2008-12-18
Hi caljohnsmith, I tried the code you provided. I can access Ubuntu Grub menu but when I boot ubuntu, it didn't work. Here is error message (Error 15:file not found) and when I boot ubuntu from fedora menu, it says "Error 13: Invalid or executable(unsupported format). What should I do next?

---

### Post by caljohnsmith on 2008-12-18
In order to get a clearer picture of your setup, how about doing the following while you are in Fedora:
```

su - 
wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be

---

### Post by blue_sun on 2008-12-18
Hi caljohnsmith,this code (wget 'http://home.comcast.net/~ubuntu_grub/boot_info.txt' && sh ./boot_info.txt) doesn't work. The terminal returned "bash: wget: command not found"

---

### Post by caljohnsmith on 2008-12-18
> **blue_sun said:**
> Hi caljohnsmith,this code (wget 'http://home.comcast.net/~ubuntu_grub/boot_info.txt' && sh ./boot_info.txt) doesn't work. The terminal returned "bash: wget: command not found"
OK, I didn't realize Fedora didn't have wget installed by default. How about instead right click on this link to the [boot_info_script.txt,]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") choose "save target as", save the script to your desktop, and run it with:
```
su -
cd /home/[COLOR="Blue"]<username>[/COLOR]/Desktop
sh boot_info_script.txt
```
And replace <username> with your username. See if you can get that to work, or let me know if you have problems again.

---

### Post by blue_sun on 2008-12-18
The terminal returned "Finished. The results are in the file boot_info_results.txt located in /home/visethso/Desktop". I tried "su - 
wget 'http://home.comcast.net/~ubuntu_grub/boot_info.txt' && sh ./boot_info.txt". Still didn't work.

---

### Post by blue_sun on 2008-12-18
sorry man, I just saw the file on the desktop.

No known boot loader is installed in the MBR of /dev/sda

sda1:
    File system:  Extended Partition

sda2:
    File system:  Extended Partition

sda3:
    File system:  Extended Partition

sda4:
    File system:  Extended Partition

sda5:
    File system:  Extended Partition


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8b1290e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   119539664    59769801    7  HPFS/NTFS
/dev/sda2       119539665   172987919    26724127+  83  Linux
/dev/sda3       172987920   176988104     2000092+  82  Linux swap / Solaris
/dev/sda4       176988105   234436544    28724220    5  Extended
/dev/sda5       176988168   234436544    28724188+  83  Linux
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=119539602, Id= 7, bootable
/dev/sda2 : start=119539665, size= 53448255, Id=83
/dev/sda3 : start=172987920, size=  4000185, Id=82
/dev/sda4 : start=176988105, size= 57448440, Id= 5
/dev/sda5 : start=176988168, size= 57448377, Id=83

StdErr Messages 

Unknown MBR on /dev/sda

00000000  eb 48 90 d0 bc 00 7c 8e  c0 8e d8 bf 1e 06 be 1e  |.H....|.........|
00000010  7c 50 57 b9 e2 01 f3 a4  b9 00 02 f3 ab cb 80 fa  ||PW.............|
00000020  8f 7e 02 b2 80 52 52 bb  94 07 8d af 2a 00 8a 46  |.~...RR.....*..F|
00000030  04 66 8b 7e 08 66 03 3e  b3 06 84 c0 74 0b 03 02  |.f.~.f.>....t...|
00000040  80 00 00 80 08 60 2a 0b  00 08 fa 90 90 f6 c2 80  |.....`*.........|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 f6 c2 80  |. ..@|<.t...R...|
00000070  74 54 b4 41 bb aa 55 cd  13 5a 52 72 49 81 fb 55  |tT.A..U..ZRrI..U|
00000080  aa 75 43 a0 41 7c 84 c0  75 05 83 e1 01 74 37 66  |.uC.A|..u....t7f|
00000090  8b 4c 10 be 05 7c c6 44  ff 01 66 8b 1e 44 7c c7  |.L...|.D..f..D|.|
000000a0  04 10 00 c7 44 02 01 00  66 89 5c 08 c7 44 06 00  |....D...f.\..D..|
000000b0  70 66 31 c0 89 44 04 66  89 44 0c b4 42 cd 13 72  |pf1..D.f.D..B..r|
000000c0  05 bb 00 70 eb 7d b4 08  cd 13 73 0a f6 c2 80 0f  |...p.}....s.....|
000000d0  84 f0 00 e9 8d 00 be 05  7c c6 44 ff 00 66 31 c0  |........|.D..f1.|
000000e0  88 f0 40 66 89 44 04 31  d2 88 ca c1 e2 02 88 e8  |..@f.D.1........|
000000f0  88 f4 40 89 44 08 31 c0  88 d0 c0 e8 02 66 89 04  |..@.D.1......f..|
00000100  66 a1 44 7c 66 31 d2 66  f7 34 88 54 0a 66 31 d2  |f.D|f1.f.4.T.f1.|
00000110  66 f7 74 04 88 54 0b 89  44 0c 3b 44 08 7d 3c 8a  |f.t..T..D.;D.}<.|
00000120  54 0d c0 e2 06 8a 4c 0a  fe c1 08 d1 8a 6c 0c 5a  |T.....L......l.Z|
00000130  8a 74 0b bb 00 70 8e c3  31 db b8 01 02 cd 13 72  |.t...p..1......r|
00000140  2a 8c c3 8e 06 48 7c 60  1e b9 00 01 8e db 31 f6  |*....H|`......1.|
00000150  31 ff fc f3 a5 1f 61 ff  26 42 7c be 7f 7d e8 40  |1.....a.&B|..}.@|
00000160  00 eb 0e be 84 7d e8 38  00 eb 06 be 8e 7d e8 30  |.....}.8.....}.0|
00000170  00 be 93 7d e8 2a 00 eb  fe 47 52 55 42 20 00 47  |...}.*...GRUB .G|
00000180  65 6f 6d 00 48 61 72 64  20 44 69 73 6b 00 52 65  |eom.Hard Disk.Re|
00000190  61 64 00 20 45 72 72 6f  72 00 bb 01 00 b4 0e cd  |ad. Error.......|
000001a0  10 ac 3c 00 75 f4 c3 00  00 00 00 00 00 00 00 00  |..<.u...........|
000001b0  00 00 00 00 00 00 00 00  0e 29 b1 e8 00 00 80 01  |.........)......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 92 07 20 07 00 fe  |......?..... ...|
000001d0  ff ff 83 fe ff ff d1 07  20 07 3f 8e 2f 03 00 fe  |........ .?./...|
000001e0  ff ff 82 fe ff ff 10 96  4f 0a b9 09 3d 00 00 fe  |........O...=...|
000001f0  ff ff 05 fe ff ff c9 9f  8c 0a f8 97 6c 03 55 aa  |............l.U.|
00000200

boot_info_script.txt: line 106: xxd: command not found
boot_info_script.txt: line 152: vol_id: command not found
boot_info_script.txt: line 152: vol_id: command not found
boot_info_script.txt: line 152: vol_id: command not found
boot_info_script.txt: line 152: vol_id: command not found
boot_info_script.txt: line 152: vol_id: command not found

---

### Post by blue_sun on 2008-12-18
Is it the right file?

---

### Post by caljohnsmith on 2008-12-18
OK, something didn't go right with the script on your setup for some reason. How about downloading the attached "script1.sh.txt" to your Fedora desktop and do:
```
su -
cd /home/[COLOR="Blue"]<username>[/COLOR]/Desktop
sh sript1.sh.txt
```
And replace <username> with your username. Please post the results.

---

### Post by blue_sun on 2008-12-18
Hi John, This is the result. What should I do next?





[visethso@localhost ~]$ su
Password: 
[root@localhost visethso]# cd /home/visethso/Desktop
[root@localhost Desktop]# sh sript1.sh.txt
sh: sript1.sh.txt: No such file or directory
[root@localhost Desktop]# sh script1.sh.txt
+ mount
+ grep ' / '
+ awk '{print $1}'
/dev/sda5
+ mkdir /mnt/sda2 /mnt/sda5
+ mount /dev/sda2 /mnt/sda2
+ mount /dev/sda5 /mnt/sda5
+ ls -l /mnt/sda2 /mnt/sda5 /mnt/sda2/boot /mnt/sda5/boot
/mnt/sda2:
total 84
drwxr-xr-x   2 root root  4096 2008-12-17 21:49 bin
drwxr-xr-x   3 root root  4096 2008-12-17 21:48 boot
lrwxrwxrwx   1 root root    11 2008-12-17 21:08 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-10-30 12:04 dev
drwxr-xr-x 122 root root  4096 2008-12-17 21:53 etc
drwxr-xr-x   3 root root  4096 2008-12-17 21:20 home
lrwxrwxrwx   1 root root    32 2008-12-17 21:48 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root  4096 2008-12-17 21:49 lib
drwx------   2 root root 16384 2008-12-17 21:08 lost+found
drwxr-xr-x   3 root root  4096 2008-10-30 11:53 media
drwxr-xr-x   2 root root  4096 2008-10-21 01:27 mnt
drwxr-xr-x   2 root root  4096 2008-10-30 11:53 opt
drwxr-xr-x   2 root root  4096 2008-10-21 01:27 proc
drwxr-xr-x   5 root root  4096 2008-12-17 21:53 root
drwxr-xr-x   2 root root  4096 2008-12-17 21:49 sbin
drwxr-xr-x   2 root root  4096 2008-10-30 11:53 srv
drwxr-xr-x   2 root root  4096 2008-10-15 02:02 sys
drwxrwxrwt  10 root root  4096 2008-12-17 21:53 tmp
drwxr-xr-x  11 root root  4096 2008-10-30 11:58 usr
drwxr-xr-x  15 root root  4096 2008-10-30 12:12 var
lrwxrwxrwx   1 root root    29 2008-12-17 21:48 vmlinuz -> boot/vmlinuz-2.6.27-7-generic

/mnt/sda2/boot:
total 11936
-rw-r--r-- 1 root root  507665 2008-10-24 21:29 abi-2.6.27-7-generic
-rw-r--r-- 1 root root   91364 2008-10-24 21:29 config-2.6.27-7-generic
drwxr-xr-x 2 root root    4096 2008-12-17 21:48 grub
-rw-r--r-- 1 root root 8175421 2008-12-17 21:48 initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root  124152 2008-09-12 08:11 memtest86+.bin
-rw-r--r-- 1 root root 1029585 2008-10-24 21:29 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root    1073 2008-10-24 21:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root 2244272 2008-10-24 21:29 vmlinuz-2.6.27-7-generic

/mnt/sda5:
total 116
drwxr-xr-x   2 root root  4096 2008-11-20 08:14 bin
drwxr-xr-x   4 root root  4096 2008-12-18 11:08 boot
drwxr-xr-x   3 root root  4096 2008-11-20 08:13 dev
drwxr-xr-x 103 root root 12288 2008-12-20 04:17 etc
drwxr-xr-x   3 root root  4096 2008-12-18 11:17 home
drwxr-xr-x  16 root root 12288 2008-11-20 08:14 lib
drwx------   2 root root 16384 2008-11-20 08:10 lost+found
drwxr-xr-x   3 root root  4096 2008-12-20 04:05 media
drwxr-xr-x   4 root root  4096 2008-12-20 04:17 mnt
drwxr-xr-x   2 root root  4096 2008-09-06 22:13 opt
drwxr-xr-x   2 root root  4096 2008-11-20 08:10 proc
drwxr-x---   5 root root  4096 2008-12-20 04:16 root
drwxr-xr-x   2 root root 12288 2008-11-20 08:16 sbin
drwxr-xr-x   2 root root  4096 2008-11-20 08:18 selinux
drwxr-xr-x   2 root root  4096 2008-09-06 22:13 srv
drwxr-xr-x   2 root root  4096 2008-11-20 08:10 sys
drwxrwxrwt  19 root root  4096 2008-12-20 04:16 tmp
drwxr-xr-x  13 root root  4096 2008-11-20 08:12 usr
drwxr-xr-x  20 root root  4096 2008-11-20 08:16 var

/mnt/sda5/boot:
total 6920
-rw-r--r-- 1 root root   90889 2008-11-19 06:30 config-2.6.27.5-117.fc10.i686
drwxr-xr-x 3 root root    4096 2008-11-20 08:12 efi
drwxr-xr-x 2 root root    4096 2008-12-19 22:30 grub
-rw------- 1 root root 3179670 2008-12-18 11:08 initrd-2.6.27.5-117.fc10.i686.img
-rw-r--r-- 1 root root  112076 2008-04-04 10:16 memtest86+-2.01
-rw-r--r-- 1 root root 1089949 2008-11-19 06:30 System.map-2.6.27.5-117.fc10.i686
-rwxr-xr-x 1 root root 2570960 2008-11-19 06:30 vmlinuz-2.6.27.5-117.fc10.i686
+ cat /mnt/sda2/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2c8c8217-baf7-4e46-b70a-f919532d866c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2c8c8217-baf7-4e46-b70a-f919532d866c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2c8c8217-baf7-4e46-b70a-f919532d866c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2c8c8217-baf7-4e46-b70a-f919532d866c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2c8c8217-baf7-4e46-b70a-f919532d866c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2c8c8217-baf7-4e46-b70a-f919532d866c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2c8c8217-baf7-4e46-b70a-f919532d866c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

+ cat /mnt/sda5/boot/grub/menu.lst
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,4)
#          kernel /boot/vmlinuz-version ro root=/dev/sda5
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=1
timeout=20
splashimage=(hd0,4)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,4)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=fa1e586c-39a2-46a9-965f-b57df84d9ea3 rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.i686.img
title Window XP
	rootnoverify (hd0,0)
	chainloader +1
title Ubuntu
	rootnoverify (hd0,1)
	chainloader +1

+ cat /mnt/sda2/boot/grub/grub.conf
cat: /mnt/sda2/boot/grub/grub.conf: No such file or directory
+ cat /mnt/sda5/boot/grub/grub.conf
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,4)
#          kernel /boot/vmlinuz-version ro root=/dev/sda5
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=1
timeout=20
splashimage=(hd0,4)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,4)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=fa1e586c-39a2-46a9-965f-b57df84d9ea3 rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.i686.img
title Window XP
	rootnoverify (hd0,0)
	chainloader +1
title Ubuntu
	rootnoverify (hd0,1)
	chainloader +1

+ xxd -l 2 -p /dev/sda
script1.sh.txt: line 13: xxd: command not found
+ xxd -s 1049 -l 2 -p /dev/sda
script1.sh.txt: line 14: xxd: command not found
[root@localhost Desktop]#

---

### Post by caljohnsmith on 2008-12-18
OK, how about doing:
```
su -
grub
grub> root (hd0,1)
grub> setup (hd0,1)
grub> quit
```
And please post the output of the above commands. Next reboot, and choose Ubuntu from your Fedora menu. Let me know if you get a Grub error or exactly what happens.

---

### Post by blue_sun on 2008-12-19
This is the result, John. How can I become a sudoers file?

[visethso@localhost ~]$ sudo grub
[sudo] password for visethso: 
visethso is not in the sudoers file.  This incident will be reported.
[visethso@localhost ~]$ grub> root (hd0,1)
bash: syntax error near unexpected token `('
[visethso@localhost ~]$ grub> setup (hd0,1)
bash: syntax error near unexpected token `('
[visethso@localhost ~]$

---

### Post by caljohnsmith on 2008-12-19
Sorry about that, I forgot you don't have sudo in Fedora; I corrected my previous post. Please try again and post the output.

---

### Post by blue_sun on 2008-12-19
This is the output, John.

[visethso@localhost ~]$ su
Password: 
[root@localhost visethso]# grub
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename.]
grub>  root (hd0,1)
 root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83
grub> setup (hd0,1)
setup (hd0,1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,1) /boot/grub/stage2 p /boot/grub/grub.conf "... succeeded
Done.
grub> quit
quit
[root@localhost visethso]#

---

### Post by caljohnsmith on 2008-12-19
So did you try rebooting, and when you choose Ubuntu from your Fedora menu what happens?

---

### Post by blue_sun on 2008-12-19
This is the output when I select Ubuntu from Fedora menu.

[Minimal BASH-like line editing is supported. For the first word, Tab lists possible command completions. Anywhere else Tab lists the possible completions of a device/filename.]

grub>
#When I press Tab, I got the following#

Possible commands are: background blocklist boot border cat chainloader clear cmp color configfile debug displayapm displaymen embed find foreground fstest geometry halt help hide impsprobe initrd install ioprobe kernel lock makeactive map md5crypt module modulenounzip paper partnew parttype password pause print quiet read reboot root rootnoverify savedefault serial setkey setup shade splash image terminal terminfo testload testvbe unhide uppermen uuid vbeprobe viewport

---

### Post by caljohnsmith on 2008-12-19
OK, when you try to boot Ubuntu again from the Fedora menu and get the Grub command line, try:
```
grub> blocklist (hd0,1)/boot/grub/menu.lst
grub> cat (hd0,1)/boot/grub/menu.lst
```
And please let me know the first numbers that the first blocklist command returns, and also let me know if the cat command above shows the Ubuntu menu.lst. 

Lastly, the script you previously ran that didn't work has been updated, so please download again the "[boot_info_script.txt]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt")" file to your desktop (make sure to save it to your desktop with that file name), and try the following while you are in Fedora:
```
su -
cd /home/visethso/Desktop
bash boot_info_script.txt
```
And then copy/paste the contents of the "boot_info_results.txt" file on your desktop to your next post. We can work from there.

---

### Post by blue_sun on 2008-12-19
This is the results.

grub> blocklist (hd0,1)/boot/grub/menu.lst
(hd0,1)6372640+10

grub> cat (hd0,1)/boot/grub/menu.lst

#menu.lst-see: grub(8), info grub, Update-grub(8)
               grub-install(8), grub-floppy(8), grub-md5-crypt, /usr/shar/doc/grub
               and /usr/share/doc/grub-doc/.
.......
.......

Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #2 for its boot files.

sda1:
    File system:  ntfs
    Boot sector  type:  Unknown
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 63.
    Operating System: XP
    Boot files/directories present:  /boot.ini /bootmgr /ntldr /NTDETECT.COM /Boot

sda2:
    File system:  ext3
    Boot sector  type:  Grub
    Boot sector  info:  Grub is installed to the boot sector of /dev/sda2 and looks at sector 126011345 of the same hard drive for the stage2 file. (a stage2 file is at this location on /dev/sda) and on partition #1 for menu.lst.
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sda3:
    File system:  swap

sda4:
    File system:  Extended Partition

sda5:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot/grub/grub.conf /boot /boot/grub


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8b1290e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   119539664    59769801    7  HPFS/NTFS
/dev/sda2       119539665   172987919    26724127+  83  Linux
/dev/sda3       172987920   176988104     2000092+  82  Linux swap / Solaris
/dev/sda4       176988105   234436544    28724220    5  Extended
/dev/sda5       176988168   234436544    28724188+  83  Linux
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=119539602, Id= 7, bootable
/dev/sda2 : start=119539665, size= 53448255, Id=83
/dev/sda3 : start=172987920, size=  4000185, Id=82
/dev/sda4 : start=176988105, size= 57448440, Id= 5
/dev/sda5 : start=176988168, size= 57448377, Id=83

sda1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


sda1/Boot

total 492
drwxrwxrwx 1 root root   4096 2008-04-19 16:08 .
drwxrwxrwx 1 root root   8192 2008-12-21 10:45 ..
-rwxrwxrwx 1 root root  16384 2008-05-06 19:43 BCD
-rwxrwxrwx 1 root root  13312 2008-05-06 19:40 BCD.LOG
-rwxrwxrwx 1 root root  65536 2008-04-20 17:18 BootStat.dat
drwxrwxrwx 1 root root      0 2008-04-19 16:08 cs-CZ
drwxrwxrwx 1 root root      0 2008-04-19 16:08 da-DK
drwxrwxrwx 1 root root      0 2008-04-19 16:08 de-DE
drwxrwxrwx 1 root root      0 2008-04-19 16:08 el-GR
drwxrwxrwx 1 root root      0 2008-04-19 16:08 en-US
drwxrwxrwx 1 root root      0 2008-04-19 16:08 es-ES
drwxrwxrwx 1 root root      0 2008-04-19 16:08 fi-FI
drwxrwxrwx 1 root root   4096 2008-04-19 16:08 Fonts
drwxrwxrwx 1 root root      0 2008-04-19 16:08 fr-FR
drwxrwxrwx 1 root root      0 2008-04-19 16:08 hu-HU
drwxrwxrwx 1 root root      0 2008-04-19 16:08 it-IT
drwxrwxrwx 1 root root      0 2008-04-19 16:08 ja-JP
drwxrwxrwx 1 root root      0 2008-04-19 16:08 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 22:51 memtest.exe
drwxrwxrwx 1 root root      0 2008-04-19 16:08 nb-NO
drwxrwxrwx 1 root root      0 2008-04-19 16:08 nl-NL
drwxrwxrwx 1 root root      0 2008-04-19 16:08 pl-PL
drwxrwxrwx 1 root root      0 2008-04-19 16:08 pt-BR
drwxrwxrwx 1 root root      0 2008-04-19 16:08 pt-PT
drwxrwxrwx 1 root root      0 2008-04-19 16:08 ru-RU
drwxrwxrwx 1 root root      0 2008-04-19 16:08 sv-SE
drwxrwxrwx 1 root root      0 2008-04-19 16:08 tr-TR
drwxrwxrwx 1 root root      0 2008-04-19 16:08 zh-CN
drwxrwxrwx 1 root root      0 2008-04-19 16:08 zh-HK
drwxrwxrwx 1 root root      0 2008-04-19 16:08 zh-TW

sda2/boot/grub/menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2c8c8217-baf7-4e46-b70a-f919532d866c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2c8c8217-baf7-4e46-b70a-f919532d866c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2c8c8217-baf7-4e46-b70a-f919532d866c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2c8c8217-baf7-4e46-b70a-f919532d866c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2c8c8217-baf7-4e46-b70a-f919532d866c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2c8c8217-baf7-4e46-b70a-f919532d866c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2c8c8217-baf7-4e46-b70a-f919532d866c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


sda2/boot

total 11944
drwxr-xr-x  3 root root    4096 2008-12-17 21:48 .
drwxr-xr-x 20 root root    4096 2008-12-17 21:48 ..
-rw-r--r--  1 root root  507665 2008-10-24 21:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 21:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-17 21:48 grub
-rw-r--r--  1 root root 8175421 2008-12-17 21:48 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-12 08:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 21:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 21:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 21:29 vmlinuz-2.6.27-7-generic

sda2/boot/grub

total 216
drwxr-xr-x 2 root root   4096 2008-12-17 21:48 .
drwxr-xr-x 3 root root   4096 2008-12-17 21:48 ..
-rw-r--r-- 1 root root    197 2008-12-17 21:48 default
-rw-r--r-- 1 root root     15 2008-12-17 21:48 device.map
-rw-r--r-- 1 root root   8108 2008-12-17 21:48 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-17 21:48 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-17 21:48 installed-version
-rw-r--r-- 1 root root   8712 2008-12-17 21:48 jfs_stage1_5
-rw-r--r-- 1 root root   4619 2008-12-17 21:48 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-17 21:48 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-17 21:48 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-17 21:48 stage1
-rw-r--r-- 1 root root 121460 2008-12-17 21:48 stage2
-rw-r--r-- 1 root root   9556 2008-12-17 21:48 xfs_stage1_5

sda5/boot/grub/menu.lst

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,4)
#          kernel /boot/vmlinuz-version ro root=/dev/sda5
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=1
timeout=20
splashimage=(hd0,4)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,4)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=fa1e586c-39a2-46a9-965f-b57df84d9ea3 rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.i686.img
title Window XP
	rootnoverify (hd0,0)
	chainloader +1
title Ubuntu
	rootnoverify (hd0,1)
	chainloader +1


sda5/boot/grub/grub.conf

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,4)
#          kernel /boot/vmlinuz-version ro root=/dev/sda5
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=1
timeout=20
splashimage=(hd0,4)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,4)
	kernel /boot/vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=fa1e586c-39a2-46a9-965f-b57df84d9ea3 rhgb quiet
	initrd /boot/initrd-2.6.27.5-117.fc10.i686.img
title Window XP
	rootnoverify (hd0,0)
	chainloader +1
title Ubuntu
	rootnoverify (hd0,1)
	chainloader +1


sda5/boot

total 6932
drwxr-xr-x  4 root root    4096 2008-12-18 11:08 .
drwxr-xr-x 22 root root    4096 2008-12-21 03:06 ..
-rw-r--r--  1 root root   90889 2008-11-19 06:30 config-2.6.27.5-117.fc10.i686
drwxr-xr-x  3 root root    4096 2008-11-20 08:12 efi
drwxr-xr-x  2 root root    4096 2008-12-19 22:30 grub
-rw-------  1 root root 3179670 2008-12-18 11:08 initrd-2.6.27.5-117.fc10.i686.img
-rw-r--r--  1 root root  112076 2008-04-04 10:16 memtest86+-2.01
-rw-r--r--  1 root root 1089949 2008-11-19 06:30 System.map-2.6.27.5-117.fc10.i686
-rwxr-xr-x  1 root root 2570960 2008-11-19 06:30 vmlinuz-2.6.27.5-117.fc10.i686

sda5/boot/grub

total 316
drwxr-xr-x 2 root root   4096 2008-12-19 22:30 .
drwxr-xr-x 4 root root   4096 2008-12-18 11:08 ..
-rw-r--r-- 1 root root     63 2008-12-18 11:08 device.map
-rw-r--r-- 1 root root  11736 2008-12-18 11:08 e2fs_stage1_5
-rw-r--r-- 1 root root  11512 2008-12-18 11:08 fat_stage1_5
-rw-r--r-- 1 root root  10744 2008-12-18 11:08 ffs_stage1_5
-rw------- 1 root root    765 2008-12-19 22:30 grub.conf
-rw------- 1 root root    825 2008-12-19 08:08 grub.conf~
-rw-r--r-- 1 root root  10736 2008-12-18 11:08 iso9660_stage1_5
-rw-r--r-- 1 root root  12328 2008-12-18 11:08 jfs_stage1_5
lrwxrwxrwx 1 root root     11 2008-12-18 11:08 menu.lst -> ./grub.conf
-rw------- 1 root root    764 2008-12-18 12:06 menu.lst~
-rw-r--r-- 1 root root  10968 2008-12-18 11:08 minix_stage1_5
-rw-r--r-- 1 root root  13360 2008-12-18 11:08 reiserfs_stage1_5
-rw-r--r-- 1 root root  40685 2008-10-25 03:40 splash.xpm.gz
-rw-r--r-- 1 root root    512 2008-12-18 11:08 stage1
-rw-r--r-- 1 root root 111004 2008-12-18 11:08 stage2
-rw-r--r-- 1 root root  11008 2008-12-18 11:08 ufs2_stage1_5
-rw-r--r-- 1 root root  10344 2008-12-18 11:08 vstafs_stage1_5
-rw-r--r-- 1 root root  12984 2008-12-18 11:08 xfs_stage1_5

StdErr Messages 

hexdump: stdin: Illegal seek.
boot_info_script.txt: line 201: [: =: unary operator expected

---

### Post by caljohnsmith on 2008-12-19
Something doesn't make sense, because according to the script you ran, Grub on start up is using the menu.lst in your Ubuntu sda2 partition. Did you run any Grub commands since your last few posts? Just to double-check, how about doing:
```
su -
hexdump -s 1049 -n 2 -e '"%x\n"' /dev/sda
```
And if that returns "ff01", then Grub is using the menu.lst in sda2. When you boot, is the first option you see in the Grub menu "Ubuntu 8.10, kernel 2.6.27-7-generic"? I don't get it, because you have been booting into Fedora, right? Also, your stage2 in sda2 points to the first sda1 partition for the menu.lst instead of sda2 like it should, so that would explain why the Ubuntu menu.lst doesn't load at least from that aspect. 

How about when you are in Fedora still, try:
```
su -
mount /dev/sda2 /mnt/sda2
cp /mnt/sda2/usr/lib/grub/*/stage2 /mnt/sda2/boot/grub
```
Then reboot, and again choose Ubuntu from the Fedora boot menu, if the Fedora boot menu is what you get on start up. I think you will be able to load the Ubuntu menu.lst, but let me know what happens.

---

### Post by blue_sun on 2008-12-21
I am not sure about this "Ubuntu 8.10, kernel 2.6.27-7-generic" because I deleted the code that add Ubuntu grub menu to fedora menu but it looks like the right one. 

[visethso@localhost ~]$ su
Password: 
[root@localhost visethso]# hexdump -s 1049 -n 2 -e '"%x\n"' /dev/sda
ff01
[root@localhost visethso]# su
[root@localhost visethso]# mount /dev/sda2 /mnt/sda2
[root@localhost visethso]# cp /mnt/sda2/usr/lib/grub/*/stage2 /mnt/sda2/boot/grub
cp: overwrite `/mnt/sda2/boot/grub/stage2'? y
[root@localhost visethso]# 


After rebooting I got the following:

[Minimal BASH-like line editing is supported. For the first word, Tab lists possible command completions. Anywhere else Tab lists the possible completions of a device/filename.]

grub>


Did I not install more than one linux distributions in a proper way? or Is it because of my laptop hardware? My laptop medel is ASUS Z53Eseries.
If it is because of the former reason. Can you give me a guide to install multiple linux distributions? I will reinstall everything. Thank you!!!

---

### Post by caljohnsmith on 2008-12-21
> **blue_sun said:**
> 
Did I not install more than one linux distributions in a proper way? or Is it because of my laptop hardware? My laptop medel is ASUS Z53Eseries.
If it is because of the former reason. Can you give me a guide to install multiple linux distributions? I will reinstall everything. Thank you!!!
If you want to reinstall everything, my recommendation would be to install Fedora first and let it install Grub to the MBR (the default option), and then install Ubuntu after that. Ubuntu will also by default install Grub to the MBR, so if you install Ubuntu after Fedora, then Ubuntu will be in charge of the booting process in the end. Then all you have to do to boot Fedora would be to add the following to your Ubuntu menu.lst:
```
title Fedora Grub Menu
root (hd0,4)
configfile /boot/grub/menu.lst
```
That assumes you install Fedora to sda5 again, which is (hd0,4) in Grub's world. How about trying that and let me know how it goes.

---

### Post by blue_sun on 2008-12-22
Thanks for your guide, John. Can you give me the code to access Ubuntu menu.lst file?

---

### Post by caljohnsmith on 2008-12-22
> **blue_sun said:**
> Thanks for your guide, John. Can you give me the code to access Ubuntu menu.lst file?
Sure, when you are in Ubuntu, open a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And that will open your menu.lst so you can edit it. Good luck and let me know how it goes.

---

### Post by blue_sun on 2008-12-23
Hi Jonh, I installed fedora and than Ubuntu. I got a nice result. Ubuntu is very friendly to fedora. It added fedora to its menu automatically. It worked smoothly. How about Mandriva and OpenSuse? Is ubuntu friendly to them? Thanks for your nice guide.

---

### Post by caljohnsmith on 2008-12-23
> **blue_sun said:**
> Hi Jonh, I installed fedora and than Ubuntu. I got a nice result. Ubuntu is very friendly to fedora. It added fedora to its menu automatically. It worked smoothly. How about Mandriva and OpenSuse? Is ubuntu friendly to them? Thanks for your nice guide.
If you install Mandriva or OpenSUSE after you've all ready installed Ubuntu, as you can probably guess, Ubuntu will not automatically detect them the next time you boot into Ubuntu and add them to your Grub's menu.lst for you. You can add them to your Ubuntu menu.lst by linking to their own menu.lst/grub.conf files, using the notation from post #26. :)

---

### Post by blue_sun on 2008-12-23
Last question, John.
I mean if I install Mendriva or OpenSuse instead of Fedora first then install Ubuntu. Does it work? But I got what you said I can install them after Ubuntu but I don't have to install their boot loader to MBR so that Ubuntu boot loader is kept the same, isn't it?

Merry Christmas. see you later:)

---

### Post by caljohnsmith on 2008-12-23
> **blue_sun said:**
> Last question, John.
I mean if I install Mendriva or OpenSuse instead of Fedora first then install Ubuntu. Does it work? But I got what you said I can install them after Ubuntu but I don't have to install their boot loader to MBR so that Ubuntu boot loader is kept the same, isn't it?

Merry Christmas. see you later:)
Yes, as far as I know, if you install Ubuntu after Mandriva/OpenSUSE, I don't think you will have any problems. And yes, if you install them after Ubuntu, make sure to install their boot loader to their partition boot sector, and not the MBR. Cheers and Merry Christmas to you too. :)

---

