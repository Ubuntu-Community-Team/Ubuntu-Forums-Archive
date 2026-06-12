---
title: "Error 15: File not found"
date: 2008-02-02
forum: General Help
---

### Post by steve196 on 2008-02-02
(using new wubi 8.04 hh alpha 4)
> Booting 'ubuntu'

find --set-root --ignore-floppies /wubi/boot/linux

Error 15: File not found 

A \wubi directory does not exist on any of my drives.
I have no file named "linux", but i have a file D:\ubuntu\install\boot\vmlinuz (no vmlinuz anywhere else). D is on an 80 Gbyte  ATA harddisk

---

### Post by ago on 2008-02-02
Make sure you do not have 7.04 boot files (grldr*/wubildr*) or menu.lst files C:\
Then reinstall and try again

---

### Post by steve196 on 2008-02-02
Thank you!
I have uninstalled, found those files and removed them.
But now wubi does not start at all. I double click on it, see the hourglass next to the mouse for a second and that was it.
(using win2ksp4)

---

### Post by Scoty on 2008-02-02
i have the same error. i have deinstall 7.10 and have install 8.04.

---

### Post by ago on 2008-02-02
> **steve196 said:**
> Thank you!
I have uninstalled, found those files and removed them.
But now wubi does not start at all. I double click on it, see the hourglass next to the mouse for a second and that was it.
(using win2ksp4)

make sure you uninstalled everything, reboot reinstall wubi 8.04.
If you still have problems type %temp% in the file browser and post here the 8.04 wubi log

---

### Post by ago on 2008-02-02
> **Scoty said:**
> i have the same error. i have deinstall 7.10 and have install 8.04.

There are 2 errors posted above, 

1) trying to boot off /wubi/boot/linux
2) wubi crashing in windwos

which one do you have?

---

### Post by Scoty on 2008-02-02
i have install 8.04 but after the install on next boot i see the error message.

---

### Post by ago on 2008-02-02
Can you post the exact error message you see?

---

### Post by Scoty on 2008-02-02
i see this message:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=58348&d=1201943682[/IMG]

---

### Post by ago on 2008-02-02
at the countdown press ESC
then "e" to edit
change the line so that

root (hd0,0)/ubuntu/disks 

becomes

root (hdX,Y)/ubuntu/disks 

with X=disk number -1, Y=partition number -1

so if you installed on the 3rd partition of the first harddisk it would be: root (hd0,2)/ubuntu/disks

press enter to confirm, and "b" to boot

---

### Post by Scoty on 2008-02-02
with wubi 7.10 i dont have this problem, why with 8.04 ?

---

### Post by ago on 2008-02-02
> **Scoty said:**
> with wubi 7.10 i dont have this problem, why with 8.04 ?

The boot mechanism is different

