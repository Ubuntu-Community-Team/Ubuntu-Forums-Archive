---
title: "[SOLVED] need some phone help"
date: 2008-06-04
forum: General Help
---

### Post by bj218 on 2008-06-04
Is their anyone that could help me via the telephone? I live in Palos Verdes California. I have just installed UBUNTU 8.04 and Linux MINT on two different hard drives and believe I have grub problem. I also have Windows XP on a third HD. My Phone is ***.  The name here is Bill and I am beginner on linux.

---

### Post by nick_h on 2008-06-04
What is your problem exactly?

Maybe someone can help on the forums.

---

### Post by bj218 on 2008-06-05
I have 3 HD's one has had win-xp on it for more than a year. Another one has had UBUNTU 8.04 on it for 1 month. The last one has had Linux Mint on it about for about a week. Before installing Mint I was runing win or ubuntu by changing the boot sequence in the cmos at start up. one HD is a PATA drive (Mint). The other 2 are SATA drives. When I setup the boot sequence as follows PATA,SATA1,SATA2 I get the following screen 2 options for Mint and 2 options for Ubuntu no mention of Win. If I select Ubuntu all goes well(noprob.) if I select Mint I get a Mint screen for a few seconds then all goes black. Could their be a problem with Grub and Win MBR?

---

### Post by VMC on 2008-06-05
> **bj218 said:**
> I have 3 HD's one has had win-xp on it for more than a year. Another one has had UBUNTU 8.04 on it for 1 month. The last one has had Linux Mint on it about for about a week. Before installing Mint I was runing win or ubuntu by changing the boot sequence in the cmos at start up. one HD is a PATA drive (Mint). The other 2 are SATA drives. When I setup the boot sequence as follows PATA,SATA1,SATA2 I get the following screen 2 options for Mint and 2 options for Ubuntu no mention of Win. If I select Ubuntu all goes well(noprob.) if I select Mint I get a Mint screen for a few seconds then all goes black. Could their be a problem with Grub and Win MBR?

I'm close enough to call you, but first lets see if we can solve your problem online , that way more people can benefit from it.

1 SATA HD = XP, 1 SATA HD = ubuntu, 1 IDE HD = Mint, correct> Thre all plugged in, but you switch them through the BIOS, coorect?

Can you leave them all connected through the BIOS and will they boot up that way. Why mess with the BIOS everything? 

output of '/etc/fstab' & '/boot/grub/menu.lst' would help. But then all would change when you enable/disable the hard drives through the BIOS.

I'm just guessing your afraid of tainting your hard drives that's why you have each OS on a separate hard drive. They could all happily coexists on one hard drive.

---

### Post by bj218 on 2008-06-06
I just spent about an hour trying to ans your response and when I tried to submit it said i was not authorized to do this. I think all my effort was lost!!        bj218

---

