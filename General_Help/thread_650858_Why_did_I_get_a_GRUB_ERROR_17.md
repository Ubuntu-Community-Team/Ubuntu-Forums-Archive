---
title: "Why did I get a GRUB ERROR 17?"
date: 2007-12-26
forum: General Help
---

### Post by TR3GO on 2007-12-26
Hello,

I have two disk drives... One 500 GB Samsung SATA Disk & One 80 GB Western Digital EIDE. I dedicated my 80 GB Disk to Ubuntu. I selected (Use 80 GB EIDE DISK for Install). So it installed....

I boot up into Vista Select EasyBCD 1.7 to add the Linux (Ubuntu) to the MBR. 

I restart -- Vista WORKS -- then I reboot -- Select Ubuntu and it goes into a GRUB loader. I select Ubuntu.

It gives me an Error 17 - Disk is ntfs and some other information. I assumed during the install it changed the disk to EXT2 or EXT3.

I installed Ubuntu 7.10 by the way.

WHY IS IT GIVING ME AN ERROR 17? I tried reinstalling over and over & it still gave me the same issue. I know it saved GRUB to (HD0). Could that be an issue?

How can I have the windows boot loader allow me to boot into Ubuntu or Vista with no ERROR or MISSING NLTDR.

THANKS FOR YOUR HELP!!
-Stefan

---

### Post by p_quarles on 2007-12-26
This will be a lot easier if you just use GRUB to load both Ubuntu and Windows. Easier, plus a lot more people here are going to know how to help you.

---

### Post by PmDematagoda on 2007-12-26
Are you sure the GRUB entry for Ubuntu is pointing at the right drive?

For example when you press "E" at the entry there shold be an antry like this:-

```
root (hd1,0)
```

---

### Post by TR3GO on 2007-12-26
I'm not positive -- when I was installing Ubuntu I clicked advanced before installing and it said Ubuntu was being installed to (HD0). But how can I log into Ubuntu with the error 17 to double check?

---

### Post by p_quarles on 2007-12-26
The hard drive address in GRUB-speak is going to contain two digits, separated by a comma, i.e.: "(hd0,0)"

You can check by booting from a live disk and looking at /boot/grub/menu.lst

---

### Post by TR3GO on 2007-12-26
Ok i'll do that... do I open up the terminal and cast "/boot/grub/" and cat menu.lst?

after I do that i'll post where GRUB is pointed.

Thanks!

---

### Post by p_quarles on 2007-12-26
Or, just:
```
cat /boot/grub/menu.lst
```

---

### Post by TR3GO on 2007-12-27
I "cd boot" and I'm in the boot directory, but I do not have grub directory. Boot is as far as I can get.

```
buntu@ubuntu:~$ cd /boot
ubuntu@ubuntu:/boot$ ls
abi-2.6.22-14-generic             memtest86+.bin
config-2.6.22-14-generic          System.map-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak  vmlinuz-2.6.22-14-generic

```

Any further recommendations on how I can boot into Ubuntu? 
And also boot into Vista?

---

### Post by p_quarles on 2007-12-27
> **TR3GO said:**
> I "cd boot" and I'm in the boot directory, but I do not have grub directory. Boot is as far as I can get.

```
buntu@ubuntu:~$ cd /boot
ubuntu@ubuntu:/boot$ ls
abi-2.6.22-14-generic             memtest86+.bin
config-2.6.22-14-generic          System.map-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak  vmlinuz-2.6.22-14-generic

```

Any further recommendations on how I can boot into Ubuntu? 
And also boot into Vista?
Yeah, I was kind of afraid of that. I'm guessing that GRUB was installed on your Windows partition, and that's why it's giving you the "wrong filesystem" error. 

Like I said before, this will be much easier if you use GRUB as your primary bootloader. I've dual-booted with Ubuntu and Vista in the past, and GRUB handles this perflectly well.

---

### Post by TR3GO on 2007-12-27
Ok I did locate on menu.lst... and found:

