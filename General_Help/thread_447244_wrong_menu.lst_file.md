---
title: "wrong menu.lst file?"
date: 2007-05-17
forum: General Help
---

### Post by raybaron on 2007-05-17
I've tried booting several times and end up getting dumped into the Busy Box ash shell as a few others on here. I looked at zenigata.log ind it is complaining about "Cannot find Host Folder , "Check boot parameters", etc.... I've tried installing on both my C: and D:  partitions in a dual boot with XP on c: and Vista on D: with the sanme results. I'm usin c:\grldr.mbr="Ubuntu" in XP's c:\boot.ini file and copied both grldr and menu.lst to the root of both of the c: & D: partitions. I put 7.04's grldr.mbr file in c: . The menu.lst file I'm using in the root directories looks good and is readable, however when I look in C:\wubi\boot\grub, the menu.lst file is much different. Here they are:

=================================================================
And, the c:\ and d:\menu.lst files (as configured  by wubi):

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
timeout        0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

## Pretty colours
#color cyan/blue white/blue

#### KERNEL PARAMETERS ####

# the /folder/path paramater must be matched in the following 3 lines:
#
#find --set-root /folder/path/linux
#kernel /folder/path/linux find=/folder/path/linux
#initrd /folder/path/linux
#
#you must replace /folder/path with the path where the files where installed
#do not use the same folder name on different partitions

## To specify the ISO (otherwise the first one in the folder will be used)
#setup_iso=setup.iso

## To specify the root harddisk image(otherwise root.img is assumed)
#root_virtual_disk=system.virtual.disk

## To specify the home harddisk image (otherwise home.virtual.disk is assumed)
#home_virtual_disk=home.virtual.disk

## To specify the swap harddisk image (otherwise swap.virtual.disk is assumed)
#home_virtual_disk=swap.virtual.disk

## To specify extra harddisk image (otherwise extra.virtual.disk is assumed)
#extra_virtual_disk=extra.virtual.disk

## Debug
#pause_for_debug debug

#### MENU ITEMS BELOW HERE ####

title Ubuntu
find --set-root --ignore-floppies /wubi/boot/grub/menu.lst
configfile /wubi/boot/grub/menu.lst

==================================================

c:\wubi\boot\grub\menu.lst file(as installed by wubu):


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=find=/wubi/boot/linux ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux

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

title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux quiet ro
initrd /wubi/boot/initrd
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot

======================================
Evidently, something is wrong somewhere. Why are the 2 files so different? Where can I read up on this stuff?I thought that this would be pretty much turnkey  but I need more help in setting up my system to boot other than from the Live CD.

Any and all help would be appreciatted.

As soon as I can locate where I copied the zenigata.log file from Ubuntu, I'll post it here. Riught now I'm copying over 5000 MP3's from one drive to another and cannot reboot my swystem into the "Busy Box" to determine where I copied the file. I searched through windows but in Linux I copied it to the "host" directory and evidently that is inside one of the virtual drives.  Is there some way I can copy files from within the shell to the NTFS file system in Windows so I can print see it outside of Ubuntu?
thx,
Ray

---

### Post by ago on 2007-05-18
Try to uninstall and install again. It should be c:\grldr="Ubuntu".

---

### Post by ecology2007 on 2007-05-18
The menu.lst are different because they don t have the same purpose. The first one calls the second one.You do not need to alter any of the menu.lst unless you know what you are doing.
Ago is right. The following is wrong i assume you wrote this manually. It should be **c:\grldr="Ubuntu"**
**I'm usin c:\grldr.mbr="Ubuntu" in XP's c:\boot.ini file and copied both grldr and menu.lst to the root of both of the c: & D: partitions.**
But if you get to the busy box, you have no problem of bootloader at all.

Where is XP ?
Where is Vista ?
Did you install wubi from vista or xp ?
And give any relevant detail you can think of about your hardware configuration.

---

### Post by raybaron on 2007-05-19
Hi!