### Post by nick_h on 2008-06-06
Just type the following commands:
```
cat /etc/fstab
cat /boot/grub/menu.lst
```
Then just cut & paste the result into your post.
Surround the pasted text with code tags (# button in the advanced post section).

---

### Post by bj218 on 2008-06-07
About a year ago I had Ubuntu 7.04 and WIN XP on one drive and everything worked good for quite a while, then one day I must have done something wrong and ubuntu wiped out the whole drive. I then put each OS on a separatet drive and used the boot sequence to run the OS I wanted to use.
Today during bootup I pressed Pause and this is what I saw:
Auto Detecting Pri Master..IDE Hard Drive
Auto Detecting PriSlave.. CD/DVD ROM
Auto Detecting 3rd Master..IDE Hard Drive
Auto Detecting 4th Master..IDE Hard Drive
Pri Master: WDC 1000
PriSlave: DVDRW IDE16X
3rd Master:WDC 2500
4th Master:WDC 1600
Boot sequence was set as follows:
1st Boot Drive WDC 1000
2nd BootDrive WDC 2500
3rd Boot Drive WDC 1600

At bootup I get the following screen:
Linux Mint, kernel 2.6.22-14 generic
Linux Mint, kernel 2.6.22-14 generic (recovery mode)
Linux Mint, kernel memtest 86x
Other Operating Systems:
Ubuntu 8.04,kernel 2.6.24-17 generic (on/dev/sda1)
Ubuntu 8.04,kernel 2.6.24-17 (recovery mode) (on/dev/sda1)
NOTE: Down at the bottom of the screen are the following words:
Boot Options &#8220;root=dev/hda1 ro quiet splash

If I press enter on the first item I get the Linux Mint screen and it looks like it is loading
after about 10sec. The screen goes BLACK. All I can do after this is press the reset switch .
If I press enter on the second item I get lots of screens in just a few sec. The last item on this screen is &#8220;root@bj218-desktop:~#. If I press enter  at this time I get a few more screens then the system reboots.
If I press enter on Ubuntu it loads and works great.

The only way I can get to Win XP is to change the boot sequence.

---

### Post by nick_h on 2008-06-07
It looks like you are using a copy of grub installed by Linux Mint.  This has probably installed to the MBR of your first HDD (WDC 1000).

The first step to find out why Mint doesn't boot is to look in the /boot/grub/menu.lst file on the Mint drive.

You could add an entry for Windows.  The listing of /etc/fstab will help in writing the appropriate entry.

Finally, you will probably have a /boot/grub/menu.lst file on your Ubuntu drive which is not being used.  It may be easier to use your Ubuntu copy of grub.

---

### Post by bj218 on 2008-06-07
bill@bill-desktop:~$ cat /etc/fstab 
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/sda1 
UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac /               ext3    relatime,errors=remount-ro 0       1 
# /dev/sda3 
UUID=e2c057b4-5682-4789-b564-d2369e769c9e none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
bill@bill-desktop:~$ cat /boot/grub/menu.lst 
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
timeout		15 

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
# kopt=root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,0) 

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-18-generic 

title		Ubuntu 8.04, kernel 2.6.24-17-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-17-generic 

title		Ubuntu 8.04, kernel 2.6.24-16-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Ubuntu 8.04, memtest86+ 
root		(hd0,0) 
kernel		/boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda5 
title		Windows NT/2000/XP 
root		(hd0,4) 
savedefault 
makeactive 
chainloader	+1 

bill@bill-desktop:~$
NOTE:All of the above was taken from Ubuntu 8.04

---

### Post by nick_h on 2008-06-07
OK. That *menu.lst* file is the Ubuntu one that isn't being used at the moment.  It will load 3 Ubuntu kernel versions on partition 1 and Windows from an extended logical partition on the same drive (not your current configuration).

You could use the Ubuntu version of grub but first it would be a good idea to check that the UUIDs for the disks are the same.  To check this post the output of:
```
ls -al /dev/disk/by-uuid/
```

To find out where your Windows is installed type:
```
sudo fdisk -l
```
(unfortunately it was not listed in /etc/fstab)

---

### Post by bj218 on 2008-06-07
During installation of Mint HD partitions were set as follows:
/dev/hda                THIS IS WDC1000
    /dev/hda1 ext3
   /dev/hda2 swap
  /dev/hda3 fat32

/dev/sda                THIS IS WDC2500
   /dev/sda1 ext3
  /dev/sda3 swap
  /dev/sda5 fat32

/dev/sdb                THIS IS WDC1600
  /dev/sdb1 ntfs
 /dev/sdb5 fat32

---

### Post by nick_h on 2008-06-07
The first thing you have to do is decide which grub you are going to use - the one installed by Mint or the one installed by Ubuntu.  You have posted the *menu.lst* from the Unbuntu installation which from your earlier description of your boot menu is not the one you are using.

If you want to find out why your Mint is not loading then posting your menu.lst from your **Mint** installation would be a good idea.

To get a menu entry for Windows you will have to add something like the following to the bottom of your menu.lst file:
```
title Microsoft Windows
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

```
This assumes that Windows is on disk 3.  Make sure you edit the correct menu.lst file.  There is a file called /boot/grub/device.map where you can check your device mappings.

---

### Post by bj218 on 2008-06-07
1. Re runing  /boot/grub/menu.lst how do I do this I can't get Mint started?
2. Would it be a good idea to delete grub from one of the OS?
3. Can I do something with MBR?
4. Would reinstalling Mint do anything to help my problem?

---

### Post by nick_h on 2008-06-07
> 1. Re runing /boot/grub/menu.lst how do I do this I can't get Mint started?
You will need to mount the Mint partition in Ubuntu.  The fdisk command will show you the partitions.  Then mount it with something like:
```
sudo mkdir /mnt/Mint
sudo mount /dev/sdb1 /mnt/Mint
```

> 2. Would it be a good idea to delete grub from one of the OS?
You can very easily re-install grub - [link](http://ubuntuforums.org/showthread.php?t=224351).  In your case the *find /boot/grub/stage1* command should list two partitions (Mint and Ubuntu).

> 3. Can I do something with MBR?
You will want grub installed in the MBR of the first drive.  *setup (hd0)* in the link does this.

> 4. Would reinstalling Mint do anything to help my problem?
Yes, it might even fix everything.  It should install its copy of grub in the MBR of the first drive.  Hopefully it will then detect the other two OS and add entries for them.

---

### Post by bj218 on 2008-06-07
bill@bill-desktop:~$ ls -al /dev/disk/by-uuid 
total 0 
drwxr-xr-x 2 root root 220 2008-06-07 13:33 . 
drwxr-xr-x 6 root root 120 2008-06-07 06:33 .. 
lrwxrwxrwx 1 root root  10 2008-06-07 13:33 13A6A658EF2947F9 -> ../../sdc1 
lrwxrwxrwx 1 root root  10 2008-06-07 06:33 4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac -> ../../sdb1 
lrwxrwxrwx 1 root root  10 2008-06-07 06:33 4811-EA99 -> ../../sdc5 
lrwxrwxrwx 1 root root  10 2008-06-07 06:33 50C2-67F2 -> ../../sdb5 
lrwxrwxrwx 1 root root  10 2008-06-07 13:33 840841400841328A -> ../../sdc6 
lrwxrwxrwx 1 root root  10 2008-06-07 06:33 c2aedd8d-0818-4b0c-8f67-658ac8c6a04a -> ../../sda2 
lrwxrwxrwx 1 root root  10 2008-06-07 06:33 C5EB-64D2 -> ../../sda3 
lrwxrwxrwx 1 root root  10 2008-06-07 06:33 e2c057b4-5682-4789-b564-d2369e769c9e -> ../../sdb3 
lrwxrwxrwx 1 root root  10 2008-06-07 06:33 f948abb4-12b9-4c7c-9667-1f660631ddef -> ../../sda1 
bill@bill-desktop:~$ sudo fdisk -1 
[sudo] password for bill: 
fdisk: invalid option -- 1 

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table 
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s) 
       fdisk -s PARTITION           Give partition size(s) in blocks 
       fdisk -v                     Give fdisk version 
Here DISK is something like /dev/hdb or /dev/sda 
and PARTITION is something like /dev/hda7 
-u: give Start and End in sector (instead of cylinder) units 
-b 2048: (for certain MO disks) use 2048-byte sectors 
bill@bill-desktop:~$

---

### Post by nick_h on 2008-06-07
> fdisk: invalid option -- 1
You need a lowercase "L" rather than the number "1".

I think the situation is clear now.

If you boot to your PATA drive you get the Mint grub (which you haven't posted yet) which lists Mint and Ubuntu but the Mint option fails.

If you boot to your Windows partition I assume it boots to Windows OK.

What happens if you put your ubuntu drive first in the boot sequence?  The ubuntu grub entry looks good for booting to ubuntu with ubuntu being on the first drive.  If the ubuntu grub was installed to the MBR of its disk you should see 3 ubuntu options + 1 windows option (which won't work).

---

### Post by bj218 on 2008-06-08
WinXP works ok if i make the boot drive. Ubuntu works ok if i make it the boot drive.

Below are a Ubuntu  and Mint grub lst. Last nite I reinstalled Mint and everything worked great except no WinXP. This morning  Ubuntu said I needed a proprietary viedo
driver I said do it that was the end of Ubuntu screen goes BLACK when trying to reboot. 
This is the same thing that Mint was doing before I reinstalled it . Maybe I should start all over
ie reinstall both Ubuntu and Mint and have the 3 drives working plus have the boot sequence
setup properly !! ??. And don't install  any proprietary drivers? When i reinstalled Mint i made it root ie /, and i made the ntfs /Windows all the rest i left as/media/!!. What do thoes # signs mean in the grub lst?

The data below is the result of the following command &#8220;sudo gedit /boot/grub/menu.lst&#8221; in Mint

# menu.lst - See: grub(8), info grub, update-grub(8) 
#            grub-install(8), grub-floppy(8), 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-doc/. 

## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
default		0 

gfxmenu=/etc/grub/message.mint 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		10 

# Pretty colours 
color cyan/blue white/blue 

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
# kopt=root=/dev/hda1 ro 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,0) 

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

## altoption boot targets option 
## multiple altoptions lines are allowed 
## e.g. altoptions=(extra menu suffix) extra boot options 
##      altoptions=(recovery mode) single 
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

## ## End Default Options ## 

title		Linux Mint, kernel 2.6.22-14-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic 
boot 

title		Linux Mint, kernel 2.6.22-14-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic 
boot 

title		Linux Mint, kernel memtest86+ 
root		(hd0,0) 
kernel		/boot/memtest86+.bin 
boot 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 

 
# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-18-generic (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-17-generic (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, memtest86+ (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda5 
title		Windows NT/2000/XP 
root		(hd1,4) 
savedefault 
makeactive 
map		(hd0) (hd1) 
map		(hd1) (hd0) 
chainloader	+1 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb1 
title		Microsoft Windows XP Professional 
root		(hd2,0) 
savedefault 
makeactive 
map		(hd0) (hd2) 
map		(hd2) (hd0) 
chainloader	+1 


The data below is the result of the following command &#8220;sudo gedit /boot/grub/menu.lst&#8221; in Ubuntu

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
timeout		15 

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
# kopt=root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,0) 

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-18-generic 

title		Ubuntu 8.04, kernel 2.6.24-17-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-17-generic 

title		Ubuntu 8.04, kernel 2.6.24-16-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Ubuntu 8.04, memtest86+ 
root		(hd0,0) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda5 
title		Windows NT/2000/XP 
root		(hd0,4) 
savedefault 
makeactive 
chainloader	+1

---

### Post by nick_h on 2008-06-08
To fix your new problem with the video drivers, boot to recovery mode and run the following:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
It should give you a working video configuration.

When you have a working video configuration it is a good idea to make a backup of your /etc/X11/xorg.conf file.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

When you make Ubuntu the boot drive you should see the 3 Ubuntu kernels plus a non-working Windows option.  The grub entry for Windows on this partition is pointing to a Windows on an extended logical drive on the same disk as Ubuntu, which from what you have said is not where it is installed.

When you make Mint the boot drive you see the Mint options plus the Ubuntu ones (which work?) and 2 Windows options:  Windows NT/2000/XP and Microsoft Windows XP Professional.  The Windows NT/2000/XP is pointing to the extended logical drive on the same disk as Ubuntu and so will not work.  The Microsoft Windows XP Professional option is pointing to a Windows installation on disk 3, which is where it should be.  I'm not sure why this doesn't work.

Is your objective to get to the stage where you don't have to change the drive boot sequence and have all 3 OS on a grub menu?

---

### Post by bj218 on 2008-06-09
I would like to have all 3OS on agrub menu.I could reinstall Ubuntu/Mint if that is the best solution. I do have a couple of prog. on Ubuntu that i would like to save but because of the viedo prob. I may have to reinstall any way.

This is what I did this morning, booted to Ubuntu recovery mode and got a screen called &#8220;Recovery Mode Menu&#8221; I selected &#8220;drop to root shell prompt&#8221; 
root@bill-desktop:~#. I then typed &#8220;sudo dpkg-reconfigure phigh xserver-xorg. The results were &#8220;Package `phigh' is not installed and no information is avaible.
Use  sudo dpkg &#8211;-info (=dpkg-deb &#8211;info) to examine archive files,  use  sudo dpkg &#8211;contents (=dpkg-deb &#8211;contents) to list thier contents, use  sudo /usr/sbin/dpkg-reconfigure: phigh is not installed. The response I got from these commands were syntax error near unexpected token `('.
Since I know very little about Linux and it's commands I qiut while I was ahead. Wat do thoes # signs mean in the grub lst?

---

### Post by bj218 on 2008-06-18
Yesterday 6/17 I reinstalled Mint and had the drive sequence set properly ie dvd,2500,1600. After inst. I ran
the grub lst as showen below. Next I added the # sign in the 2 entries for WinXP that I think are wrong?
This did nothing to help my problem, both Mint and Ubuntu run just fine but no mention of Win?


# menu.lst - See: grub(8), info grub, update-grub(8) 
#            grub-install(8), grub-floppy(8), 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-doc/. 

## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
default		0 

gfxmenu=/etc/grub/message.mint 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		10 

# Pretty colours 
color cyan/blue white/blue 

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
# kopt=root=/dev/hda1 ro 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,0) 

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

## altoption boot targets option 
## multiple altoptions lines are allowed 
## e.g. altoptions=(extra menu suffix) extra boot options 
##      altoptions=(recovery mode) single 
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

## ## End Default Options ## 

title		Linux Mint, kernel 2.6.22-14-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic 
boot 

title		Linux Mint, kernel 2.6.22-14-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic 
boot 

title		Linux Mint, kernel memtest86+ 
root		(hd0,0) 
kernel		/boot/memtest86+.bin 
boot 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 

 
# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-18-generic (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-17-generic (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda1. 
title		Ubuntu 8.04, memtest86+ (on /dev/sda1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda5 
#title		Windows NT/2000/XP 
#root		(hd1,4) 
#savedefault                                                 NOTE: I put the # sign's in!!
#makeactive 
#map		(hd0) (hd1) 
#map		(hd1) (hd0) 
#chainloader	+1 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb1 
title		Microsoft Windows XP Professional 
root		(hd2,0) 
savedefault 
makeactive 
map		(hd0) (hd2) 
map		(hd2) (hd0) 
chainloader	+1 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb5 
#title		Windows NT/2000/XP 
#root		(hd2,4) 
#savedefault                                           NOTE: I put the # sign's in??
#makeactive 
#map		(hd0) (hd2) 
#map		(hd2) (hd0) 
#chainloader	+1

---

### Post by VMC on 2008-06-18
I noticed you were trying to give us your current disk layout. Please type the following and give output back here:

```
sudo fdisk -l
```

Also copy your outputs into CODE fields. Just copy all data then push on the # above.

Thanks.

---

### Post by nick_h on 2008-06-19
> I then typed &#8220;sudo dpkg-reconfigure phigh xserver-xorg.
You have missed out a minus sign.

> Wat do thoes # signs mean in the grub lst?
They are comments.  Don't uncomment them, the lines are supposed to be commented in the menu.lst file.  (I don't fully understand the last commented section though - an old copy of windows?)

Your menu.lst file looks good for the following boot sequence:
1. Mint
2. Ubuntu
3. Windows

---

### Post by bj218 on 2008-06-19
I have 3 HD'S :
The first is a 100GB Pata it has Mint on it.
The second is a 250GB Sata in MB sata1 connector it has Ubuntu on it.
The third is a 160GB Sata in MB sata2 connector it has WinXP on it.
During inst. Mint partitioned the drives as follows:
/dev/hda     (100GB Pata)
      /dev/hda1 ext3  I made this root  ie /
     /dev/hda2  swap
    /dev/hda 3  fat32
/dev/sda       (250GB Sata1)
      /dev/sda1 ext3
     /dev/sda3  swap
    /dev/sda5   fat32 
/dev/sdb       (160GB Sata2)
    /dev/sdb1   ntfs I made this /windows
   /dev/sdb5   fat32                                                                                                                   


bill@bill-desktop:~$ sudo fdisk -l 
Disk /dev/sda: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x95dc719e 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        3040    24418768+  83  Linux 
/dev/sda2            3169        6355    25599577+   f  W95 Ext'd (LBA) 
/dev/sda3            3041        3168     1028160   82  Linux swap / Solaris 
/dev/sda5            3169        6355    25599546    b  W95 FAT32 

Partition table entries are not in disk order 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x761c12f3 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        3187    25599546    7  HPFS/NTFS 
/dev/sdb2            3188       19457   130688775    f  W95 Ext'd (LBA) 
/dev/sdb5            3188        6374    25599546    b  W95 FAT32 
/dev/sdb6            6375        9561    25599546    7  HPFS/NTFS 

Disk /dev/hda: 100.0 GB, 100030242816 bytes 
255 heads, 63 sectors/track, 12161 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x0d4057a2 

   Device Boot      Start         End      Blocks   Id  System 
/dev/hda1   *           1        3039    24410736   83  Linux 
/dev/hda2            3040        3282     1951897+  82  Linux swap / Solaris 
/dev/hda3            3283        6321    24410767+   b  W95 FAT32 
bill@bill-desktop:~$
310-375-2437

---

### Post by bj218 on 2008-06-19
The # sign's that I added ie /dev/sda5 is a fat32 with my personal data on it.
The second place where I added the # sign ie /dev/sdb5 is a fat32 partition with the same data as the one above.

---

### Post by VMC on 2008-06-19
Your Grub mapping looks correct. Also the hard drive placement looks correct. Windows is on the third hard drive. You say that when grub shows its face Windows doesn't show up?

Can you tell us how many different boot images show up. It appears you have 5 or 6 on last count. I just want to make sure.

> title Microsoft Windows XP Professional 
root (hd2,0) 
savedefault 
makeactive 
map (hd0) (hd2) 
map (hd2) (hd0) 
chainloader +1

---

### Post by nick_h on 2008-06-20
> The # sign's that I added ie /dev/sda5 is a fat32 with my personal data on it.
The second place where I added the # sign ie /dev/sdb5 is a fat32 partition with the same data as the one above.
The Mint installation added these two sections thinking they were bootable Windows partitions.  You commented out the correct sections.

As VMC said the configuration looks good now.  I count 1 Mint kernel (+ recovery and memtest), 3 Ubuntu kernels (+ recovery and memtest) and 1 uncommented Windows section.

I would expect you to be able to get Mint and Ubuntu working.  There are potential problems with Windows when not on the first drive.  Here is a link to the [grub manual](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows).

---

### Post by bj218 on 2008-06-20
This is all the info. that is on the bootup screen.I would think Win should be here even if it won't boot!

Linux Mint kernel 2.6.22-14-generic
Linux Mint kernel 2.6.22-14-generic ( recovery mode)
Linux Mint kernel memtest 86+
Other operating systems:
Ubuntu 8.04 kernel 2.6.24-18-generic (on /dev/sda1)
Ubuntu 8.04 kernel 2.6.24-18-generic  (recovery mode) (on /dev/sda1)

---

### Post by VMC on 2008-06-20
> **nick_h said:**
>  There are potential problems with Windows when not on the first drive.  Here is a link to the [grub manual](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows).Exactly! That's why I mentioned that his mapping of the Windows chainload looked correct. I think that's the key somehow.

---

### Post by bj218 on 2008-06-20
I could remove Mint from the Pata drive and copy WinXP to that drive. I could then reinstall Mint on the 160GB Sata drive and change the MB Sata connectors.

---

### Post by nick_h on 2008-06-20
> I could remove Mint from the Pata drive and copy WinXP to that drive. I could then reinstall Mint on the 160GB Sata drive and change the MB Sata connectors.

I don't think that would work.  The easiest thing to do would be to change the boot sequence to:
1. Windows
2. Ubuntu
3. Mint
and then overwrite the MBR of disk 1 (the Windows disk) with grub.

Boot to Ubuntu and make 2 entries at the end of your menu.lst (under Other OS) for Windows and Mint.

Windows:
```
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```

Mint:
```
title Linux Mint, kernel 2.6.22-14-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
boot

title Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root (hd2,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single
initrd /boot/initrd.img-2.6.22-14-generic
boot

title Linux Mint, kernel memtest86+
root (hd2,0)
kernel /boot/memtest86+.bin
boot
```

Now locate the line:
```
# groot=(hd0,0)
```
and change it to:
```
# groot=(hd1,0)
```

Save the file and update it using:
```
sudo update-grub
```

Now you can install this grub on the Windows MBR:
```
sudo grub
root (hd0,0)
setup (hd**x**)
quit
```
where **x** is the drive number for Windows when you follow these instructions (use hd1 for drive 2).

The advantage of this setup is that you don't modify the grub on your Mint drive so that your previous configuration should still boot to Ubuntu and Mint.  It is also likely to boot to Windows.

The disadvantage is that you overwrite your Windows boot loader.  Before you try this I suggest that you have your Windows disk handy to restore it.  (Boot to recovery mode and type FIXMBR).

Edit:  Just realised that Ubuntu will be on hd0 for these instructions
Useful link - [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351[/url)

---

### Post by nick_h on 2008-06-20
Just one more thought - you ought to make a backup of your menu.lst before changing it:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Also, now I read through the instructions I gave they seem complicated since the drive order changes between setup and the final order.  My setup is 3 OS on a single drive with Windows on the first partition.  It might be useful to get another opinion.

The link in my previous post will allow you to retore grub from a live CD if something goes wrong.  The Windows CD will allow you to restore your Windows MBR if something goes wrong.

---

### Post by bj218 on 2008-06-21
Why do you think puting win on the Pata drive and have the 2 linux OS on the 2 Sata drives wouldn't work? We have been more than a week at trying to fix my current problem, I think I am not capable of working with the linux commands ie when I hit enter in this cmd to go to the second line I get a lot of info but no second line!! as for x I think it should be hd2 since it is the third drive? I made all the changes to  the Ubuntu grub.lst except this one & the BU one.If you want I can copy the grub.lst for you?
sudo grub
root (hd0,0)
setup (hd2)
quit

---

### Post by nick_h on 2008-06-21
> Why do you think puting win on the Pata drive and have the 2 linux OS on the 2 Sata drives wouldn't work?
Windows is generally happier installed on the first partition of the first drive.  It shouldn't matter if it is on a sata or pata drive as long as the Windows drive is the first drive.  It seems that the drive order is defined by the boot sequence.

I'm not saying that it is impossible to get it working when Windows is not the first drive (that is why I gave you the link to the grub manual).  Both VMC and I thought that your grub configuration looked OK for Windows on the third drive but it obviously didn't work.  I don't know why.

> I think I am not capable of working with the linux commands ie when I hit enter in this cmd to go to the second line I get a lot of info but no second line!!
After you type *sudo grub* you should see a grub prompt *grub>*

These commands are a little confusing especially when you are changing the boot sequence.  I can see now why you wanted phone support.  Did VMC phone you?

My instructions were intended to make a good menu.lst based on Windows being the first drive in the boot sequence.  The final set of commands are just to install grub to the MBR of the Windows drive.  However, at the point you execute these commands you drive order might not be the final drive order.

If you want an easier idea then make Windows the first drive.  Then install a Linux OS on either the second or third drive.  In the installation there should be an advanced option where you can specify where you want grub installed - specify the MBR of the first (Windows) drive.  This will overwrite the boot loader for Windows, but you can restore it if necessary with the Windows CD.

---

### Post by nick_h on 2008-06-21
Just found a link that might be useful - [http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

This is a guide for installing 3 OS (Windows + 2 Ubuntu) on 2 drives.  Note how Windows is on the first partition of the first drive.  It also shows the screen where you can select where to install grub.

The link comes from the [Illustrated Dual Boot Site](http://users.bigpond.net.au/hermanzone/).  There may be other examples that are useful.

---

### Post by VMC on 2008-06-21
bj218,

Where do we stay so far? Is this still valid?

> 1 SATA HD = XP, 1 SATA HD = ubuntu, 1 IDE HD = Mint
There all plugged in, but you switch them through the BIOS, correct?

I looked back and you mentioned that you change the drive order somehow through BIOS. Lets keep the BIOS from changing. Can you display what BIOS options for the drives. 

If Nick's links fixed the problem and/or if you moved XP to the first hard drive so we don't have to map Windows, We will need a fresh:

```
sudo fdisk -l
```

Also what boots and works and what doesn't. I'm a little lost at this point.

---

### Post by bj218 on 2008-06-28
The last few days I have been looking at the links Nick gave me their sure is plenty of info. available. I put most of the sites in my bookmarks so I can study them more later THANK'S NICK. AT this time I only have my WinXP drive running (160GB connected to the SATA2 MB connector). I have a new prob. when I try to boot Ubuntu I get a error message 17 and a black screen!! If it would make things simpler I could put both Linux systems on the 250GB drive which is connected to the SATS1 MB connector? At present my boot sequence is:
1st Boot Device      WDC1600
2nd Boot Device      DVD
3rd Boot Device      1st floppy
During Bootup I see the following 
Auto Detecting  Pri Slave  DVD
Auto Detecting  4th Master IDE Hard Drive

---

### Post by nick_h on 2008-06-28
> AT this time I only have my WinXP drive running
Where is the Ubuntu you are trying to run?  on the XP drive?
Have you installed grub on the MBR of your XP drive?

---

### Post by bj218 on 2008-06-28
Ubuntu is inst. on the 250GB SATA drive and WinXP is inst. on the 160GB
SATA drive. I ran the WinXP CD and did a FIXMBR on the 160GB drive the other 2 drives(250GB SATA + 100GB PATA) were not connected to power, so I think grub is not inst. on the MBR of the Win drive at this time. Also 
Mint is not inst. on any drive at this time.

---

### Post by nick_h on 2008-06-28
I think that you will need to re-install grub.

[How to install Grub from a live Ubuntu cd.](http://ubuntuforums.org/showthread.php?t=224351)

You can either install it to the MBR of the Ubuntu disk or the Windows disk.  I suggest you install it to the Windows MBR and keep the Windows as the first disk in the boot sequence.

You will need to make sure that your /boot/grub/menu.lst file is consistent with your installation.  (This is probably why you are getting grub error 17 at the moment)

Post your menu.lst file if you have problems.

---

### Post by bj218 on 2008-07-01
Nick  I want to thank you and VMC you both have taught  me quit a bit about the Linux OS. Every thing is working  great now even error 17 is gone. It looks like if  you have Windows on a multi drive systems you have to set the boot sequence correctly and you need to put Grub on the Win MBR.
Thanks again without your help I probably would have given up. Another ? can  I delete the Grub entries that do not work?


1.  Putting  Ubuntu Grub on Win MBR

[ Minimal BASH-like line editing is supported.   For 
         the   first   word,  TAB  lists  possible  command 
         completions.  Anywhere else TAB lists the possible 
         completions of a device/filename. ] 

grub> find /boot/grub/stage1 
 (hd1,0) 

grub> root (hd1,0) 

grub> setup (hd0) 
 Checking if "/boot/grub/stage1" exists... yes 
 Checking if "/boot/grub/stage2" exists... yes 
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded. 
succeeded 
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,0)/boot/grub/stage 
2 /boot/grub/menu.lst"... succeeded 
Done. 

After doing this I  restarted and got 3 Ubuntu  and 1 WinXP readings and each one worked great.
WinXP is inst. on the 160GBdrive and Ubuntu is on the 250GB drive.


 2.   This is the  Ubuntu Grub Lst on 6/29/08

## ## End Default Options ## 

title		Ubuntu 8.04, kernel 2.6.24-18-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-18-generic 

title		Ubuntu 8.04, kernel 2.6.24-17-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-17-generic 

title		Ubuntu 8.04, kernel 2.6.24-16-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Ubuntu 8.04, memtest86+ 
root		(hd1,0) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 

# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb1 
title	Microsoft Windows XP Professional 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 


3.After making sure that every thing was working I then installed Mint on the
Ubuntu drive.

 4.   This is the Mint Grub Lst after installation of Mint.

# ## End Default Options ## 
title		Linux Mint, kernel 2.6.22-14-generic 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb4 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic 
boot 

title		Linux Mint, kernel 2.6.22-14-generic (recovery mode) 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb4 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic 
boot 

title		Linux Mint, kernel memtest86+ 
root		(hd1,3) 
kernel		/boot/memtest86+.bin 
boot 

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


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda5           Can I delete these entries with the delete key?
#title		Windows NT/2000/XP 
#root		(hd0,4) 
#savedefault               I added the # sign's
#makeactive 
#chainloader	+1 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-18-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-17-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, memtest86+ (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Linux Mint, kernel memtest86+ (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb5     Can all of these be deleted with the delete key?
#title		Windows NT/2000/XP 
#root		(hd1,4) 
#savedefault          I added the # sign's
#makeactive 
#map		(hd0) (hd1) 
#map		(hd1) (hd0) 
#chainloader	+1 


This is the Ubuntu Grub Lst that I got this morning 7/1/08


## ## End Default Options ## 

title		Ubuntu 8.04, kernel 2.6.24-18-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-18-generic 

title		Ubuntu 8.04, kernel 2.6.24-17-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-17-generic 

title		Ubuntu 8.04, kernel 2.6.24-16-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
quiet 

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Ubuntu 8.04, memtest86+ 
root		(hd1,0) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 

# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb1 
title	Microsoft Windows XP Professional 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 


This is the Mint Grub Lst that I got this morning 7/1/08

title   Linux Mint, kernel 2.6.22-14-generic 
root  (hd2,0) 
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quit splash 
initrd /boot/initrd.img-2.6.22-14-generic 
boot 

title   Linux Mint, kernel 2.6.22-14-generic (recovery mode) 
root  (hd2,0) 
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single 
initrd /boot/initrd.img-2.6.22-14-generic 
boot 

title   Linux Mint, kernel memtest86+ 
root  (hd2,0) 
kernel /boot/memtest86+.bin 
boot 

title		Linux Mint, kernel 2.6.22-14-generic 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb4 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic 
boot 

title		Linux Mint, kernel 2.6.22-14-generic (recovery mode) 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb4 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic 
boot 

title		Linux Mint, kernel memtest86+ 
root		(hd1,3) 
kernel		/boot/memtest86+.bin 
boot 

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


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda5 
#title		Windows NT/2000/XP 
#root		(hd0,4) 
#savedefault 
#makeactive 
#chainloader	+1 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-18-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-17-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04, memtest86+ (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Linux Mint, kernel memtest86+ (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb5 
#title		Windows NT/2000/XP 
#root		(hd1,4) 
#savedefault 
#makeactive 
#map		(hd0) (hd1) 
#map		(hd1) (hd0) 
#chainloader	+1 


When I bootup now I get 3 Mint choice's +1 WinXP  + 1 Ubuntu I can boot all of them with no prob.
This is great and I have no prob. with it,  but the Grub Lst looks like there should be something more showing when I bootup!!

---

### Post by nick_h on 2008-07-02
You now have Windows, Ubuntu and 2 Mint systems (one on disk 2 and the other on disk 3).

The section of the menu.lst file between "BEGIN AUTOMAGIC KERNELS LIST" and "END DEBIAN AUTOMAGIC KERNELS LIST" is automatically generated.  Don't manually make changes here because they will be overwritten when kernels are added or removed from the system.  If you want to reduce the number of kernels displayed here then edit the line:
```
# howmany=all
```
and specify the number of kernels you want listed.

Then regenerate the menu.lst file with:
```
sudo update-grub
```

The section after "END DEBIAN AUTOMAGIC KERNELS LIST" you can edit to suit your requirements.

The only disadvantage to this setup is that only one linux system will update grub automatically when a new kernel is added.  You could install a grub for each linux system and then chainload them but I use one copy of grub and update it manually.

---

### Post by VMC on 2008-07-02
bj, Also, and I don't recall if Nick mentioned this on his links, but there is a good tutorial on Grub and on using Startup Manager. It would do you good to print it out and study it. It's found here and on my signature link:

[http://ubuntuforums.org/showthread.php?t=818177&highlight=HOWTO](http://ubuntuforums.org/showthread.php?t=818177&highlight=HOWTO)

Glad everything is working okay. Remember you wanted just phone help. I said then that this would benefit more people having similar issues. Someone over the phone could have walked you through it, but trial and error(mostly error), is sometimes the best teacher. There's a big difference having someone telling you to go here and push that, add this, then you actually doing the work yourself. Good job!

---

### Post by bj218 on 2008-07-03
This is one of the links that I looked at the other day but did not understand how it worked it sounds
good but!!
The link below says you can put grub on a seperate partition.
[http://www.users.bigpond.net.au/hermanzone/p18.htm#](http://www.users.bigpond.net.au/hermanzone/p18.htm#)



Keep GRUB and Make a Dedicated GRUB Partition*
GRUB is more than just a boot loader, GRUB is almost a small operating system in it's own right. GRUB doesn't need to be inside a Linux operating system for any real reason, GRUB can stand on it's own two feet! *GRUB only needs a small partition and can live on its own.
GRUB is actually a great boot manager as well as a boot loader. 
Actually, it is FAR BETTER to use GRUB as your 'third party boot manager'* if you are setting up a Windows-Windows dual boot than to let Windows do it the Windows default way, read this website to find out why, Understanding MultiBooting and Booting Windows from an Extended Partition.
So if you have read all that you'll understand why you should keep GRUB, even if you are giving up on Linux

---

### Post by VMC on 2008-07-03
> **bj218 said:**
> This is one of the links that I looked at the other day but did not understand how it worked it sounds
good but!!
The link below says you can put grub on a seperate partition.
[http://www.users.bigpond.net.au/hermanzone/p18.htm#](http://www.users.bigpond.net.au/hermanzone/p18.htm#)

Red Hat uses a separate boot partition. I prefer to keep it simple "[KISS]("http://en.wikipedia.org/wiki/KISS_principle")". Once you get use to using grub you won't have the problems you've experienced. I don't see the benefit of having a separate partition wasting space. I'm sure the ones that came up with that idea may have their reasoning.

---

### Post by bj218 on 2008-07-03
That How To looks very interesting I have it on my computer and will study it more later. Thanks bj

---

### Post by |{urse on 2008-07-03
I prefer to KISS too <3 lol.

---