I have opened a bug [https://bugs.launchpad.net/wubi/+bug/188460](https://bugs.launchpad.net/wubi/+bug/188460)

---

### Post by ysuire on 2008-02-04
> **ago said:**
> at the countdown press ESC
then "e" to edit
change the line so that

root (hd0,0)/ubuntu/disks 

becomes

root (hdX,Y)/ubuntu/disks 

with X=disk number -1, Y=partition number -1

so if you installed on the 3rd partition of the first harddisk it would be: root (hd0,2)/ubuntu/disks

press enter to confirm, and "b" to boot
Hello,

I have the same problem ... but how can we know on which partition it's installed ??

---

### Post by ago on 2008-02-04
You can use 

control panel>admin tools>Computer Mgmt> Disk Mgmt

and look for the partition # corresponding to the drive letter where wubi was installed.

or type cat /proc/partitions in linux for a list of partitions (then try one by one).

or simply go by trial and error 

(hd0,0)
(hd0,1)
(hd0,2)
(hd0,3)
(hd1,0)
(hd1,1)
(hd1,2)
(hd1,3)

---

### Post by ysuire on 2008-02-04
OK but the problem is that i cannot enter into Ubuntu because of this screen ... :confused: i think i will go by trial and error ... thanks, i'll tell you if it works ...

---

### Post by steve196 on 2008-02-04
Thank you!
The temp folder was full of trash and i deleted everything there. Now wubi started and i even could reboot into ubuntu install. But the reboot after that ran into error 15 while loading the kernel again. 
In the menu.lst i found the line:
> root		(hd0,0)/ubuntu/disks
which is odd because wubi files are on the fourth partition of my second harddrive.

---

### Post by ago on 2008-02-04
> **steve196 said:**
> Thank you!
The temp folder was full of trash and i deleted everything there. Now wubi started and i even could reboot into ubuntu install. But the reboot after that ran into error 15 while loading the kernel again. 
In the menu.lst i found the line:

which is odd because wubi files are on the fourth partition of my second harddrive.

should be (hd1,3)
see [http://ubuntuforums.org/showthread.php?t=685926](http://ubuntuforums.org/showthread.php?t=685926)

---

### Post by steve196 on 2008-02-05
Thank you!
Now it finds the file but runs into another problem (although i do not know, if this is wubi related)
> /dev/shm/root unexpected inconsistency. Run fsck manually...
Error writing block 576 (attempt to write block from filesystem resulted in short write)
(this message is not exactly copied and pasted, but the important parts are here)

---

### Post by ago on 2008-02-05
try to ron chkdsk /r from windows on the target drive

---

### Post by steve196 on 2008-02-05
chkdsk d: /r found nothing.

---

### Post by ago on 2008-02-05
You can run fsck from a live system, but it's probably easier to reinstall.

---

### Post by steve196 on 2008-02-06
Uninstalled, reinstalled, boot into system install went ok, again corrected the drive in menu.lst after install, again ran into the unexpected inconsistency. 
I tried (unsuccessfully) to boot  into recovery mode and saw, that the unexpected inconsistency is not one, but there are probably hundreds before the system gives up. 
I know, that the host partition filesystem is clean, but it is a FAT32 and maybe wubi is not made for that. I also don't see file system errors when booting into install.

---

### Post by steve196 on 2008-02-06
Error found! menu.lst specified root.disk to be mounted readonly. I changed this to rw and now the system boots.
You should really include a guide to menu.lst with wubi. There is no way grandmother could figure those things out.
Thank you for your help!

---

### Post by ago on 2008-02-06
> **steve196 said:**
> Error found! menu.lst specified root.disk to be mounted readonly. I changed this to rw and now the system boots.
You should really include a guide to menu.lst with wubi. There is no way grandmother could figure those things out.
Thank you for your help!

Hmm I will have to look into this since "ro" in menu.lst is _normal_. And that is ignored anyway at the moment by initramfs...
Are you sure that is the issue?

---

### Post by steve196 on 2008-02-06
It was the only thing i changed. I rebooted into windows, changed one letter in menu.lst, rebooted into wubi and had success. Before, i consistently got the error.

---

### Post by steve196 on 2008-02-06
Well, it worked...ONCE.
Now there is new fun. Second reboot i ended in a shell but not the one that failed starts usually end up with. 
Rebooting in recovery mode gives me the error:
> mount: Mounting /dev/disk/by-uuid/386E-3D77 on /root failed: No such device
and errors that are obviously a consequence of the one above.
I paged through the bootup messages yet found nothing extraordinary above that

edit: Sorry i forgot, a system update ran in the first run and updated the kernel. The new kernel was the problem.

---

### Post by acowboydave on 2008-02-11
Hello, it's been a long time since I have been here. Since this is a post about error 15 I thought I would put my situation here. Have acquired a Acer 5520 using Wubi 8.4 installed Hardy..got the error 15 change the.. root(hd0,0)/ubuntu/disks.. to.. root(hd0,1)/ubuntu/disks.. OK I am in. The problem is I am having to do this every time I reboot...if the answer to this was given in this post or another..sorry missed it. Install of Wubi and Hardy is in sda1 or in Vista, C. Do I have to change something in Vista?

---

### Post by ago on 2008-02-11
In ubuntu

sudo gedit /boot/grub/menu.lst

Change the line 

# groot = (hd0,0)/ubuntu/disks

Close and save

sudo update-grub

---

### Post by acowboydave on 2008-02-11
This has me know..getting this message back

---

### Post by ago on 2008-02-11
There is a space between gedit and the filename...

---

### Post by acowboydave on 2008-02-11
If my eyes are not tired it is already like that.

. # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=E8FC9F99FC9F609C loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)/ubuntu/disks

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

title		Ubuntu hardy (development branch), kernel 2.6.24-7-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-7-generic root=UUID=E8FC9F99FC9F609C loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-7-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-7-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-7-generic root=UUID=E8FC9F99FC9F609C loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-7-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by acowboydave on 2008-02-11
Think I have found the problem install of Wubi and Hardy is in sda2 not 1 shaold I change to (hd0,1) ?

---

### Post by ago on 2008-02-11
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)/ubuntu/disks

---

### Post by acowboydave on 2008-02-11
OK that did the trick..thanks so much...;)