```
ubuntu@ubuntu:/$ cd /usr/share/doc/memtest86+/examples/
ubuntu@ubuntu:/usr/share/doc/memtest86+/examples$ ls
grub-menu.lst  lilo.conf
ubuntu@ubuntu:/usr/share/doc/memtest86+/examples$ cat grub-menu.lst 
# sample /boot/grub/menu.lst entry for memtest86
#
# This example  assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

```

It says sample -- so I doubt this is it.

---

### Post by p_quarles on 2007-12-27
Yeah, that's definitely not the boot menu, that's just documentation. Like I said, it looks like GRUB is installed on the Windows partition, but I would have no idea where to look for it.

---

### Post by TR3GO on 2007-12-27
Ok... How about if I DELETE THE UBUNTU INSTALLATION under Vista. 

Start from scratch.

Turn off computer -- disconnect my Vista Drive

Redo Ubuntu installation so it only can see one hard disk.

Will that do the trick?

Only down side it won't see Vista in Grub.

---

### Post by meierfra on 2007-12-27
> Yeah, that's definitely not the boot menu, 

The OP is working on the live CD. that why he/she cannot find menu.lst.

Do you have an icon for the ubuntu partition on the   desktop? If not look in Computer->Places.

Click on the icon do mount the partition.

Then open a terminal and 

```
gksudo gedit /media/disk/boot/grub/menu.lst
```


Post your menu.lst and also

```
sudo fdisk -l
```

---

### Post by p_quarles on 2007-12-27
No, no, you don't need to reinstall anything. You just need to install GRUB, and it *will* automatically detect your Vista partition (it did for me anyway). 

There are two ways to do this.
1) Use the Ubuntu live CD: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
2) Use the Super Grub Disk: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

The only potential problem I can foresee here is that GRUB may attempt to boot into your EasyBCD menu rather than directly to Vista. You might just want to uninstall that before installing GRUB.

---

### Post by meierfra on 2007-12-27
Don't delete Ubuntu. I'm sure there is nothing wrong with it. Just a slight confusion between disks. (Happens with Sata and Ide drives)

---

### Post by meierfra on 2007-12-27
Only menu.lst needs to edited, then EasyBCD will work.  (and you will need to edit menu.lst even if you replace EasyBCD by Grub)

---

### Post by TR3GO on 2007-12-27
menu.lst:

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
# kopt=root=UUID=6484deab-5ff0-4357-99e6-c297e2d9cd18 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6484deab-5ff0-4357-99e6-c297e2d9cd18 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6484deab-5ff0-4357-99e6-c297e2d9cd18 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
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
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

sudo fdisk -l:

```
ubuntu@ubuntu:~$ gksudo gedit /media/disk/boot/grub/menu.lst

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09220921

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9327    74919096   83  Linux
/dev/hda2            9328        9729     3229065    5  Extended
/dev/hda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00046ae5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15200   122093968+   7  HPFS/NTFS
/dev/sda2           15201       30400   122094000    7  HPFS/NTFS
/dev/sda3           30401       45600   122094000    7  HPFS/NTFS
/dev/sda4           45601       60801   122102032+   7  HPFS/NTFS

Disk /dev/sdb: 2079 MB, 2079850496 bytes
17 heads, 32 sectors/track, 7467 cylinders
Units = cylinders of 544 * 512 = 278528 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7468     2031088    6  FAT16
ubuntu@ubuntu:~$ 

```

I also looked in "Computer" and found my partition. It's a 74 GB disk. I right clicked and it is mounted.

Thanks for your help

---

### Post by meierfra on 2007-12-27
Since you have  three   disks I'm not 100 % sure that this will work on the first try, but it should:

Edit menu.lst as follows:

Change 

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)

to

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)


save the file and reboot. If it did not work, try (hd1,0) in place of (hd2,0).

---

### Post by TR3GO on 2007-12-27
Ok I made the change -- Let me see if it works. I do have EasyBCD adding Ubuntu to the Vista Boot Loader... Does that mean anything?

---

