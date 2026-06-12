---
title: "Cannot do a triple boot"
date: 2007-12-24
forum: General Help
---

### Post by AimLXJ on 2007-12-24
Okay I have four partitions on one hardrive and the stuff were installed in this order:
1. System Recovery - SDA1
2. Windows XP - SDA2
3. Windows Vista - SDA5
4. Ubuntu - SDA6

I tried booting WIndows XP but all it did was it bootup the System Recovery, for WIndows Vista it said something about "Invalid Device Requested". So I went to the menu.lst and tried booting Windows XP and Windows Vista with (HD0,0), (HD0,1), (HD0,2), (HD0,3), (HD0,4), (HD0,5).
With (HD0,0) my computer just reboots, for (HD0,1) the System Recovery starts up, and the rest I recieve "Invalid Device Requested".

**blkid**
> /dev/sda1: UUID="220CFF700CFF3D7B" TYPE="ntfs" 
/dev/sda2: UUID="34CC52D3CC528ECC" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda5: UUID="12F4A00D3D9D0BA1" LABEL="Windows Vista" TYPE="ntfs" 
/dev/sda6: UUID="9898c63b-d7a8-4cec-bc85-83745a3995a2" TYPE="ext2" 

**Super Grub Disk**
I tried getting the MBR back and I believe I have, but the computer kept on rebooting so I went back to Grub

