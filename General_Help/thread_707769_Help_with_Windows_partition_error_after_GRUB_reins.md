---
title: "Help with Windows partition error after GRUB reinstall"
date: 2008-02-25
forum: General Help
---

### Post by novellterminator on 2008-02-25
I had Ubuntu and Vista running smoothly from GRUB. Yesterday I was playing around with a Vista boot manager program (shame on me), and it set Vista as the primary boot loader (disabling GRUB).

I put my Ubuntu (alternative install (because I have a 8800GT)) disc in, and choose to start from the hard drive instead of installing. But to my surprise (perhaps because I'm a newbie) GRUB loaded again.

Note: I thought the problem was fixed after that, so I took out the CD, restarted, and it was back to booting directly to Vista.

SO! I put my CD back in and loaded Ubuntu. After researching online, I tried reinstalling GRUB using:

```
sudo grub-install /dev/sdb1
```

Tada! GRUB was fixed! Needless to say, I was very happy with myself. But to my unpleasant surprise, I couldn't get Vista to load anymore. When I selected the Vista boot partition, after a black screen flashing for half a second, GRUB automatically restarted.

I also had to go into menu.lst and change my Ubuntu partition to (hd0,1) to get it working. It's currently set at:

> title		Microsoft Windows Vista x64
root		(hd0,0)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1

title		Ubuntu Linux 7.10 x64
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c29ca424-139c-4cc6-99f3-e7ece0dfb509 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

Note that I commented out the maps, because I had no idea what they did, and I was trying to test different partitions via (hd#,#) to see if the Windows partition had simply moved, like the linux.

I tried my Vista DVD > Repair Startup, but that didn't work. And I can't access my NTFS drive from the terminal in the Vista repair terminal.

Ubuntu still sees my two NTFS partitions (1 contains the OS, the another is a different physical hard drive), but is no longer able to mount them.

I get this error when I try to access the hard-drive with Vista and Linux on it:

> Unable to mount the volume.

Details: Unexpected cluster per mft record (-1). Failed to mount '/dev/sdb1': Invalid argument The device '/dev/sdb1' doesn't have a valid NTFS. Maybe you selected the wrong device? Or the whole disk instead of a partition? Or the other way around?

And my other NTFS drive (not external) with just data gives the error:

> $LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: (Says here how to go through windows "safely remove hardware")
Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line:

>> mount -t ntfs-3g /dev/sda1 /media/disk -o

^ This doesn't work, it says "mount: option requires an argument -- o"

> (continued:) force   Or add the option to the revelant row in the /etc/
fstab file: /dev/sda1 /media/disk ntfs-3g defaults,force 0 0

^ Outputs "bash: /dev/sda1: Permission denied". I tried as sudo and it says "sudo: /dev/sda1: command not found" (Remember I'm a newbie so don't make fun, I'm trying :))

Sorry for the long post. I tried to include as much information as possible. Does anyone know how to fix these problems?

(Also, is there a command I can run in the terminal to see the drives and partitions in "(hd#,#)" format? I searched around on the web, but all I got was "sudo fdisk -l" which shows it in the "/dev/sda#" format. I need to know what partition Vista is now on so I can add it to GRUB.)

Thanks,
Derek

---

### Post by victor_gm on 2008-03-24
I have almos the same issues, only that I just have one NTFS partition, by the way I'm newbie too, I don't know how you got those outputs. Thanks.

---

### Post by victor_gm on 2008-03-26
Ok, I've read a little so now I can give more info, I hope this is not "confidential" info if so please tell me.
My menu.lst is

title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ee95ff6a-e95d-4422-93ed-77353d4f4288 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ee95ff6a-e95d-4422-93ed-77353d4f4288 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

when I try to mount NTFS this message prompts:

Unable to mount the volume.

Details: Unexpected cluster per mft record (-1). Failed to mount '/dev/sdb1': Invalid argument The device '/dev/sdb1' doesn't have a valid NTFS. Maybe you selected the wrong device? Or the whole disk instead of a partition? Or the other way around?

wich is the same novellterminator gets.

I attach a screensht of what happened when I opened Partition Editor.
At last if sudo fdisk -l gives me this:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08bf6cfe

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14358   115328000    7  HPFS/NTFS
/dev/hda2           14359       19242    39230730   83  Linux
/dev/hda3           19243       19457     1726987+   5  Extended
/dev/hda5           19243       19457     1726956   82  Linux swap / Solaris

WHAT I need: create a partition d: inside c: and retrive all the info from the win files to that partition so I can re-install win; because I think that I don't want to be in this situation again if I mess with the grub or something else (remember I'm very new to this). Thanks for your help

---

### Post by forrestcupp on 2008-03-26
> **novellterminator said:**
> 
Note that I commented out the maps, because I had no idea what they did, and I was trying to test different partitions via (hd#,#) to see if the Windows partition had simply moved, like the linux.


Lol.  You shouldn't just comment something out because you don't know what it does.  Uncomment the maps.  If Vista is really on hd0,0, the maps are probably your problem.

If it still doesn't work after you uncomment the maps, then give us the results of
```
sudo fdisk -l
```

---

### Post by forrestcupp on 2008-03-26
@victor_gm

If you don't have the 2 lines for the maps in your menu.lst like what the OP commented out, put them in and see if that fixes your problem.

---

### Post by victor_gm on 2008-03-26
Tahnks for teh tip, but i don't have the same menu.lst as novell his is 
title Microsoft Windows Vista x64
root (hd0,0)
savedefault
makeactive
[B]#map (hd0) (hd1)
#map (hd1) (hd0)[/B]
chainloader +1
mine
title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1
so I don't understand if you are saying I should put the same two map lines he has, if that's the case plese tell me. Thanks again.

---

### Post by forrestcupp on 2008-03-26
Yes, you need to have those two map lines in yours, only they shouldn't have the '#' at the beginning.

---

### Post by victor_gm on 2008-03-26
I did what you told, my menu.lst is know like this:

title		Windows Vista
root		(hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1

nothing changed, I mean I still can't mount the vista partition neither can "see" my files inside NFTS. The result of the fdisk -l is:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08bf6cfe

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14358   115328000    7  HPFS/NTFS
/dev/hda2           14359       19242    39230730   83  Linux
/dev/hda3           19243       19457     1726987+   5  Extended
/dev/hda5           19243       19457     1726956   82  Linux swap / Solaris

I think that's all.
Thanks again.

---

### Post by forrestcupp on 2008-03-26
you're going to have to post the entire contents of menu.lst, not just that small part.  This time, use the quote tags; it formats it better and makes your post look neater.

---

### Post by victor_gm on 2008-03-26
> **forrestcupp said:**
> you're going to have to post the entire contents of menu.lst, not just that small part.  This time, use the quote tags; it formats it better and makes your post look neater.
I hope this the quote thing yo said, her goes the entire menu.lst

# gfxmenu /boot/grub/message.ubugrey
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
# kopt=root=UUID=ee95ff6a-e95d-4422-93ed-77353d4f4288 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

title		Windows Vista
root		(hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ee95ff6a-e95d-4422-93ed-77353d4f4288 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ee95ff6a-e95d-4422-93ed-77353d4f4288 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root

---

### Post by Awperator on 2008-03-26
> **forrestcupp said:**
> you're going to have to post the entire contents of menu.lst, not just that small part.  This time, use the quote tags; it formats it better and makes your post look neater.

He means using the # button for '['CODE][/CODE']' when you are replying to a thread (without the single quotes).

Like this:
```

Hello. I have code in here, like menu.lst

```

---

### Post by 67GTA on 2008-03-26
Try running these in a terminal one at a time and post the output.

```
sudo grub
```
```
find /boot/grub/stage1
```

---

### Post by victor_gm on 2008-03-26
@ Awperator, let me see if I get it.

```
# gfxmenu /boot/grub/message.ubugrey
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
# kopt=root=UUID=ee95ff6a-e95d-4422-93ed-77353d4f4288 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

title		Windows Vista
root		(hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ee95ff6a-e95d-4422-93ed-77353d4f4288 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ee95ff6a-e95d-4422-93ed-77353d4f4288 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root
```

---

### Post by victor_gm on 2008-03-26
@67GTA After what you asked the result is:

```
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,1)
```

---

### Post by 67GTA on 2008-03-26
According to that you have grub installed to the Ubuntu partition instead of the boot sector. You might try installing grub to the boot sector. 

```
sudo grub
```
```
root (hd0,1)
```
```
setup (hd0)
```

---

### Post by victor_gm on 2008-03-26
Hi. I've done what you asked this is the output:

```
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
```
I'm going to restart................
I restarted and aperently nothing has changed, when I pick vista from the start menu still gets error 18 and freezes
I attach a screenshot or partition editor, it still flags /dev/hda1 ntfs as a boot partition.
The output of fdisk is:
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08bf6cfe

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14358   115328000    7  HPFS/NTFS
/dev/hda2           14359       19242    39230730   83  Linux
/dev/hda3           19243       19457     1726987+   5  Extended
/dev/hda5           19243       19457     1726956   82  Linux swap / Solaris

```

---

### Post by forrestcupp on 2008-03-27
When you are writing a post, you can press the quote button which will put the code to make a quote box in your post.  Look at my screen shot to see where the quote button is.  You just press that button and it will put the code in your post with your cursor in the middle.  Where it puts your cursor, just paste your contents there, then after that, you can continue typing the rest of your message after the end of the quote code.  When you use it, it's easier to understand than it is to explain.  I'll give you an example below, so you can see what it looks like.  But don't worry, because I was able to look through what you posted.

Now, about your problem.  The only thing I saw wrong is that your Windows entry should not be in the Automagic Kernels List.  It should either be before it or after it.  So what you should do is cut this whole section out:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

title Windows Vista
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
And paste it at the very end of menu.lst.  You need to do that even if it doesn't work.

Hopefully that will make it work.  I don't see anything else wrong.  If that doesn't fix it, then you have somehow screwed up your Windows installation.

---

### Post by 67GTA on 2008-03-27
I'm with forrestcupp, looks good to me unless you have changed a partition or something. What app was you playing with in windows, and what exactly did you do? One more thing to check is when you have gparted open, right click on the windows partition and make sure the box for boot is checked. You have makeactive in your menu.lst, but sometimes when grub is reinstalled, it activates the partition it was installed to.

---

### Post by victor_gm on 2008-03-27
Ok. I've pasted what you told me, still doesn't boot vista returns error 18. Still can't mount hda1 I aplied fdisk to hda1 an this happened:

> Disk /dev/hda1: 118.0 GB, 118095872000 bytes
255 heads, 63 sectors/track, 14357 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/hda1p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/hda1p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hda1p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/hda1p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Also I checked for the flag 67GTA says and it is ok. I was trying to change the grub to a nicer one more less this is what I did:
> #downloaded the new grub from here
```
[http://kanotix.com/debian/pool/main/g/grub-gfxboot/](http://kanotix.com/debian/pool/main/g/grub-gfxboot/)
```
picked the latest version for AMD64, meanwhile I chose a theme (message.ubu) from another site, then I followed these instructions```
$ sudo aptitude remove grub
$ sudo dpkg -i grub-gfxboot_x.xx-x_amd64.deb

```where x is the version number```
$ cat /boot/grub/menu.lst | grep kopt=root=/dev/
```this was to search for the output /dev/hd**, and that's where I think I messed up because as a newbie y just copy-paste, anyway I think I did this ```
sudo grub-install /dev/hda1
``` when I had to do this or viceversa ```
 sudo grub-install /dev/hda2
``` then I continued ```
sudo cp message.ubu /boot/grub/
sudo gedit /boot/grub/menu.lst
``` In order to put this line at first, wich I have comented right now ```
gfxmenu /boot/grub/message.ubu
```restart and that's it 

---

### Post by forrestcupp on 2008-03-27
So you installed a different version of GRUB?  Post a link to the instructions you followed to install it.  Also, post the results of this command in from a terminal
```
cat /boot/grub/message.ubu
```
I don't know what that is.  Maybe this new version of GRUB uses a different file for its settings, and maybe you were changing the wrong file.

---

### Post by victor_gm on 2008-03-27
Yes, I installed a new grub, I inserted the ubuntu 7.10 instalation disk and supossely fixed the grub right now I have an old grub running, but as I said still can't mount vista partition. When I write the command you asked inside the terminal I recieve a non "postable" answer, what I mean is than it starts writing a bunch of signs and characters, by the way the name of the theme I chose is message.ubugrey. I think I mentioned but in case I forgot the new grub was running well, even I managed to change the themes several times, but I found couldn't mount vista partition. The url for the instructions is [http://aneolf.blogspot.com/2006/09/grub-al-estilo-suse-para-u_115797336949533346.html](http://aneolf.blogspot.com/2006/09/grub-al-estilo-suse-para-u_115797336949533346.html)
they are in spanish, as you have wondered I speak spanish, that's why my english is so bad, although almost at the middle of the blog says **fuentes** which means **references**

---

### Post by forrestcupp on 2008-03-27
I suggest restoring your Windows boot loader to see if you can boot Windows at all.  Then you can restore GRUB, and hopefully it will work.

Get your Ubuntu Live CD out and go [here](http://ubuntuforums.org/showthread.php?t=622828) to find out how to use it to restore the Windows boot loader.  **Warning**, if this works you will not be able to boot to Ubuntu, so if Windows is just totally destroyed, you'll need to be able to access the next directions to get Ubuntu back.

After restoring the Windows boot loader, try rebooting *without* the CD to see if it just goes to Windows.  If that method didn't work, you can try the option on [the Super Grub CD](http://supergrub.forjamari.linex.org/) to restore Windows' boot loader.

Then reboot with your Ubuntu CD and follow [these directions](http://ubuntuforums.org/showthread.php?t=224351) to restore Grub.

Hopefully this will do a couple of things.  First, if you restore Windows boot loader and it still doesn't work, you know you've hosed your installation and if you care about it, you'll have to reinstall.  Second, if it *does* work, maybe this will fix a problem with the Windows loader that comes *after* the GRUB menu.

---

### Post by victor_gm on 2008-03-30
Ok, so far this is how I "solved" it, I was in a desperate situation then I inserted the vista restore disk and installed it in the c: partition, actually I have the doubt if it would have been better to just format, anyway vista installed and then I got a recovery sofware and could recover like 80% of the important info wich is the 10% of total amount I lost (lots of crap to the trash, although I miss my music), after all that I have the obvious problem (for the rest of the people not for me) of dual booting, if I try to restore the grub from the ubuntu cd vista won´t start again and have to reinstall it to run it, right now I'm using vista and searching for a way to make a dual boot from vista whithout messing it. Thanks to all for your help.

---

