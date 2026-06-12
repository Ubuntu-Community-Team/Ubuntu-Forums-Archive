---
title: "Need help with dual boot xp &amp; ubuntu"
date: 2008-06-19
forum: General Help
---

### Post by Radytz on 2008-06-19
i have this configuration :

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        1247      249007+  82  Linux swap / Solaris
/dev/sda3            1248        4998    30129907+   5  Extended
/dev/sda5            1248        4998    30129876    b  W95 FAT32

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        9964    80027797+   f  W95 Ext'd (LBA)
/dev/sdb5               2        9964    80027766    7  HPFS/NTFS

and i want to make a new entry in the GRUB boot menu (i know how to do it) to boot up windows from second drive , sdb . nothing seems to work till now  after i watched several threads here .

---

### Post by Radytz on 2008-06-19
bump :(

---

### Post by fooman on 2008-06-19
well you say you "know how to do it", so i'm not real sure what it is that your asking....but to add a drive with windows xp pro to the /boot/grub/menu.lst,  the entry should look something like this:

```

title           Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1
```

be sure to backup your menu.lst before you go messing around with it...

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

---

### Post by Radytz on 2008-06-19
ok tyvm that was exactly what i asked , problem solved:P

---

### Post by gulatiakshay on 2008-06-19
Unable to boot xp after i install ubuntu 8.04 help me ...i am not getting dual boot screen

---

### Post by leito666 on 2008-06-19
> **gulatiakshay said:**
> Unable to boot xp after i install ubuntu 8.04 help me ...i am not getting dual boot screen

But could you see Grub with only linux options?

---

### Post by gulatiakshay on 2008-06-19
Well its not giving any option, ubuntu is directly booting.....i tried to reinstall ubuntu to see if i deleted windows or what....
but windows is there
                size    free
/dev/sda5 ntfs  20974  10900
/dev/sda6 ntfs  10487   3200

Rest is ubuntu in some space, and rest some free space....and in ubuntu terminal window when i checkd the space used following is what i am getting

akshay@akshay-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.3G  2.2G  6.7G  25% /
varrun               1010M  100K 1010M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M   48K 1010M   1% /dev
devshm               1010M   12K 1010M   1% /dev/shm
lrm                  1010M   38M  972M   4% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon      9.3G  2.2G  6.7G  25% /home/akshay/.gvfs

I am totally new to linux.....

---

### Post by russlar on 2008-06-19
@gulatiakshay -watch your system boot up. Do you see a boot menu screen at all? It should give you a couple of options to boot to, and it will only be on screen for five seconds. If you see this screen, then all you need to do is the fix fooman posted a couple of posts up.

---

### Post by gulatiakshay on 2008-06-19
First screen i am getting as:

Grub loading....
Press esc to see menu 

if i press esc then i am getting

three options to log in ubuntu
ubuntu 8.04 kernel 2.6.24 - 16 generic
ubuntu 8.04 kernel 2.6.24 - 16 generic (recovrey mode)
ubuntu 8.04 memtest86+

if i dont press esc then another screen which i get is

starting...

then finally ubuntu is started

so from where i will get windows dual boot screen

---

### Post by russlar on 2008-06-19
> **gulatiakshay said:**
> First screen i am getting as:

Grub loading....
Press esc to see menu 

if i press esc then i am getting

three options to log in ubuntu
ubuntu 8.04 kernel 2.6.24 - 16 generic
ubuntu 8.04 kernel 2.6.24 - 16 generic (recovrey mode)
ubuntu 8.04 memtest86+

if i dont press esc then another screen which i get is

starting...

then finally ubuntu is started

so from where i will get windows dual boot screen

what you need to do is the fix fooman posted further up.

1. sudo fdisk -l
this will give you all of the disks that your system recognizes. look for one that's formatted as NTFS
2. sudo cp /boot/grup/menu.lst /boot/grup/menu.lst.OLD
this makes a backup copy of the grub menu that you see at boot
3. sudo gedit /boot/grup/menu.lst 
this opens the grub menu for editing.

the file that you've opened should have examples of how to write an entry. The important parts are title, which is how the entry will appear in the boot list, and root, which is the hard drive that the windows partition is on.

---

### Post by gulatiakshay on 2008-06-19
1. sudo fdisk -l
this will give you all of the disks that your system recognizes. look for one that's formatted as NTFS


1.akshay@akshay-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb710b710

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        3825        8865    40491832+   f  W95 Ext'd (LBA)
/dev/sda5            3825        6374    20482843+   7  HPFS/NTFS
/dev/sda6            6375        7649    10241406    7  HPFS/NTFS
/dev/sda7            7650        8865     9767488+  83  Linux





2. sudo cp /boot/grup/menu.lst /boot/grup/menu.lst.OLD
this makes a backup copy of the grub menu that you see at boot

2. akshay@akshay-desktop:~$ sudo cp /boot/grup/menu.lst /boot/grup/menu.lst.OLD
cp: cannot stat `/boot/grup/menu.lst': No such file or directory

3. sudo gedit /boot/grup/menu.lst
this opens the grub menu for editing.
3.menu.lst appears but its blank what should i write on that, ;) well i am just a starter .....i am sorry if i am irritating by trivial questions

---

### Post by fooman on 2008-06-19
> **gulatiakshay said:**
> 

3. sudo gedit /boot/grup/menu.lst
this opens the grub menu for editing.
3.menu.lst appears but its blank what should i write on that, ;) well i am just a starter .....i am sorry if i am irritating by trivial questions

a little typo there....instead of /boot/gru[COLOR="Red"]p[/COLOR]/menu.lst,  it should be /boot/gru[COLOR="Red"]b[/COLOR]/menu.lst

and also....when using an editor with a gui (like gedit),  you should use "gksudo" instead of just "sudo".  so you should run the command like so:

```
gksudo gedit /boot/grub/menu.lst
```

hope that helps.

---

### Post by gulatiakshay on 2008-06-19
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
timeout		3

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
# kopt=root=UUID=070750fb-6809-4e04-8269-e51d80016132 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=070750fb-6809-4e04-8269-e51d80016132 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=070750fb-6809-4e04-8269-e51d80016132 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Now what changes should i make, well i know i have to edit and bring windows but how should i write that so that from next time i will get boot option

---

### Post by fooman on 2008-06-19
looking at what you posted earlier....try adding this to the end of the file just after the memtest entry:

```
title           Windows XP Professional
root            (hd0,5)
savedefault
makeactive
chainloader     +1
```

so that the end result looks exactly like this:

```
title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=070750fb-6809-4e04-8269-e51d80016132 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=070750fb-6809-4e04-8269-e51d80016132 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
quiet

title           Windows XP Professional
root            (hd0,5)
savedefault
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

save the changes, close the file and reboot.  see if the windows entry is there and if you can boot into it.

i'm not sure about the "root (hd0,5)" part,  but give that a try.  if when you choose windows,  you see an error...just boot back into ubuntu and we will try another edit.

---

### Post by gulatiakshay on 2008-06-20
I am getting 

error 12: device invalid 

so what next,

---

### Post by fooman on 2008-06-20
sorry,  i'm no grub pro...but try changing:

```
root            (hd0,5)
```

to:

```
root            (hd0,4)
```

see what that gets you.

---

### Post by meierfra. on 2008-06-20
Radytz:  Here is a similar case  which got solved:

[http://ubuntuforums.org/showthread.php?t=83486]("http://ubuntuforums.org/showthread.php?t=834864")

Follow the instruction  in post #9 of that thread with the following modification:

Replace the second line in Step 1 by

```
sudo mount /dev/sdb5 /windows
```

And in Step 3 use:

title XP
rootnoverify (hd1,4)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by meierfra. on 2008-06-20
gulatiakshay:  Here is a similar case which got solved:

[http://ubuntuforums.org/showthread.php?t=83486]("http://ubuntuforums.org/showthread.php?t=834864")

Follow the instruction in post #9 of that thread with the following modification:

Replace the second line in Step 1 by


```
sudo mount /dev/sda5 /windows
```


(This assumes that the Windows OS is on /dev/sda5. If the OS is on /dev/sda6, let me know and I'll give you new instruction)

---

### Post by meierfra. on 2008-06-21
I just noticed that my link was missing a number. It's fixed now.

---

### Post by gulatiakshay on 2008-06-21
There r only two post in the link  provided by you......i cant find post#9

---

### Post by meierfra. on 2008-06-21
Did you see my  last post? I already fixed the link.

---

### Post by gulatiakshay on 2008-06-21
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb710b710

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        3825        8865    40491832+   f  W95 Ext'd (LBA)
/dev/sda5            3825        6374    20482843+   7  HPFS/NTFS
/dev/sda6            6375        7649    10241406    7  HPFS/NTFS
/dev/sda7            7650        8865     9767488+  83  Linux


akshay@akshay-desktop:~$ mkdir /windows  
mkdir: cannot create directory `/windows': Permission denied

akshay@akshay-desktop:~$ sudo mount /dev/sda5 /windows
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /windows ntfs-3g force 0 0

Now what, i dont find windows running any where neither any hardware is attached, i need to get windows back on any cost

is there any way to get it back

---

### Post by meierfra. on 2008-06-21
> mkdir /windows
mkdir: cannot create directory `/windows': Permission denied


Opps, that should have been "sudo mkdir /windows"


> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported

Did you use hibernation the last time you shutdown Windows?
Did you resize XP  during installation?
Did you deleted any partition during installation?

If  you have a windows CD, I suggest to boot from the Windows CD, press "r" to enter the repair console and then

```
chkdsk
```

and if that returns some errors:


```
chkdsk /p /r
```


Or you can try 


```
sudo mount -t ntfs-3g /dev/sda5 /windows -o force
```

in the Ubuntu terminal.

---

### Post by fooman on 2008-06-21
gulatiakshay,  just curious....did you try the edit i gave you in post #16 ?

thanks

---