XP in on C: and Vista on D: . I unstalled while running XP on the first partition on both the  XP partion ad then the xp partition but with  the same results.  I never installed from Vista. At this point I copied the \wubi directory to both partitionds but to no avail- nsame results..   I'm using a Gateway 650ROG laptop with a 120 GB hard drive split into 2 partitions and fortmated with NTFS. I  had set the line c:\grldr="Ububntu" and had thru 2 menus to get the system to boot, the  option I have currently referencing mbr allows me to get thing going thru the first Windows menu instead of 2 levels of menus. I have a good copy of zenigata.log but cannot read it from outside of BusyBox. I had copied it to the host directory whichbcontains files in what appears to be an abbreviated copy of my Vista root directory but from XP or Vista I cannot see the zenigata.log file I had coped there while Ubuntu was running. While inBusy Box It clearly shows my error saying I have the wrong boot parameters setting up /dev/sda1 as the /host and shows several failed attempts to set the 
mntpoint= /host then it quits after several test and attempts at this throughou tthe booting process which seems to take foever. At one poinyt it tries /dev/sda5 which I have no idea what it is.

Is there a way of coping the zenigatalog  file out to Windows so I can copy  and paste it up here for you guys to take a look at? Its quit large and I'm not up to taking pictures of it with my digital camera.

BTW, what is the exact boot sequence of a "normal" working wubi system with XP?. I mean what menu is displayed first, what shound I select and what can i expect next, etc?.

Need massive help in Phsadelphia, PA. This is worth a few beers for the winning solution. Still no boot other than the live CD :(
thx,
Ray

---

### Post by ecology2007 on 2007-05-19
You must have a wubi folder on only one of your drives. 
The logs are in wubi/logs.
If the install does not complete at once at first boot, you need to reinstall wubi from wubi.exe.

I suggest you copy the iso in wubi/install in the same folder as wubi-... . exe then
-run wubi.exe, select uninstall.
-run wubi.exe, look at the advanced settings, but don't change them, and complete the process.
-look at /wubi folder, check that the disks in wubi/disks are correct filesizes.
-check that the iso is in wubi/install
-check that you have c:\ntldr; c:\boot.ini;c:\grldr;c:\menu.lst
Then reboot.

Post the logs here, try full reinstall and feel free to ask further informations.

---

### Post by robodesign on 2007-06-11
Hello guys!

I have three PCs. One has a native Ubuntu 7.04 installatio (no Windows on this one, only Linux), and the other two computers have Windows XP.

I am interested to install Ubuntu with Wubi on both of the other systems.

One of the systems is a test one - so I don't care if something goes wrong. The Pentium 4 only has a single SCSI HDD (20 GB, 6 GB free space, NTFS).

Wubi installation went smooth - no issues. **Boot.ini** was properly updated.

The **boot.ini** file contains the following Ubuntu line:**c:\grldr="Ubuntu"**

The **grldr** file exists in c:\.

Windows still boots properly - no errors.

When I select the "Ubuntu" option from the bootloader I the Linux kernel loads properly, no errors. But... after a few seconds I get the error "no block devices" - no other system activity. Weird.

So... I edited **c:\wubi\boot\grub\menu.lst** with Windows. I removed the "splash" and "quiet" options from the kernel arguments list for both of the kernels, "Ubuntu" and "Ubuntu (Original Kernel)". I also added a delay so I can see the grub menu list.

I rebooted and selected "Ubuntu" from the grub menu. Now I saw all the verbose details of the system boot.

I was glad to see no obvious errors: USBs were properly detected, the SCSI device was also detected (**/dev/sda1** and **/dev/sg1**), no ACPI errors, loop module was loaded, etc. The root file system was mounted. The scripts **init-premount** and **local-top** were ran with no errors.

Now the error: **"no block devices found"** after **"waiting for root file system"**. After a long delay i get dropped into the BusyBox shell. I looked into the **zenigata.log** and I saw the same errors as reported by **raybaron**.

Before BusyBox shows I also get the message **"check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev"**.

Any suggestions?

I used the **wubi7.04-test3.exe** installer, the Ubuntu 7.04 flavour.

---

