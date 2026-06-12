---
title: "[SOLVED] Partition problems ; Unabe to boot"
date: 2007-11-14
forum: General Help
---

### Post by Catalonian on 2007-11-14
Hey there,
I've got two 70 GB HD, which contained winXP and Ubuntu respectively.
I tried to make another partition on the HD that contained windows and now I can't boot Ubuntu, neither windows.
I think I messed with the boot partition. I'm sure that Ubuntu is untouched but I cant boot it; I could reinstall it and everythng would be fine but I'd like to try to recover it :/.

Can anyone help? the HD which contains ubuntu has 3 partitions, I suppose that one's for root, another for swap and I dont know what does the last one contain (I didnt touch these partitions, they are the default from an Ubuntu intallation).

I could even install another ubuntu at first HD to have something to work on (some partitioning /boot editing tool?)

Maybe I could do if someone told me the 3 lines that tell where the OS is located (hd1 in my case), where's the kernel and can't remember what the last line contained (I can still edit lines where it used to ask me what I wanted to boot, linux or windows)  :confused:

Thx a lot guys

EDIT: using Gutsy Gibbon btw

---

### Post by bumanie on 2007-11-14
Need a little bit more information.
What tool did you use to partition the hard drive?
Can you boot windows or is it both windows and ubuntu that you can't boot?

---

### Post by RudolfMDLT on 2007-11-14
Hi there,

You're going to have to give more information! :) 

If Ubuntu did boot before you messed around with the partition tables and it doesn't boot now it means that GRUB can't find anything to boot on the drive specified or the drive doesn't exists any more.

What you need to do is insert the live disc, open the partition editor and see that all the drives are still "Alive". Anything broken or unformatted will appear in as a grey box. Then if you still need help, please tell where your drives are located and what is on them, ie root or home ect...

Inorder to tell what's in a drive, use gparted to identify the drive, that is, "/dev/hda1" or "/dev/sdb3".

Then in the terminal as root type:
> 
sudo mkdir /drive1

chmod 777 /drive1

mount /dev/sd?? /drive1

ls /drive1


Goodluck,

Rudolf


EDIT: The file you are looking for is here: 

> /boot/grub/menu.lst

and the contents that you want to edit is:

> title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic[COLOR="Red"] root=UUID=12e6200b-7b04-4a0b-9c80-da775c5b9f31[/COLOR] ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet


where the red bit specifies the root drive. Using a UUID is another way of saying /dev/somedrive. PLEAE DON'T EDIT IT YET. Lets first identify the problem before you hack away at a config file that might not be broken!

---

### Post by Catalonian on 2007-11-14
Oh my, two answers already, thats awesome :)

I was trying to install Gentoo in a little partiton on my first HD, the one containing windows.
After some problems, I decided to use the default partitons in the gentoo installer (which would erase windows), but I didn't know it would not let me to boot Ubuntu (on the other drive).

Now, at startup, I only get the option to get into gentoo but cannot select Ubuntu. I can edit the lines there (all look like the last lines you posted, Rudolf :)).
I can post them if you need. 

I have not yet tried what you said about the live cd, I've got to download it again (70% :P).

---

### Post by RudolfMDLT on 2007-11-14
I tried Mandriva and it killed Ubuntu to! :)

Anyway, with the live disc, identify the drive with thw folder /boot in it and also make sure that /boot is not empty. A long story cut short, /boot resides on /, but the contents of /boot may reside on a different partition! :confused: :)

So, find boot, and tell me the exact location, ie /dev/sdb1, and I can help you write the startup but for Ubuntu.... hopefully!

What version of Ubuntu is currently on your pc?

Please post the contents of the /boot folder, the full file names.

---

### Post by Catalonian on 2007-11-14
Ok:

Using the partition manager I found that in the first drive I have

> /dev/sda1  ; ext2 of 100Mb
/dev/sda2 ; linux-swap of 2 GB
/dev/sda3 ; ext 3 of 68GB
and 5 unused GB

This is where Gentoo is installed.
Now, on the drive where I have Ubuntu there is:

> /dev/sdb1 ; ext3 of 71GB
/dev/sdb2 ; extended of 3GB which has a /dev/sdb5 inside it of the same size (linux-swap)

After mounting the /dev/sdb1 I went to root.
ls from that folder:

> 
abi-2.6.17-10-generic
abi-2.6.17-11-generic
abi-2.6.20-16-generic
abi-2.6.22-14-generic
config-2.6.17-10-generic
config-2.6.17-11-generic
config-2.6.20-16-generic
config-2.6.22-14-generic
grub (folder)
initrd.img-2.6.17-10-generic
initrd.img-2.6.17-11-generic
initrd.img-2.6.17-11-generic.bak
initrd.img-2.6.20-16-generic
initrd.img-2.6.20-16-generic.bak
initrd.img-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak
memtest86+.bin
System.map-2.6.17-10-generic
System.map-2.6.17-11-generic
System.map-2.6.20-16-generic
System.map-2.6.22-14-generic
vmlinuz-2.6.17-10-generic
vmlinuz-2.6.17-11-generic
vmlinuz-2.6.20-16-generic
vmlinuz-2.6.22-14-generic



