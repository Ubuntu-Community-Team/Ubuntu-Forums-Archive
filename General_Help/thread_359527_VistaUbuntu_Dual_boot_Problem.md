---
title: "Vista/Ubuntu Dual boot Problem"
date: 2007-02-12
forum: General Help
---

### Post by PiZZLE on 2007-02-12
im very familiar with searching of this forum and also google, but i havent found a solution to my problem. so i did a clean format of my XP/Ubuntu Partition, installed Vista and left around 80 gigs for my Ubuntu Install. Vista installed on a 100g NTFS partition, so i took the other 80 and broke it down to 2g swap, 20g ext3 for / and another 20g ext3 for /home. now here is the problem, when i boot up, Grub doesn't load, it goes to the Windows OS selector asking me to pick between Vista and "earlier version of windows" when i dont even have an older version of windows on this system anymore, and i dont even have an option for Ubuntu. what am i doing wrong? also is there resolution to bluetooth keyboard working in grub yet? thanks ahead of time.

---

### Post by jazzgossen on 2007-02-12
Looks like Vista overwrote your boot record. To repair that, you need your Ubuntu install disc. I don't remember the exact steps to take, but there should be a "repair" boot option there somewhere. You can also try looking at [this guide]("www.thinkwiki.org/wiki/Rescue_and_Recovery").

---

### Post by PiZZLE on 2007-02-12
well, trying to restore grub didn't work either....any other ideas?

---

### Post by 13thMonkey on 2007-02-12
If you can't boot into root with the LiveCD and edit your grub menu.lst file from there then try the Super Grub Disk [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) 

I had a similar problem when I reinstalled XP a few weeks back and rather than try to remember the correct incantations I used the SGD to guide me through the process :)

---

### Post by rsambuca on 2007-02-12
This should be really easy to fix.  What instructions did you follow exactly to try and restore grub?

Edit:  I was talking to PiZZLE

---

### Post by 13thMonkey on 2007-02-12
I wish I could remember! I do know that I had grub installed on the MBR though (with XP and Linux on the first and second partitions of hda). Come to think of it, I think I may have had a Gentoo install on the second partition at the time, but the principle is the same. 