### Post by TR3GO on 2007-12-27
I tried it with the new (hd2,0) and it just booted into Vista. Do I need to do a new MBR in BCD?

I tried to change the HD to (hd1,0) but when I go into the terminal and enter: I tried it with the new (hd2,0) and it just booted into Vista. Do I need to do a new MBR in BCD?

I entered ```
gksudo gedit /media/disk/boot/grub/menu.lst
``` into the terminal -- but I just get a blank file.

---

### Post by TR3GO on 2007-12-27
Nevermind -- closed the terminal and opened it again and got the file to open. Disregard.

---

### Post by meierfra on 2007-12-27
> Do I need to do a new MBR in BCD?

No. You did  not change the MBR. Only the file menu.lst.

---

### Post by meierfra on 2007-12-27
Did (hd1,0) fail too?

If yes, you should switch to grub. Let me  know.  It is fairly easy and I can give you detailed instruction.

---

### Post by meierfra on 2007-12-27
Oops, I just realized that sdb is just  a flash drive. So I should have suggested (hd1,0) first.

---

### Post by TR3GO on 2007-12-27
Yea thats my little flash drive -- Um... Ok so let me try (hd1,0) again. BECAUSE...

In Vista I have to add Linux to the MBR because when I do it allows me to select Ubuntu and go into the grub menu and then get into Ubuntu. I tried it with (hd2,0) and it said it couldn't find the installation. So I am gonna try: (hd1,0) and see if it works, and I'll brb!

Thanks!

---

### Post by TR3GO on 2007-12-27
HURRRRRRAAYYYYY!!! IT WORKS!!! 

I set it to (hd1,0) like you said and it works!

I have to have the Vista MBR have Vista & Ubuntu on it --- once I click Ubuntu it goes into grub and then I load up Ubuntu!

I forgot how sleek this OS is!

Now I got to stop this continuous loud BUZZ.

THANKS A LOT FOR EVERYONES HELP!

---

### Post by meierfra on 2007-12-27
> In Vista I have to add Linux to the MBR because when I do it allows me to select 

I don't  understand. You already added Ubuntu to  EasyBCD a long time ago. You shouldn't have to do it again.

Oops. Didn't see your previous post.

---

### Post by TR3GO on 2007-12-27
I installed updates under Ubuntu and now it won't boot again -- weird. I found out it was because it changed the hd to (hd0,0) for some reason. I changed it back to (hd1,0) along with the debug one and the rest of the Ubuntu options and it gave me a "Panic error". I'm not just leaving the one Ubuntu option in the grub loader to be (hd1,0)... To see if that helps.

Do you have a reason for this change?

---

### Post by TR3GO on 2007-12-27
No I still keep getting a kernel panic... Most likely due to the updates I did...

---

### Post by meierfra on 2007-12-27
I  just  came here to tell you  that you need to edit menu.lst a little bit more so that you don't run into troubles after the next kernel update. Seems it already happened. Just give me a minute to type up instructions.

---

### Post by meierfra on 2007-12-27
I know why (hd1,0) changed to (hd0,0)  and that is my fault. It  can be fixed easily so that it does not happen again. But we'll worry about that later. But I do not understand the kernel panic after you fixed that.  (Can't blame that on me)

You should have  a backup of your menu.lst called menu.lst~ (also in /boot/grub on the ubuntu partition)

Boot from the live CD, mount your ubuntu partition and compare the two.  In particular look at  "root=UUID=some number"  in the Ubuntu item.  Compare the numbers. 

You might also compare the numbers with the output of

```
blkid
```

---

### Post by meierfra on 2007-12-27
To avoid that "root (hd1,0)" is changed to   "root (hd0,0)" during kernel upgrades change

#groot (hd0,0) 

to

#groot (hd1,0)

To be able to boot into recovery mode and  run the memtest change the corresponding "root (hd0,0)" to "root (hd1,0)".

I also suggest to change

#hiddenmenu

to 

hiddenmenu.