And ls from grub:

> 
default
device.map
e2fs_stage1_5
fat_stage1_5
installed-version
jfs_stage1_5
menu.lst
menu.lst~
minix_stage1_5
reiserfs_stage1_5
stage1
stage2
xfs_stage1_5


I'm using Gutsy Gibbon (I read the installed-version file from grub and it says 0.97-11ubuntu14).

If you need anything else, just ask! :)

---

### Post by RudolfMDLT on 2007-11-14
Sorry, I should have asked for this earlier, What do you see in grub when you boot. is it the Gentoo grub or the original Ubuntu grub?

In either case, could you please paste the contents of your current grub menu.lst file. You can find it in /boot/grub.

Could you also please confirm this for me:
> After mounting the /dev/sdb1 I went to root.
ls from that folder:

Quote:
abi-2.6.17-10-generic
abi-2.6.17-11-generic

Are you saying that that you "went to root" as in you became root and the said "ls /driveX/boot" or when you said "ls /" the above appeared? I need to know EXACTLY where root(/) lies and boot(/boot) lies and also whether / and /boot are ons the same partition. that is, when you mount driveX, "ls /driveX" will produce something like:
>  
bin
boot
cdrom
debian
dev
etc
home
initrd
initrd.img
lib
lost+found
media
mnt


and "ls /drveX/boot":
> 
abi-2.6.22-14-generic
config-2.6.22-14-generic
grub
initrd.img-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak
initrd.img-2.6.22-14-generic.dpkg-bak
memtest86+.bin
System.map-2.6.22-14-generic
vmlinuz-2.6.22-14-generic


Thanks,

Rudolf

---

### Post by Catalonian on 2007-11-14
I see the Gentoo grub with just one option (getting into gentoo).

ls /drive1/boot generates:

> 
abi-2.6.17-10-generic
abi-2.6.17-11-generic
abi-2.6.20-16-generic
abi-2.6.22-14-generic
config-2.6.17-10-generic
config-2.6.17-11-generic
config-2.6.20-16-generic
config-2.6.22-14-generic
grub (folder)
initrd.img-2.6.17-10-generic
initrd.img-2.6.17-11-generic
initrd.img-2.6.17-11-generic.bak
initrd.img-2.6.20-16-generic
initrd.img-2.6.20-16-generic.bak
initrd.img-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak
memtest86+.bin
System.map-2.6.17-10-generic
System.map-2.6.17-11-generic
System.map-2.6.20-16-generic
System.map-2.6.22-14-generic
vmlinuz-2.6.17-10-generic
vmlinuz-2.6.17-11-generic
vmlinuz-2.6.20-16-generic
vmlinuz-2.6.22-14-generic


ls /drive1 generates:

> 
bin
boot
dev
etc...and so on


contents of menu.lst:

> 
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
# kopt=root=UUID=85d33e5d-7856-43e0-a04a-1be619136c29 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=85d33e5d-7856-43e0-a04a-1be619136c29 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=85d33e5d-7856-43e0-a04a-1be619136c29 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=85d33e5d-7856-43e0-a04a-1be619136c29 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=85d33e5d-7856-43e0-a04a-1be619136c29 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.17-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=85d33e5d-7856-43e0-a04a-1be619136c29 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=85d33e5d-7856-43e0-a04a-1be619136c29 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu 7.10, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=85d33e5d-7856-43e0-a04a-1be619136c29 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=85d33e5d-7856-43e0-a04a-1be619136c29 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1



The nice guys with sunglasses are -> ( 8 )
:P

---

### Post by RudolfMDLT on 2007-11-15
Okay, I'm assuming that you can get into gentoo?

Boot into gentoo, and find gentoo's boot folder and the menu.lst file. It might be in the exact same place as the Ubuntu one but I'm not sure. Open the file as root. either in the terminal:

sudo nano /boot/grub/menu.lst

of I think by pressing ALT + F2

Bow depending on whether you are running KDE or Gnome enter one of the following:

Gnome: "gksu gedit /boot/grub/menu.lst"
KDE: "kdesu kate /boot/grub/menu.lst"
where /boot/grub/menu.lst is the real location that you found the Gentoo grub to be.

Now that we are in the Gentoo grub's menu file let's add the Ubuntu boot bit; at the bottom of the file paste the following:

> 