Since you have internet access (I didn't at the time) you might want to try [this]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by PiZZLE on 2007-02-12
> **rsambuca said:**
> This should be really easy to fix.  What instructions did you follow exactly to try and restore grub?

Edit:  I was talking to PiZZLE

i tried this method [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) and also the SGD which i tried all 3 options under fix linux

both of them said succesful but neither worked =(

---

### Post by rsambuca on 2007-02-12
Do you have more than one hard drive? (one SATA one IDE?)

Also, the older version of windows that the Vista bootloader is seeing could be a hidden recovery partition - I have one on my drive from XP.

---

### Post by PiZZLE on 2007-02-12
> **rsambuca said:**
> Do you have more than one hard drive? (one SATA one IDE?)

Also, the older version of windows that the Vista bootloader is seeing could be a hidden recovery partition - I have one on my drive from XP.

yea more than one HD, i have 3....how can i fix all this?

---

### Post by rsambuca on 2007-02-12
I suspected as much.  What type are they?

---

### Post by 13thMonkey on 2007-02-12
I'm not au fait with the way Windows boots (other than what I've read), but from what I've seen Vista has tried to do away with boot.ini I don't know if GRUB has caught up with that (I'm sure it has though) but try googling bcdedit

Other than that I'm sure somebody that knows what they're talking about will be along soon to help :confused:

---

### Post by PiZZLE on 2007-02-12
> **rsambuca said:**
> I suspected as much.  What type are they?

2 IDE and 1 Sata.

---

### Post by rsambuca on 2007-02-12
Sounds just like my setup!  I assume that your rig came with an IDE drive, and you subsequently added a slave IDE and a SATA drive?

Which drive did you load the OS's onto?  There can be a problem with mixed SATA and IDE drives as the bios has to guess the boot order.

---

### Post by PiZZLE on 2007-02-13
> **rsambuca said:**
> I suspected as much.  What type are they?

my main with vista/ubuntu is off of a IDE, i got 2 backups, one with SATA and one with IDE....

---

### Post by rsambuca on 2007-02-13
Allright,  can you post your your menu.lst and your fstab outputs please?

---

### Post by PiZZLE on 2007-02-13
> **rsambuca said:**
> Allright,  can you post your your menu.lst and your fstab outputs please?

can i do that from the live CD? if so how do i do it so i can paste it for you...

edit: i tried using the live CD, but since ubuntu is loaded into ram it wont let me bring up fstab and menu.list for grub that i installed earlier...

---

### Post by rsambuca on 2007-02-13
You can do it using the liveCD, you just have to mount the drives first.

First, make a directory to mount your linux partition to:```
sudo mkdir /mount/linuxdrive
```(you can call it whatever you want instead of "linuxdrive")
Next, mount your linux partition to the directory you just created, although  from your instructions I don't know what partition it is.  If you don't know you should be able to tell by using the gnome partition editor on the live CD, and just go by the sizes and usage amounts of the partitions.  eg. if it is hda2```
sudo mount /dev/hda2 /mount/linuxdrive
```
then ```
sudo mount -a
``` to make sure the drives are mounted
then if you go to places, there will be a directory in mount called linuxdrive containing all of your files on that partition.

---

### Post by PiZZLE on 2007-02-13
> **rsambuca said:**
> You can do it using the liveCD, you just have to mount the drives first.

First, make a directory to mount your linux partition to:```
sudo mkdir /mount/linuxdrive
```(you can call it whatever you want instead of "linuxdrive")
Next, mount your linux partition to the directory you just created, although  from your instructions I don't know what partition it is.  If you don't know you should be able to tell by using the gnome partition editor on the live CD, and just go by the sizes and usage amounts of the partitions.  eg. if it is hda2```
sudo mount /dev/hda2 /mount/linuxdrive
```
then ```
sudo mount -a
``` to make sure the drives are mounted
then if you go to places, there will be a directory in mount called linuxdrive containing all of your files on that partition.

i got this error

"mkdir: cannot create directory `/mount/linux': no such file or direcotory"

edit: alright my dir is called /mnt i got the drive mounted as "linux" now where are the 2 files you want the outputs from?

---

### Post by PiZZLE on 2007-02-13
alright got it all squared away, here are what both files say

menu.lst
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
# kopt=root=UUID=d6017b08-3987-4719-b81c-c4bf93952925 ro
# kopt_2_6=root=/dev/hda3 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


```

fstab output
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=d6017b08-3987-4719-b81c-c4bf93952925 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=2272274e-3134-4ba3-a3f5-eb10c6461b87 /home           ext3    defaults        0       2
# /dev/hda1
UUID=16B81E51B81E302B /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=BC5AD4FD5AD4B57C /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=5ED083DED083BAB3 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=61120903-ea5e-446a-9e35-c454b380bbf5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by rsambuca on 2007-02-13
OK, I have an idea of what is going on.  Hopefully last question before we try to fix:  What order are the drives listed in your system Bios?

---

### Post by PiZZLE on 2007-02-13
> **rsambuca said:**
> OK, I have an idea of what is going on.  Hopefully last question before we try to fix:  What order are the drives listed in your system Bios?

whats the easiest way to pull that? just go into my bios and list the order?

---

### Post by rsambuca on 2007-02-13
Yeah, if you enter the bios (using esc, or F12, or whatever it is for your machine), there will be a section on either hard drives, or boot order options, something like that.

---

### Post by PiZZLE on 2007-02-13
> **rsambuca said:**
> Yeah, if you enter the bios (using esc, or F12, or whatever it is for your machine), there will be a section on either hard drives, or boot order options, something like that.

ok goes something like this:

IDE Channel 1 Master: IDE 200 gig (with the first 100gb is vista and the rest is for Linux)
IDE Channel 1 Slave: IDE 500gb backup NTFS
IDE Channel 2 Master: IDE Pioneer DVDRW
IDE Channel 2 Slave: nothing
IDE Channel 3 Master: SATA 320gb NTFS
IDE Channel 4 Master: Plextor DVDRW

---

### Post by rsambuca on 2007-02-13
Allright, here's what I would try (I am assuming you are positive that Vista is on the master IDE drive, and not the SATA drive that grub has assumed):

1.  ```
sudo gkedit /boot/grub/menu.lst
```
make the following changes to your grub:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/[COLOR="Red"]hda1[/COLOR]
title		Windows Vista/Longhorn (loader)
root		[COLOR="Red"](hd0,0)[/COLOR]
savedefault
makeactive
[COLOR="DarkOrchid"]map		(hd0) (hd2) ->DELETE this line
map		(hd2) (hd0) ->DELETE this line
[/COLOR]chainloader	+1
```
save and exit the editor.

2. ```
sudo grub
```
at the grub prompt:
```
root (hd0,2)
```
```
setup (hd0)
```
type quit to exit grub.

Shut down and take out the live CD.

Cross Fingers

Cross toes

Try and reboot from the Hard drive.

Let me know what happens.

---

### Post by pxwpxw on 2007-02-13
rsambuca


Please ignore, covered by code above by rsambuca. 
=================================

 Its been a while since I used either grub or windows (xp), but if your treatmnent above 
  doesnt fix it you might like to consider:


 and the mbr is still booting the windows loader at hda1 (hd0,0).

---

### Post by PiZZLE on 2007-02-14
> **rsambuca said:**
> Allright, here's what I would try (I am assuming you are positive that Vista is on the master IDE drive, and not the SATA drive that grub has assumed):

1.  ```
sudo gkedit /boot/grub/menu.lst
```
make the following changes to your grub:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/[COLOR="Red"]hda1[/COLOR]
title		Windows Vista/Longhorn (loader)
root		[COLOR="Red"](hd0,0)[/COLOR]
savedefault
makeactive
[COLOR="DarkOrchid"]map		(hd0) (hd2) ->DELETE this line
map		(hd2) (hd0) ->DELETE this line
[/COLOR]chainloader	+1
```
save and exit the editor.

2. ```
sudo grub
```
at the grub prompt:
```
root (hd0,2)
```
```
setup (hd0)
```
type quit to exit grub.

Shut down and take out the live CD.

Cross Fingers

Cross toes

Try and reboot from the Hard drive.

Let me know what happens.

didn't work....

---

### Post by rsambuca on 2007-02-14
What did it say?

---

### Post by PiZZLE on 2007-02-14
> **rsambuca said:**
> What did it say?

nothing, just went back into booting to vista through the Windows Boot manager

---

### Post by rsambuca on 2007-02-14
Ok, this is really frustrating me, but I am sorry I have to go to bed now.  Too tired!

---

### Post by PiZZLE on 2007-02-14
> **rsambuca said:**
> Ok, this is really frustrating me, but I am sorry I have to go to bed now.  Too tired!

i really appreciate all the help. i noticed something

on the last step when in a grub prompt when i do "setup (hd0)" it says a few lines and they are successful like "/boot/grub/menu.lst success" blah blah blah. remember im running off of a live CD so that dir doesn't really exist, my menu.lst is in /mnt/linux/boot/grub/menu.lst does that make sense?

---

### Post by pxwpxw on 2007-02-14
PiZZLE 

I think that would have restarted to grub, then given errors.

Stay with rsambuca, but while waiting, you might recheck your BIOS setup,
for the boot disk order setting.

Are you sure that was the boot order?

The listing you gave:

IDE Channel 1 Master: IDE 200 gig (with the first 100gb is vista and the 
 ..... 
and so on.

looks nore like just a listing of all the drives.

For example my (old) PC bios lists:

 First boot FD
 Second boot CD
 Third Boot HD1

and so on.

---

### Post by PiZZLE on 2007-02-14
ahhh, yes, it says HD....thats all second is CD

---

### Post by pxwpxw on 2007-02-14
ok, but which hd?

---

### Post by PiZZLE on 2007-02-14
pxwpxw you nailed it on the head. it was booting HD first, but which HD? so while i was in bios i saw a option that said "HD BOOT SELECTION PRIORITY" and guess what my master HD was not priority, so now everything is working. wanted to thank both of you, especially sambuca for spending so much time. you guys really show what the linux community is about, helping eachother, and i commend both of you. thanks a lot!

---

### Post by pxwpxw on 2007-02-14
Very glad to hear that. Happy ubunting.

---

### Post by rsambuca on 2007-02-14
w00t!!  Glad you got it working!  It was really starting to bug me.  I knew it had to be the order of your bios after my last set of instructions didn't work.  In any event, have fun in the linux world!

---

### Post by PiZZLE on 2007-02-14
> **rsambuca said:**
> w00t!!  Glad you got it working!  It was really starting to bug me.  I knew it had to be the order of your bios after my last set of instructions didn't work.  In any event, have fun in the linux world!

if either of you know how to setup bluetooth kb and mouse let me know =)
i used to have dapper drake working perfectly until my HD crashed.

---

### Post by pxwpxw on 2007-02-14
> **PiZZLE said:**
> if either of you know how to setup bluetooth kb and mouse let me know =)
i used to have dapper drake working perfectly until my HD crashed.
Nope, not me. I'd try a new thread for that.

---