**GParted**
[[IMG]http://img175.imageshack.us/img175/5333/90245191mj3.th.jpg[/IMG]](http://img175.imageshack.us/my.php?image=90245191mj3.jpg)

Help Please!

:(

---

### Post by heatpumpcontrol on 2007-12-24
post your grub.

gksudo gedit /boot/grub/menu.lst

---

### Post by AimLXJ on 2007-12-24
> **heatpumpcontrol said:**
> post your grub.

gksudo gedit /boot/grub/menu.lst

**Grub**
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
# kopt=root=UUID=9898c63b-d7a8-4cec-bc85-83745a3995a2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9898c63b-d7a8-4cec-bc85-83745a3995a2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9898c63b-d7a8-4cec-bc85-83745a3995a2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,4)
savedefault
makeactive
chainloader	+1


---

### Post by heatpumpcontrol on 2007-12-24
what are you booting into now? or is this machine not booting?

---

### Post by AimLXJ on 2007-12-24
I'm trying to boot into Windows XP and Vista.

---

### Post by heatpumpcontrol on 2007-12-24
> **AimLXJ said:**
> I'm trying to boot into Windows XP and Vista.

Yes but are you in Ubuntu right now?

---

### Post by AimLXJ on 2007-12-24
Yes.

---

### Post by heatpumpcontrol on 2007-12-24
> **AimLXJ said:**
> Yes.

Ok.... let me look at this and I'll try to help you. HD labels are different from what grub looks at. For grub the partitions start at 0... ie (hd0,0) so this would be HD1 partition 1...kinda weird. I can't explain it but it works something like that...

---

### Post by AimLXJ on 2007-12-24
I think I understand you, so is there anything you can do to?

---

### Post by heatpumpcontrol on 2007-12-24
It seems to me that your boot order is good in grub. but let's play with it a bit.
First let's make a back up of grub. (We won't change anything on (hd0,5) cause that's your active boot of ubuntu and it works..

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

now:

```
gksudo gedit /boot/grub/menu.lst
```

where you have Vista (hd0,4) change that to

(hd0,2)

Let's try that first... and try to boot into Vista.

---

### Post by AimLXJ on 2007-12-24
Got this error:
> Error 12: Invalid device requested
Press any key to continue...

---

### Post by heatpumpcontrol on 2007-12-24
OK. do this

```
sudo cp /boot/grub/menu.lst.bak /boot/grub/menu.lst
```

this brings you back to previous condition.

Please go to Partition Editor and make sure that those partitions where Vista and XP are located are flagged as boot partitions. Just right click on them and select "Manage Flags". If they are not then make sure that "boot" is selected and then try again.. I'll wait

---

### Post by AimLXJ on 2007-12-24
Yea, both of were already flagged as "boot".

---

### Post by heatpumpcontrol on 2007-12-24
Ok, did some searching and you may want to try this link

[http://ubuntuforums.org/showthread.php?t=226402](http://ubuntuforums.org/showthread.php?t=226402)

It utilizes a SystemRescueCD. I've used it and it will guide you on getting into your bootable partitions. What I suggest is using it and keeping an eye on what and where the SR CD reports each bootable partition to be and then editing your grub/menu.lst to reflect the same.

---

### Post by heatpumpcontrol on 2007-12-24
I will continue to review this but I'm not too hip on linux enough to solve this at the moment. I would have to do more reading myself.... Sorry. I like to try

---

### Post by AimLXJ on 2007-12-24
So basically I insert the CD and reboot the computer, then type fdisk -l which will tell me all the names of the partition which I write down correct?

---

### Post by heatpumpcontrol on 2007-12-24
Yes, Also I just thought of something else. When you reboot, you get the grub menu correct. Well what you can do is right there just click e on your keyboard and edit the grub menu.lst and try different combinations of (hd0,3) for example on the XP or Vista partition and see what grub does. If it doesn't like it, it will just let you know right then and there and you can just try another partition number.

Just remember your original partition number and DO NOT CHANGE YOUR UBUNTU (hd0,5)

---

### Post by heatpumpcontrol on 2007-12-24
let me try it on my laptop.... I have dual boot on it...


OK, you can. just highlight the OS that you want to work with and click 'e' on keyboard and go from there.

---

### Post by meierfra on 2007-12-24
You might try 

title Windows NT/2000/XP
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

and 

title Windows Vista/Longhorn (loader)
rootnoverify (hd0,4)
savedefault
chainloader +1

(I removed the makeactive, since makeactive applied to a  logical partition gives the "invalid device" error)
But I don't have much hope that this will work. 

In theory your Windows XP entry should  work, and give you  a menu from which you can choose between XP and Vista.  
Were you able to boot into Vista after you installed Vista and before you installed Ubuntu?
Could you describe the whole installation process in more details?

Boot into ubuntu and 
post the output of 

```
sudo fdisk -l
```

Are you able to mount your windows partitions? Post the output of

```
mkdir XP
sudo mount -t ntfs /dev/sda2 XP
mkdir Vista
sudo mount -t ntfs /dev/sda5 Vista

```

---

### Post by AimLXJ on 2007-12-24
[[IMG]http://img291.imageshack.us/img291/1691/1224072052ev4.th.jpg[/IMG]](http://img291.imageshack.us/my.php?image=1224072052ev4.jpg)

---

### Post by AimLXJ on 2007-12-24
**sudo fdisk -l**
> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe986dc4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         914     7341673+  17  Hidden HPFS/NTFS
/dev/sda2   *         915       16178   122608080    7  HPFS/NTFS
/dev/sda3           16179       24321    65408647+   f  W95 Ext'd (LBA)
/dev/sda5   *       16179       21771    44925741    7  HPFS/NTFS
/dev/sda6           21772       24321    20482843+  83  Linux

Disk /dev/sdf: 125 MB, 125960704 bytes
8 heads, 32 sectors/track, 961 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         961      122959+   6  FAT16


> wil@Wil-Desktop:~$ sudo mount -t ntfs /dev/sda2 XP
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda2 (Windows XP)
wil@Wil-Desktop:~$ sudo mount -t ntfs /dev/sda5 Vista
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda5 (Windows Vista)

---

### Post by meierfra on 2007-12-25
This sounds like that  XP and/or Vista did not shutdown right the last time you used it.  Did  you try "rootnoverify (hd0,1)"? 

If this  did not work I suggest to get SuperGrub (see my signature).   It might let you boot into XP and Vista. It also lets you fix the XP boot sector.

---

### Post by AimLXJ on 2007-12-25
I was never able to use WIndows XP nor WIndows VIsta when I had Ubuntu install. I'll try "rootnoverify (hd0,1)"

I have already tried SuperGrub but I don't I have tried fixing it since the menu was sort of complicated.

**EDIT**
**rootnoverify (hd0,1)**
> wil@Wil-Desktop:~$ rootnoverify (hd0,1)
bash: syntax error near unexpected token `hd0,1'


---

### Post by meierfra on 2007-12-25
No, you need to edit "menu.lst". Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```change

title Windows NT/2000/XP
root (hd0,1)
savedefault
makeactive
chainloader +1


to 

title Windows NT/2000/XP
rootnoverify  (hd0,1)
savedefault
makeactive
chainloader +1


and reboot.

---

### Post by meierfra on 2007-12-25
If you have problems with SuperGrub, you might read the Hermanzone info on SuperGrub (Click on SuperGrub  in my signature)


Do you have a  Vista CD?

---

### Post by AimLXJ on 2007-12-25
> This sounds like that XP and/or Vista did you shutdown right the last time you used it. Did you try "rootnoverify (hd0,1)"?
The computer just rebooted

> Do you have a Vista CD?
No but I have the upgrade CD if it helps

---

### Post by meierfra on 2007-12-25
> I was never able to use WIndows XP nor WIndows VIsta when I had Ubuntu install. 

But were you able to boot into Vista before you installed Ubuntu?
Can you describe  what you did when you installed Ubuntu? Did you delete any partitions? Did your resize  any partitions?
What program did you use  to resize? (gparted? Ubuntu installer?  Vista disk management.?)


> 
No but I have the upgrade CD if it helps

I Don't know.Does it has any kind of repair options?

---

### Post by AimLXJ on 2007-12-25
> But were you able to boot into Vista before you installed Ubuntu?
Yes

> Can you describe  what you did when you installed Ubuntu?
Well I just instlaled Ubuntu without a swap and converted the extra NTFS partition to ext3

> Did you delete any partitions?
No

> Did your resize  any partitions?
Yes

> What program did you use  to resize?
Norton PartitionMagic 8.0

> I Don't know.Does it has any kind of repair options?
I don't know, I haven't tried it yet.

---

### Post by meierfra on 2007-12-25
Did you resize the Vista Partition with "Norton Partition Magic 8"?   I just googled  it and it seems it cannot handle Vista.

---

### Post by AimLXJ on 2007-12-25
> **meierfra said:**
> Did you resize the Vista Partition with "Norton Partition Magic 8"?   I just googled  it and it seems it cannot handle Vista.

No, I resized the Windows XP partition and I did the partition on Windows XP.

---

### Post by meierfra on 2007-12-25
> I did the partition on Windows XP.

??? what does that mean.

Please explain in more details what you did. If  you  just resized the Windows partition,  then  I don't understand how Ubuntu could be inside the extended partition

---

### Post by AimLXJ on 2007-12-25
> **meierfra said:**
> ??? what does that mean.

Please explain in more details what you did. If  you  just resized the Windows partition,  then  I don't understand how Ubuntu could be inside the extended partition

I booted into Windows XP and made a new partition under it, I used the program called Norton PartitionMagic 8.0 to do the job. Once it was finished making a partition I rebooted twice and installed Ubuntu. I soon found out that Ubuntu cannot bei nstlaled onto a NTFS partition so it made it into a ext3 and then installed Ubuntu in the partition.

---

### Post by meierfra on 2007-12-25
Well,  in order to do that, Norton Partition Magic had to move  the Vista partition.  So I'm pretty much  convinced that Norton Partition Magic damaged Vista.  Some of the booting information for XP might by on the Vista partition, so you cannot boot XP either. 

So you need to somehow repair Vista or reinstall Vista.  I don't know enough about Vista to help you with that. 

Just for future references:
After you repaired or reinstalled Vista you probably need to reinstall grub. To do that boot from the Ubuntu LiveCd, open a terminal  and  type

```
  sudo grub 
```

and at  the "grub>" prompt:

```
root (hd0,5)
setup (hd0)
quit

```

---

### Post by heatpumpcontrol on 2007-12-25
Hi again, I'm back. ---please read entire post---

OK from what it seems, your ntloader or your boot.ini files on both XP and Vista are not pointing to the correct partition. Their is a way to recover that using the install CD of XP by booting off the CD then at the prompts request a 'Repair using console'. Then you have to enter your Admin password and edit your boot.ini file. 

I'm not too certain about all the steps but I believe they go like this:
at the command prompt enter
boot.ini
fixboot

then you have to tell the O/S to show hidden files (boot.ini)

attrib -H -S -R boot.ini

You then have to edit the boot.ini and this is where I don't remember the next steps.. It will look something like we were talking about:
Window XP partition (disc,0 partition,1) or something like this. You might want to do a search for this.

The other and probably easier way is to just do a reinstall of XP but DON'T delete your previous install, just tell it to repair the installation. If you need help with that just let me know or google it. ---> this option might be faster. Then you can run the repair on the Vista partition in the same manner but as meierfra mentioned, you'll have to repair grub because Windows will override it as they feel they're the only O/S that people want to install. 

Follow his steps above to repair grub...

---

### Post by AimLXJ on 2007-12-26
Okay I fixed it, it seems like I can use the upgrade disc to fix it.

Here's the step for those that might bump into it in the future

1. Insert the Windows Vista disc(Windows VIsta Upgrade disc is fine)
2. When it finishes loading a window should appear and click on the button "Next"
3. After that, look for something that says Repair WIndows(sorry I cannot remember)
4. Now a list should appear and pick the one located all the way on the bottom which is MS-DOS
5. Now another window should appear and type this in: Bootsect.exe /fixmbr
6. Now reboot your PC and get into your Windows Vista then download this program: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
7. Once EasyBCD is installed under Windows Vista run it, then click on the button "Add/Remove Entries"
8. Click on the "Linux/BSD" tab and add Linux onto it
9. Once it has been added save it and reboot your PC
10. Now you'll see Windows XP, Windows Vista, and Linux together ;)

Now I can finally triple boot in a way :P

---

### Post by heatpumpcontrol on 2007-12-26
Alright! glad to hear that. Maybe you can mark this thread as "Solved" so others can reference it a lot quicker....

---