title           Ubuntu, kernel 2.6.22-14-generic
[COLOR="Lime"]root            (hd1,0)[/COLOR]
kernel          /boot/vmlinuz-2.6.22-14-generic [COLOR="Lime"]root=/dev/sdb1[/COLOR] ro [COLOR="Red"]quiet splash[/COLOR]
initrd          /boot/initrd.img-2.6.22-14-generic
[COLOR="Red"]quiet[/COLOR]
savedefault
boot



The above is assuming that you where correct with telling that /dev/sdb1 is where Ubuntu root is.

DO NOT enter the red text yet. this is so that if Ubuntu does load, it will not display the Ubuntu Logo and it will tell you as much as it can about the boot process so that we can hunt for trouble.

If you cannot boot Gentoo, in the grub menu, select the Gentoo boot option and press "e". Now write down on pen and paper how each line looks. After you have created a hard copy backup, erase all the lines and type in the above quoted menu entry(which you printed or wrote down by hand :) ).

Best of luck,

Rudolf

PS: Please verify that root is on /dev/sdb. that would translate to: (hd2,0).
If it does not boot, in the grub menu list, edit the following lines until it does boot:
root            (hd2,[COLOR="Blue"]0[/COLOR])
root=/dev/sdb[COLOR="Blue"]1
[/COLOR]
([COLOR="Purple"]hd2[/COLOR],[COLOR="Blue"]0[/COLOR]) means sdC1, that is hard drive 3, partition 1
(hd1,3) means [COLOR="Purple"]sdB[/COLOR]3, that is hard drive 2, partition 3.
notice that it starts counting at 0 but that there is no Zero in the Alphabet! ;) so A =0

incrementally change the the [COLOR="Blue"]0/partition[/COLOR] upwards and then start changing the[COLOR="Purple"] hard drives[/COLOR] and begin at partition 1 again.


I hope I didn't confuse you too much with my silly explanation! :)

EDIT: Before you start, see if you can familiarise yourself with the grub menu list entry and where it points to and what every command means. This is just to help when you need to trouble shoot.

---

### Post by Catalonian on 2007-11-15
Ok, with that bit of code you provided, when I select Ubuntu from the grub it says:

> 
Booting 'Ubuntu, kernel....'

root (hd1,0)
   Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb1/ ro quiet splash
   [Linux-bzImage, setup=0x1e00, size=0x1acbb8]
initrd /boot/initrd.img-2.6.22-14-generic
   [Linux-initrd @ 0x1f905000, 0x6ea749 bytes]
savedefault

Error 15: File not found

Press any key to continue...


I'm pretty sure that root resides on /dev/sdb1/ and boot's on /dev/sdb1/boot
HD must be hd1 and when I used partition editor on the live cd it said I had 3 partitions : sdb1,2 and 5, so the first one must be 0 (root (hd1,0)).

I'll paste what's inside gentoo's menu.lst, hope it helps:

> 
default 0
timeout 30
splashimage=(hd0,0)/grub/splash.xpm.gz
title=Gentoo Linux
root (hd0,0)
kernel /kernel-genkernel-x86-2.6.19-gentoo-r5 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda3 doscsi
initrd /initramfs-genkernel-x86-2.6.19-gento-r5

title Ubuntu, kernel 2.6.22-14-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb1/ ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet
savedefault
boot


---

### Post by RudolfMDLT on 2007-11-15
Sorry for the late reply.

I think we may be able to fix this by editing in the correct info into the menu.lst file. But I think you'd rather get into Ubuntu as quick as possible. I have no idea what's going on in Gentoo's grub config file.

This might erase the Gentoo grub but then we can add that later as we know what works and you have a copy saved here on the forum.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The above should fix grub and won't take too long. You should only need the first bit of info not the extra stuff. Post back as soon as you can and again, sorry for the late reply.

---

### Post by Catalonian on 2007-11-16
Oooh finally, thanks!
That worked really well, can't get into gentoo but I don't really care if you ask me.. I won't bother trying to fix that ;)
I'll just install windows on it when I get the cd and if I lose grub again I'll just have to do the same I've done now.

Thanks again mate, you make the Ubuntu forums community a lot better caring in that way for other users ; now if I got any problem, I know who to ask to! :P

---

### Post by RudolfMDLT on 2007-11-16
Catalonian - I was so glad when I saw the [SOLVED] marker! I was dreading the grub fix not working! ;) LOL :guitar:

> title           Microsoft Windows XP Professional
[COLOR="Red"]root            (hd0,0)[/COLOR]
savedefault
makeactive
chainloader     +1


Here is the WinXP boot entry in the menu.lst file - you know by now to change the red bit to the relevant entry, the partition with /windows on it! :) 

Best of luck,

Rudolf

---