---

### Post by asearle on 2008-03-11
Hi everyone,

I have this problem and find that my system will boot to windows but not to Ubunut.

I wanted to correct correct it by changing details in /boot/grub/menu.lst but found that, although I could live-boot to Kubuntu, I could not mount the drive.  I got the message ...

hal-storage-fixed-mount refused uid 999

(... under dolphin)

I am wondering whether I should try to make the change via Knoppix?  Or in a terminal window?

And I am wondering why the problem came in the first place:  The system was relatively freshly installed and had been booting fine for a while.  However, I had had an adept package manager crash beforehand.  Could that have done it?

Many thanks for any tips that you can give me.

Regards,
Alan Searle

---

### Post by ago on 2008-03-11
You can edit menu.lst also from windows

---

### Post by Althon on 2008-03-18
Hello! I'm also having some problems with the Error 15 after having installed wubi from Windows. The problem occurs after I've installed Wubi, rebooted and seen a complete installation in Ubuntu, rebooted and then the message  "Loop=/ubuntu/disks/root.disk ro quiet splash
Error 15 File not found" appears. I've tried to change the partitions listed in menu.lst throug trial and error, but without any luck.  Any ideas?

My menu.lst follows:

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
# root		(hd1,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd1,0)
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
# kopt=root=UUID=6640236B402340E3 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)/ubuntu/disks

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

title		Ubuntu hardy (development branch), kernel 2.6.24-11-generic
root		(hd1,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=6640236B402340E3 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-11-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-11-generic (recovery mode)
root		(hd1,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=6640236B402340E3 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-11-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd1,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by ago on 2008-03-18
Try to edit menu.lst (also from windows) and set 


root (hd0,0)/ubuntu/disks

---

### Post by Althon on 2008-03-18
It says that it was not possible to load Windows since the following file is missing or damaged <windows-rot>\system32\hal.dll

Seems that I've pointed grub to load Windows?


/A

---

### Post by ago on 2008-03-18
In which drive/partition did you install ubuntu?

---

### Post by Althon on 2008-03-18
in C:\ where I have Windows. I just checked Diskmanager, and it says that  C:\ is disk 1, not 0. I have 3 hard drives if that helps you. Thank you for helping me by the way :)

---

### Post by Althon on 2008-03-18
Ps. I'm new to this, not sure what partition i installed ubuntu into. I used the windows installer, and I can't see the ubuntu partition in the Diskmanager. Should I be able to do that? Ds.

---

### Post by ago on 2008-03-18
You can change the root value on the fly by pressing esc at the countdown and then "e" on the first option and "e" again. Try different values for X (drive# -1), Y (partition# -1). Presse enter to confirm and "b" to try to boot it

root (hdX,Y)/boot/ubuntu

---

### Post by Althon on 2008-03-18
Hi this time I changed to hd0,0 and then it worked! Where in menu.lst should I change to hd0,0?

/A

---

### Post by ago on 2008-03-18
From Ubuntu 

sudo gedit /boot/grub/menu.lst

edit the line 

# groot=(hd1,0)/ubuntu/disks

then run

sudo update-grub

---

### Post by ago on 2008-03-18
The problems with menu.lst misconfiguration with multiple hard drives are most likely due to [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497)

Not wubi specific. But might be fixed soon.

---

### Post by Althon on 2008-03-18
Thanks for all the help!

Now I just have to figure out how to get my wireless card running...

/A

---

### Post by Usuckstu on 2008-04-28
I have same error 15 and no boot after that. 
The file menu list is though different then from previous poster, where there is no clear indication on (disk, partition).
What's to do in this case?

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 3
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

---

### Post by ago on 2008-04-29
What is the first menu item if you press esc after selecting Ubuntu?
What exactly is the message after that?

---

### Post by asmith3006 on 2008-05-03
> **Usuckstu said:**
> I have same error 15 and no boot after that. 
The file menu list is though different then from previous poster, where there is no clear indication on (disk, partition).
What's to do in this case?

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 3
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

I get exactly the same error. It runs the windows installation bit, reboots, runs the first Ubuntu installation bit, reboots and then comes up with the above error message. Any suggestions?

It complains it can't find /ubuntu/disks/boot/grub/menu.lst and throws an error 15.

---

### Post by tinybit on 2008-05-03
It could be caused by a bug found in configfile recently.

Try a newer wubi version, which could solve it.

---

### Post by kaushikashwin on 2008-10-31
thnx 4 help dude

---

