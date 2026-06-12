---
title: "GRUB error 21, changing motherboard gigabyte 965pds3 -&gt; ASUS 95B Deluxe-WiFi AP (IDE)"
date: 2007-09-04
forum: General Help
---

### Post by hecato on 2007-09-04
Hi there people, I have burned my motherboard **gigabyte 965PDS3** IIRC with some coca... all the other parts are OK, thus I have now an **ASUS 95B Deluxe-WiFi AP**.

The problem is that starting the system give

> GRUB Loading
Stage 1.5

GRUB Loading, please wait...
Error 21


That apparently mean that GRUB cant find the "name" or something like that of the HD or partition from BIOS... and the solution that I found more fine was 1 about modify GRUB.lst file for launch the correct name of partition....


Now Im on LiveCD Ubuntu 7.04, I have added getdeb and installed hardinfo, and I have this report [http://tyoc.nonlogic.org/hardinfo.html](http://tyoc.nonlogic.org/hardinfo.html) thought I see isnt complete, because there is no list of geforce 8800GTS... and the problem.. is in that report watch the **IDE Disks** section


Also gparted in the live CD cant list any IDE... the list is clear/clean... or there is no items in the list of gparted.


If you need the output of a command, please say me.

---

### Post by nitro_n2o on 2007-09-04
this might solve your problem 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by hecato on 2007-09-04
I will try that next... I have regenerate the [hardinfo.html]("http://tyoc.nonlogic.org/hardinfo.html") because I see that doing somethings I have disconnect the IDE that time... thus that is why isnt listed there, only the DVD... now my IDE is listed

> SCSI Disks HL-DT-ST DVDRAM GSA-H42N
ATA HDS722580VLAT20


Thanks for the info, I guess that is what I need recover grub.. to be able to boot in the correct way the installation that I already have working.

---

### Post by hecato on 2007-09-04
OK, here is some of the output...

> grub> root <TAB>
Error 1: Filename must be either an absolute pathname or blocklist

grub> find /boot/grub/stage1
 (hd0,5)
And mount actually return
> ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
** /dev/sda6 on /media/disk type reiserfs** (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/disk-1 type ntfs (rw,nosuid,nodev,umask=222,utf8)
sda6 is where I have my **/** mount point.

---

### Post by hecato on 2007-09-05
Hey people, I still have the error, I hae followed the howto recover GRUB from CD
...

Im using only LiveCD, I can see my HD, tomorrow I will try again the 3 or more different "methods" to recover GRUB, but Im getting nowhere, and I dont see that doing them a second time will work except only if I have failed to follow the instructions.

Perhaps the only way is to install in some free space I have another time Ubuntu??? Thought... that *really isn't* a solution to the problem... is only a work around.

---

### Post by hecato on 2007-09-05
This is what Im trying now...

> ubuntu@ubuntu:~$ df /media/disk-1/boot/grub/
S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/sda6             31229312  22058588   9170724  71% /media/disk-1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/disk-1/ /dev/sda6 
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /media/disk-1//boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/media/disk-1//boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /media/disk-1//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
ubuntu@ubuntu:~$ 


---

### Post by hecato on 2007-09-06
With the bad news that I have reinstalled from the LiveCD Ubuntu in a free space that I hold for add some extra OS and I have used it for Ubuntu now, but after installation, I restart PC and the error is still there

The screen of confirmation of Ubuntu installation show something like:
>  Idioma: Spanish
 Distribución del teclado: Spain
 Nombre completo: asdf
 Nombre de usuario: asdf
 Localización: America/Mexico_City


Se escribirán en los discos todos los cambios indicados a continuación si
continúa. Si no lo hace podrá hacer cambios manualmente.

AVISO: Esta operación destruirá todos los datos que existan en las
particiones que haya eliminado así como en aquellas particiones que se vayan
a formatear.

Se formatearán las siguientes particiones:
 partición #5 de SCSI3 (0,1,0) (sda) como intercambio
 partición #7 de SCSI3 (0,1,0) (sda) como reiserfs



After installation the device.map in that partition show
> (hd0)    /dev/sda
(hd1)    /dev/sdb

And the menu.lst show
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=a04435cd-3650-4960-bde3-8a973436f25c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

## ## End Default Options ##

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=a04435cd-3650-4960-bde3-8a973436f25c ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=a04435cd-3650-4960-bde3-8a973436f25c ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,6)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, kernel 2.6.20-16-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=3ff92915-8365-414f-a717-713c0b37a958 ro quiet splash 
initrd        /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=3ff92915-8365-414f-a717-713c0b37a958 ro single 
initrd        /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, kernel 2.6.20-15-generic (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=3ff92915-8365-414f-a717-713c0b37a958 ro quiet splash 
initrd        /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=3ff92915-8365-414f-a717-713c0b37a958 ro single 
initrd        /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu, memtest86+ (on /dev/sda6)
root        (hd0,5)
kernel        /boot/memtest86+.bin  
savedefault
boot

But I still geting error 21 of GRUB...

I dont know if I need some extra things?? like a jmicron driver or something like that... ¿? :S

I have readed that knopixx can boot directly an HD??? I will see if this is another option... (shame on me)

---

### Post by hecato on 2007-09-07
I have installed a boot manager called "smart boot manager" and this 1 has let me boot the Win partition (which I dont use for nothing more than play), when trying to boot the partition with Ubuntu, GRUB return again the same error 21 at stage 1.5.

Is definetely thus a problem about GRUB and the name of the HD or somehting like that, because I was able to reinstall in the free space of my disk Ubuntu 7.04 and the installation was sucessfull, also the LiveCD work OK with the sound and wireless...

---

### Post by logos34 on 2007-09-07
You might want to post your fdisk.

**sudo fdisk -l** (lowercase L)

Looks like grub is trying to boot the newer (reinstall) Ubuntu on sda7 (hd0,6). 

Can you boot this install
> 
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title Ubuntu, kernel 2.6.20-16-generic (on /dev/sda6)
root (hd0,5)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=3ff92915-8365-414f-a717-713c0b37a958 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
savedefault
boot

?

---

### Post by gnuskool on 2007-09-07
[Here]("http://users.bigpond.net.au/hermanzone/p15.htm#21") is a swiss-army knife to Grub

---

### Post by hecato on 2007-09-07
First a correction, I see that I put 95b and is P5B.

Thx for the link, I have know before a little that was about names that BIOS give to harddrives.

Sorry, I delete the other extra partition with the new GRUB installed before read your post about fidisk -l...

> ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       10011    49697077+   5  Extendida
/dev/sda5            3825        4015     1534176   82  Linux swap / Solaris
/dev/sda6            4016        7903    31230328+  83  Linux

smart boot manager let launch the windows partition, there is also listed the linux partition... when I launch it from the menu, I get the same error 21 in stage 1.5.

In the mean time I have done the following (and I know before hand that it will fail)

> ubuntu@ubuntu:/media/disk-1$ df /media/disk-
disk-1/ disk-2/ 
ubuntu@ubuntu:/media/disk-1$ ***df /media/disk-1/boot/***
S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/sda6             31229312  22058584   9170728  71% /media/disk-1
ubuntu@ubuntu:/media/disk-1$ ***sudo grub-install --root-directory=/media/disk-1/ /dev/sda6 ***
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /media/disk-1//boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/media/disk-1//boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /media/disk-1//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sdaAnd I have attach the files in /media/disk-1/boot/grub/ after that grub install
, I know my installation is there... but I dont see how to get it back... I know is something about device.map or menu.lst, but I dont know exactly what is...

Also I dont know if something like this matther???? [http://www.jmicron.com/Support_FAQ.html](http://www.jmicron.com/Support_FAQ.html)

---

### Post by hecato on 2007-09-07
I have gparted LiveCD and this is the info I have collected with it...


It contain a screenshot of gparted, gparted_details.html that is a "check" of the partition, and also a log of a run of test disck with "search more deep at teh end" or some like that.

---

### Post by logos34 on 2007-09-08
Well, there's certainly no shortage of bugs associated with that JMicron controller (more [here]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=jmicron+&orderby=-importance&search=Search&field.status%3Alist=New&field.status%3Alist=Incomplete&field.status%3Alist=Confirmed&field.status%3Alist=Triaged&field.status%3Alist=In+Progress&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package="))--it's probably the most notorious piece of hardware in recent memory (for ubuntu linux users at least).  But as of the 2.6.20 kernel the problems have been fixed or don't apply in your case.  The ubuntu install goes fine, and you can even boot into windows using SBM.  But grub just refuses to boot anything, despite reinstalling from the live cd to the MBR *and *the bootsector of root partition ('grub-install.../dev/sda6'). You've even reinstalled ubuntu into the empty space (sda7) and still won't work.  Could be a problem with just grub, or the filesystem type, or the partition type.  

Here's what I'd try:

1. Check your Bios hard disk detect settings.  Make sure it's set for '[auto]', not '[user]', chs, LBA, etc.  While you're there check that any [MBR write-protect/antivirus feature]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect") is disabled.  (although if this was the problem I wouldn't imagine you see any mention of Grub at all on the startup screen)
2.  Get [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") and see if it will boot your root partition sda6, and windows as well.
3.  Maybe it's having a problem with the fact that root is on a **logical** partition and/or Reiserfs.  Backup your data, delete the extended partition sda2 and reinstall on a **primary** partition.  Change the fs type to **ext3**.  

Good luck.

EDIT: Looking back over all the info you've provided leads me to believe this has to be a Bios/motherboard issue.  Ubuntu worked with the previous board (well enough to amass 20 some gigs of data on sda6), and the hardware iis the same except for the board.  As I said, the JMircron controller caused lots of problems (with the 2.6.17 kernels).  What is the BIOS version/date?   Because if it came with a pre- v.0910 Bios (23/1/2007) and you haven't [flashed it with an update]("http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5B%20Deluxe/WiFi-AP"), then that would definitely be the problem. The older ones use JMB Bios 1.06.22.

> Q10:  Can JMicron chip support linux/grub boot?
Ans: Yes , JMB bios 1.06.53 or above already supported. 

---

