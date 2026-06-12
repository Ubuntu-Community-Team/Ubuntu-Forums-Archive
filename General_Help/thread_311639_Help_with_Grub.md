---
title: "Help with Grub"
date: 2006-12-03
forum: General Help
---

### Post by damu on 2006-12-03
I had to reinstall WinXP after a "hal.dll missing...". THe first time I used my WinXP cd to try to repair, it deleted the grub (expected), even though I didn't go further than the first steps (let it load and select'manual edit' for the partitions...) and cancelled the installation . The second time (with the same procedure), my fat32 partition (hd4)with all my datas disappeared. I jus't couldn't believe it.I now have a nice 115 Go of free space.

Here is the structure on my HD :
-hda1 :WinXP
-hda2 :Studio-to-go
-hda3 :Ubuntu
-hda4 : empty partition (previoulsy fat 32 with my datas)
-hda5 :swap

I reinstalled WinXP on hda1. I tried to restore the grub, following an ubuntu wiki method using a dapper live cd with no success. 
I can gedit /boot/grub/menu.lst on hda3, but I don't know how to reinstall it on the MBR, and I didn't find yet any way which would work for me in the forum or wiki. Need you help here

Thanks.

---

### Post by Sef on 2006-12-03
Have you tried [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub")?

---

### Post by bulldog on 2006-12-03
Try this one with the live cd,
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by damu on 2006-12-03
Thanks for your help.

I tried this method already. It is in the forum and the wiki.

I tried it again so that I can give an accurate report.
When I do > find /boot/grub/stage1 
I get  2 answers :
(hd0,1)
(hdo,2)

When I go on with  (hd0,1), and reboot, I get a black screen with a bizarre little sign at the bottom center-right of the screen (a square which include a triangle under 2 dots )

When I go on the procedure with (hdo,2), and reboot, I get : Reboot and select proper boot device.

I can use the disk manager from the live cd to mount hda3 and therefore edit boot/grub/menu.lst :

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
# kopt=root=UUID=17a12407-10af-4d04-b1e7-af5dce23e389 ro

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
##      altoptions=(single-user) single
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


title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=17a12407-10af-4d04-b1e7-af5dce23e389 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=17a12407-10af-4d04-b1e7-af5dce23e389 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.6.17.6-rt7-ubuntumusique
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17.6-rt7-ubuntumusique root=UUID=17a12407-10af-4d04-b1e7-af5dce23e389 ro quiet splash
initrd		/boot/initrd.img-2.6.17.6-rt7-ubuntumusique
savedefault
boot

title		Ubuntu, kernel 2.6.17.6-rt7-ubuntumusique (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17.6-rt7-ubuntumusique root=UUID=17a12407-10af-4d04-b1e7-af5dce23e389 ro single
initrd		/boot/initrd.img-2.6.17.6-rt7-ubuntumusique
boot


title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda4.
title		Debian GNU/Linux, kernel (on /dev/hda4)
root		(hd0,3)
kernel		/boot/vmlinuz root=/dev/hda4 ro ramdisk_size=100000 init=/etc/init lang=uk apm=power-off nomce quiet vga=791 
initrd		/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda4.
title		Debian GNU/Linux, kernel 2.6.17-fervent (on /dev/hda4)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-fervent root=/dev/hda4 ro ramdisk_size=100000 init=/etc/init lang=uk apm=power-off nomce quiet vga=791 go sr=44100
savedefault
boot


So for now, I can't either boot in Ubuntu, WinXP, or STG.
Should I just reinstall Ubuntu Edgy and hope that it would detect the 2 other distros or is there another way to save the day?

thanks

---

### Post by bulldog on 2006-12-03
Can you give the outcome of```
sudo fdisk -l
``` and your fstab```
cat /etc/fstab
```

Looking at your menu.lst should (hd0,2)do the trick.

---

### Post by damu on 2006-12-03
Here there are :

> ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1974    15856123+   7  HPFS/NTFS
/dev/hda2            1975        2911     7526452+  83  Linux
/dev/hda3            2912        4743    14715540   83  Linux
/dev/hda4            4744       20023   122736600    5  Extended
/dev/hda5            4744        4825      658602   82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0

---

### Post by damu on 2006-12-03
So, what do u reckon I should try next?

thanks

---

### Post by bulldog on 2006-12-03
Can't find anything wrong in your menu.lst and your fstab.
But let me take a closer look it cost some time though.

---

### Post by bulldog on 2006-12-03
> **damu said:**
> I had to reinstall WinXP after a "hal.dll missing...". THe first time I used my WinXP cd to try to repair, it deleted the grub (expected), even though I didn't go further than the first steps (let it load and select'manual edit' for the partitions...) and cancelled the installation . The second time (with the same procedure), my fat32 partition (hd4)with all my datas disappeared. I jus't couldn't believe it.I now have a nice 115 Go of free space.



I'm not sure what you did here.
The procedure should be to boot into your windows disk,let it run till you come to 3 options.
1/Install Windows
2/Repair a Windows install
3/Exit without installing
Here you should choose the 'R' for repair option (2).
Now you should be taken to a console where your windows is listed,you provide the admin password and go to the recovery console.
Here you give the commands 'fixmbr' and 'fixboot'
Now exit the cd and reboot.
Windows MBR should be fixed.

You're talking about manual editing the partitions? what's that suppose to mean,and more important,what did you do?

Your menu.lst looks alright to me and I shouldn't know what to change there.

Your fstab```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1974 15856123+ 7 HPFS/NTFS
/dev/hda2 1975 2911 7526452+ 83 Linux [COLOR="Red"]<---- you are calling this studio-to-go  Why? Is this a Linux partition?[/COLOR]
/dev/hda3 2912 4743 14715540 83 Linux
/dev/hda4 4744 20023 122736600 5 Extended
/dev/hda5 4744 4825 658602 82 Linux swap / Solaris
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0
```

---

### Post by damu on 2006-12-03
When I had this problem with winXP, I don't know why, but I couldn't get to the repair console of XP with this cd(I don't have this problem with the WinXP cd of my vaio laptop). I gave up and decided to reinstall XP, which went ok. I could boot in WinXP.

After that , I tried to reinstall the grub so that I would have the possibilty of multi boot again(following the procedure of this post). 

Now, not only, can't I get the grub back, but I can't boot to WinXP either.

Any help much welcome

ps : [Studio-to-go]("http://www.studio-to-go.com") is a linux distro dedicated to audio production

---

### Post by bulldog on 2006-12-03
I can only advice to try and reinstall GRUB from the live cd again.
You should get just one location on the find command and that should be (hd0,2)watch the 0 zero instead of the o!!

Use,if you get two locations again,the (hd0,2) location for the root command.
Then setup (hd0) and it should work.

---

### Post by damu on 2006-12-03
Ok. so I did it one more time, so that I can copy and paste the teminal process :

>        [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,1)
 (hd0,2)

grub> root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>

I will now quit in the terminal and reboot. That's what I did the last 3 times with the same result - no grub at boot. But we never know. I'll be back in 5 minutes to tell you if it worked this time.

---

### Post by damu on 2006-12-03
I can now confirm that this method doesn't work for me. When I reboot from the HD, I get :
> Reboot and Select proper device or Insert Boot media in selected Boot device and press a key

Could anyone help me to sort this mess? If I could avoid to reinstall a working ubuntu edgy with packages that were not obvious to get working (keepass and so on) just for the sake of having grub working that would be great. :???: 

Thanks for ur help

---

### Post by damu on 2006-12-04
I finally manage to restore the grub by following the method given in this [wiki]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") with an alternate/install cd. Watch out- it won't work with a live-cd.
;)

---

