---
title: "Boot Selection...GONE!"
date: 2008-01-14
forum: General Help
---

### Post by Shaibani on 2008-01-14
Hi guys!

I have XP and Ubuntu and I set XP to boot after 10 seconds(at the boot selection screen). Now when I start my computer, I don't get to select what to boot up from its just XP! :( How do I get the boot selection back!?!

---

### Post by taurus on 2008-01-14
You mean the GRUB menu.  Do you see it if you pres Esc?

---

### Post by NilsE on 2008-01-14
Have you tried hitting esc during that 10 seconds? and if so do you see the choices for XP and Ubuntu?

---

### Post by Shaibani on 2008-01-16
Yeah, I've tried that. It doesn't work :(:mad:

---

### Post by louieb on 2008-01-16
Get either [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html") or [Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs") to view /boot/grub/menu.lst from XP. If you can't figure out how to fix it post it here.

---

### Post by hesterd666 on 2008-01-16
This happens in two ways for me.
1) I have a removable HDD set up so I can switch between Windows and Ubuntu. To cut the story short the BIOS is looking in the wrong HDD for the boot record so just change the boot priority so that the hard drive you placed the boot loader on is on top.
2) When I install and Ubuntu or Windows after each other (not in any order really) and its a case of the boot record being overridden. So I place the windows CD in and restore the master boot record (I cant remember now off the top of my head but the MS website should tell you.

Sorry if this isn't applicable to you.
Thanks
---
hesterd666

---

### Post by Shaibani on 2008-01-18
> **louieb said:**
> Get either [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html") or [Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs") to view /boot/grub/menu.lst from XP. If you can't figure out how to fix it post it here.

I downloaded it, and installed it and went to /boot/grub/menu.lst, what next?:confused:

---

### Post by louieb on 2008-01-18
Copy and paste /boot/grub/menu.lst in your next post.

Just wondering did you install XP before after you installed Ubuntu?

---

### Post by Shaibani on 2008-01-19
> **louieb said:**
> Copy and paste /boot/grub/menu.lst in your next post.

Just wondering did you install XP before after you installed Ubuntu?

Yes I did.


[HTML]# menu.lst - See: grub(8), info grub, update-grub(8)
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
default		4

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
# kopt=root=UUID=adaf0524-d131-46ac-adcc-006f61adb14e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=adaf0524-d131-46ac-adcc-006f61adb14e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=adaf0524-d131-46ac-adcc-006f61adb14e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

[/HTML]

---

### Post by c0met on 2008-01-19
Before getting into the code and stuff, it might be easiest if you downloaded a bootable ISO for the program called SuperGrub. Burn this to a CD and then boot your system from this CD. It will give you options for...

    * making your win(dows) drive bootable
    * making your linux drive bootable
    * setting your system up for a dual boot

If you have Windows on one drive and Linux on the other, then you simply need to choose the dual boot option and it will setup the Grub menu for you so that you can select which operating system to boot into.

This is a great little program to have on hand. It's got me out of a few tight spots. It doesn't always solve the problem but it's worth a try. You can download the ISO from...

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by louieb on 2008-01-19
> **c0met said:**
> ...downloaded a bootable ISO for the program called SuperGrub...
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I think c0met is right. Your Grub menu is set up to display for 10 seconds - then boot to XP.  The answer to my last question wasn't clear, but it looks like you installed XP after installing Ubuntu and now the XP boot loader is pointed to by the MBR code. The super grub disk can change it to point to the Grub boot loader.
[IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by Shaibani on 2008-01-19
Ok, the grub menu is back:) BUT when I choose Ubuntu it says "partion cannot be mounted"

---

### Post by c0met on 2008-01-19
As Iouieb says, I think you have overwritten GRUB in the MBR. This happens when Windows is installed after Ubuntu. It can be corrected. If you go to the below link, about 1/3 of the way down the page you'll see a heading called **Reinstalling GRUB to the MBR**. Boot from the Ubuntu Live CD and follow the instructions from that heading onwards.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

---

### Post by Shaibani on 2008-01-30
> **c0met said:**
> As Iouieb says, I think you have overwritten GRUB in the MBR. This happens when Windows is installed after Ubuntu. It can be corrected. If you go to the below link, about 1/3 of the way down the page you'll see a heading called **Reinstalling GRUB to the MBR**. Boot from the Ubuntu Live CD and follow the instructions from that heading onwards.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

I did that, I just have 1 partion, its 32 gb(both of my drives) sorry if my dumbness is bothering you but I'm new to all this partioning stuff, and ubuntu.

---

### Post by Shaibani on 2008-02-07
Umm...Hello?:confused:

---

### Post by macogw on 2008-02-07
You have just one partition?  You can't have just one partition with 2 OSes installed.  Do you have 2 disks and each has one partition?  Did you use the whole disk when you installed Windows?  If so, you just blew away your Ubuntu install.

---

### Post by Shaibani on 2008-02-10
> **macogw said:**
> You have just one partition?  You can't have just one partition with 2 OSes installed.  Do you have 2 disks and each has one partition?  Did you use the whole disk when you installed Windows?  If so, you just blew away your Ubuntu install.

Oh, I guess I gotta un-install Ubuntu then...how do i do that?

---

### Post by Shaibani on 2008-02-18
Ummm...anyone there? :confused:

---

### Post by danwood76 on 2008-02-18
What he meant is that its impossible to install 2 OS on the same partition.
So if you installed ubuntu then installed XP over the top ubuntu is gone (unless you partitioned the drive correctly and installed XP on another partition)

---

### Post by Shaibani on 2008-02-20
> **danwood76 said:**
> What he meant is that its impossible to install 2 OS on the same partition.
So if you installed ubuntu then installed XP over the top ubuntu is gone (unless you partitioned the drive correctly and installed XP on another partition)

I know what he meant! But how do I uninstall ubuntu from XP?

---

### Post by sammydee on 2008-02-20
I don't think you understand Shaibani

From what I can gather from this thread, you first installed ubuntu. Then you installed xp. You must have selected an option on the xp install cd that formatted (erased) the entire drive. This wiped ubuntu off completely, and totally replaced it with xp.

Is this what happened?

You can install ubuntu again by repartitioning the drive, adding an extra partition and installing ubuntu to there. If you like, we can talk you through this process.

---

### Post by Shaibani on 2008-03-02
ok get this:

I did NOT install ubuntu first. it was XP then i installed ubuntu by popping in the live cd and doing the installation thing! and btw "talk me thru" the process!!!

---