(This way the grub menu won't appear during boot-up. If you need to get into recovery mode, press "esc" during the count down, and the grub menu will appear)

Also change

timeout 10 

to say 

timeout 2

(10 means that grub waits for 10 second until it boots the default choice)

Once you did these changes you won't hardly notice that there are two menus involved in the boot process.


You might also change 

title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

to 

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


This way if you wanted to boot into Vista but accidently picked Ubuntu  at the EasyBCD menu you can still pick Vista at theGrub menu.


But none of this will fix your kernel panic problem.

---

### Post by TR3GO on 2007-12-27
Yea I wish the kernel update wouldn't do that -- But idk...

Here is my number: root=UUID=6484deab-5ff0-4357-99e6-c297e2d9cd18 ro

---

### Post by p_quarles on 2007-12-27
If you think it was the kernel update that's causing the panic, you can pretty easily revert the default to the previous kernel. You'd need to edit /boot/grub/menu.lst again, and then change the "default" line to point to the number of the kernel you want to boot. Note that the counting starts at zero -- so the third kernel in the Automagic list (which is most likely the one you want) would be 2.

---

### Post by meierfra on 2007-12-27
If you are lucky   the kernel update just put the wrong UUID's  in your menu.lst (see post 31). But that is unlikely.

kernel problem are outside of my area of expertise, but here are some basic suggestion what you can do:

1)  add some parameters to the kernel line in menu.lst, for example noapic:

kernel		/boot/vmlinuz-2.6.22-14-generic
root=UUID=6484deab-5ff0-4357-99e6-c297e2d9cd18 ro quiet splash noapic

(that needs to be all on one line)

2)  reinstall (and   refuse the kernel update)


3)  revert to the old kernel (you will have to chainroot into you ubuntu partition, and install the older kernel, but I don't know the details)

---

### Post by meierfra on 2007-12-27
> you can pretty easily revert the default to the previous kernel. 

I'm pretty sure that  this was  a minor kernel upgrade, (that is one with basicly  the same version number)  That means that the old kernel was overwritten and not added to "menu.lst"

---

### Post by p_quarles on 2007-12-27
> **meierfra said:**
> I'm pretty sure that  this was  a minor kernel upgrade, (that is one with basicly  the same version number)  That means that the old kernel was overwritten and not added to "menu.lst"
Oh, yeah, you're right. Doesn't look like there's been a major kernel upgrade since Gutsy was released, so that won't work. (and I'm guessing that no one wants GRUB to default to Memtest :D )

---

### Post by meierfra on 2007-12-27
> Here is my number: root=UUID=6484deab-5ff0-4357-99e6-c297e2d9cd18 ro

So the UUID's are not the problem.

---

### Post by TR3GO on 2007-12-27
Ok I made the changes -- I haven't reboot yet -- But I'm going to try to find a solution for the Kernel Panic problem.

---

### Post by meierfra on 2007-12-27
> (and I'm guessing that no one wants GRUB to default to Memtest  )

Wouldn't be worse than the current situation:)

---

### Post by TR3GO on 2007-12-27
So what are my options -- Should I just reinstall Ubuntu -- change my menu.lst to (hd1,0) and update it without the minor kernel upgrade?

Can I uninstall the new kernel?

What would be the best solution?

---

### Post by meierfra on 2007-12-27
Did you see post 35?

Uninstalling the kernel should be possible, but I don't know the specifics

---

### Post by TR3GO on 2007-12-27
Ok -- Yea I must have skimmed over those tips. I will do that -- and tell you the outcome.

Thanks!

---

### Post by TR3GO on 2007-12-27
OK! It works now -- I put "noapic" at the end of the boot path and it booted up with no problems. Thanks for all your help!

---

### Post by meierfra on 2007-12-27
> OK! It works now -- I put "noapic" at the end of the boot path and it booted up with no problems.

Good news. I didn't really think it would work. I just had googled  "kernel panic gutsy" and some people had solved their problem with "noapic". I don't even  know what "noapic" does. It does disable something. So I suggest to remove the "noapic" after the next kernel update.

---

