---
title: "All UUIDs correct, but still have UUID error at startup"
date: 2008-03-01
forum: General Help
---

### Post by oliveri on 2008-03-01
I'm getting the /dev/disk/by-uuid/blahblahblah not found error at startup, so cannot boot.  The UUIDs for this partition show up as the same with volume_id, in /dev/disk/by-uuid/, in fstab, and in grub.  The parition is mountable and readable in the rescue system.  

Any ideas?

---

### Post by taurus on 2008-03-01
Instead of using root=UUID=blah_blah_blah in /boot/grub/menu.lst, would it boot if you go back to the old fashion way, root=/dev/sda1 (if /dev/sda1 is where root partition is)?

---

### Post by oliveri on 2008-03-01
I am trying to, but the terminal in rescue mode does not work! I can't get an editor I know to function.  This is really bad.

[https://bugs.launchpad.net/ubuntu/+source/rescue/+bug/35400](https://bugs.launchpad.net/ubuntu/+source/rescue/+bug/35400)

[http://ubuntuforums.org/showthread.php?t=79150](http://ubuntuforums.org/showthread.php?t=79150)

Unfortunately just resetting TERM does not work.

---

### Post by taurus on 2008-03-01
What editor are you talking about?  In a recovery mode, you cannot use gedit.  Instead, use nano or vi.

```
nano -Bw /boot/grub/menu.lst
```
Save the changes with <Ctrl>o and exit with <Ctrl>x.

---

### Post by oliveri on 2008-03-01
Thank you for the help, but neither vi nor nano work in the rescue shell.  These are the ones I know.  The one I don't know and may be forced to figure out is ed.

Incidentally, just using the command you provided generates an error that bterm can't be opened.  The terminal has to be set to vt100 for nano to open.  When it does, the text displayed is scrambled and the cursor does not actually appear where the text is being edited.  That is to say, edits that appear to be made in one location actually happen somewhere else.

---

### Post by louieb on 2008-03-01
When GRUB come up try editing the entry there.  Just highlight it and press e to edit. and try the edit  taurus   mentioned. Then press enter and press b to boot. 

It just a temporary change. To make it permanent  you'll have to make the same change in /boot/grub/menu.lst.

---

### Post by taurus on 2008-03-01
You can still edit /boot/grub/menu.lst on your harddrive from the LiveCD, if you still have that handy.  Boot your machine with the LiveCD and open a terminal and run

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```
Assuming that /dev/sda1 is where your / is and you don't have a separate /boot partition.

---

### Post by oliveri on 2008-03-01
I have reset the entries in /boot/grub/menu.lst and /etc/fstab to point to /dev/sdb1 rather than the UUID for /, and for /dev/sdb5 for swap.  Now, kernel panic ("divide by zero").

My fstab file (copied by hand and hopefully accurate):

```
proc     /proc     proc     defaults     0     0
/dev/sdb1     /     ext3     defaults,errors=remount--ro     0     1
/dev/sdb5     none     swap     sw     0     0
/dev/hda     /media/cdrom0     udf,iso9660     user,noauto     0     0
```

I ran grub-update at some point early on in this process; I'm wondering if that has somehow spread errors around.

---

### Post by louieb on 2008-03-01
may be a typo
but
```

/dev/sdb1  / ext3   defaults,errors=**[COLOR=Red]remount--ro[/COLOR]**  0 1 

```should be **remount-ro**

---

### Post by oliveri on 2008-03-01
Thank you, but no, that wasn't it.  I found this:

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

which ominously says:

> Directly using /dev/hd* or /dev/sd* is no longer supported

I don't know if there is some indirect way of using /dev/sd* that remains.

---

### Post by dcstar on 2008-03-01
> **oliveri said:**
> I'm getting the /dev/disk/by-uuid/blahblahblah not found error at startup, so cannot boot.  The UUIDs for this partition show up as the same with volume_id, in /dev/disk/by-uuid/, in fstab, and in grub.  The parition is mountable and readable in the rescue system.  

Any ideas?

Boot off the Live CD, and open a terminal and post the output of the following:
```
ls -al /dev/disk/by-uuid
```
and the contents of the /etc/fstab on your hard disk.

---

### Post by oliveri on 2008-03-02
> **dcstar said:**
> Boot off the Live CD, and open a terminal and post the output of the following:
```
ls -al /dev/disk/by-uuid
```
and the contents of the /etc/fstab on your hard disk.

I restored the system back to the state it was in before I started editing fstab and menu.lst.  Here's the fstab and the contents of by-uuid:

```
drwxr-xr-x 2 root root 100 Mar  2 02:07 .
drwxr-xr-x 5 root root 100 Mar  2 02:07 ..
lrwxrwxrwx 1 root root  10 Mar  2 02:07 9dd4a0f3-a308-41bd-a3a6-31bad5ef0519 -> ../../sdb5
lrwxrwxrwx 1 root root  10 Mar  2 02:07 A40065B300658CDC -> ../../sda1
lrwxrwxrwx 1 root root  10 Mar  2 02:07 d22a6db5-c1eb-4c4d-b589-92e30d67af4b -> ../../sdb1
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=d22a6db5-c1eb-4c4d-b589-92e30d67af4b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=9dd4a0f3-a308-41bd-a3a6-31bad5ef0519 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Here are the outputs of blkid and vol_id /dev/sdb1

```
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=d22a6db5-c1eb-4c4d-b589-92e30d67af4b
ID_FS_UUID_ENC=d22a6db5-c1eb-4c4d-b589-92e30d67af4b
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
```

```
/dev/sda1: TYPE="ntfs" UUID="A40065B300658CDC" 
/dev/sdb1: UUID="d22a6db5-c1eb-4c4d-b589-92e30d67af4b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="9dd4a0f3-a308-41bd-a3a6-31bad5ef0519" 
```

And here is the menu.lst file.
```
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=d22a6db5-c1eb-4c4d-b589-92e30d67af4b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu 7.10, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d22a6db5-c1eb-4c4d-b589-92e30d67af4b ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d22a6db5-c1eb-4c4d-b589-92e30d67af4b ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by plucky on 2008-03-03
oliveri,

 My 2cents

Your system has Windows XP on /dev/sda1,yet there is no entry for it in /etc/fstab.
Could this be the problem?

Good luck

---

### Post by froy02 on 2008-03-03
```
proc     /proc     proc     defaults     0     0
/dev/sdb1     /     ext3     defaults,errors=remount--ro     0     1
/dev/sdb5     none     swap     sw     0     0
/dev/hda     /media/cdrom0     udf,iso9660     user,noauto     0     0
```

Just wondering why your cdrom is mounted /dev/hda?
Should it not be /dev/scd0?

---

### Post by oliveri on 2008-03-03
It's the first and only IDE drive in the system, and IDE drives are hda, hdb no matter whether they are HDs CDROMS.  scd was for SCSI drives or SCSI emulation, which is nowadays is no longer an issue, I think?

Anyhow, not connnected as far as I can see with the UUID problem.

---

### Post by oliveri on 2008-03-03
> **plucky said:**
> 
Your system has Windows XP on /dev/sda1,yet there is no entry for it in /etc/fstab.
Could this be the problem?


No, as the linux system doesn't mount sda1.  sda1 sits there quietly until I decide I need to play Portal or something.  But I appreciate you wanting to help.

---

### Post by oliveri on 2008-03-06
This is what happened:  more recent Ubuntu kernels have difficulty with SATA drives running under IDE emulation.  I had the SATA drive with the system on it set to IDE emulation in the BIOS --probably because I didn't know what AHCI was and didn't care.   AHCI turns out to be native SATA. 

A kernel update and turning AHCI on in the BIOS has everything running again.

---

