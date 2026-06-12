---
title: "grub error code 15"
date: 2007-11-27
forum: General Help
---

### Post by nynoah on 2007-11-27
I m running straight Gutsy 64bit.  No windows..............I just did the latest update and after when I rebooted, my Grub gives me an error code 15.  I tried to use the Gparted live disk to expand my linux partition and my swap.  Thinking maybe I exceeded them with the latest update.  I have done that before and it worked.  But this time, it has not.

any help.................what should I do?

---

### Post by climatewarrior on 2007-11-27
If you have an Ubuntu live cd available a solution might be to reinstall the grub from the live cd. Here's a link to a guide on how to do that.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good Luck

---

### Post by nynoah on 2007-11-27
Thanks I am using the Live CD right now

I will try that.

---

### Post by nynoah on 2007-11-27
ok now I have an error code 21

WTF?

---

### Post by meierfra on 2007-11-27
Does the grub menu appear during boot-up (Press Esc during the Count-Down)?

Boot from the Live CD and post the output of

```
sudo fdisk -l
```

and

```
 sudo blkid
```
(l is a lowercase L)

If you can access your Ubuntu partiton, post the content of the file "/boot/grub/menu.lst")
(If not, I'll give you detailed instruction once I see your "fdisk -l" output)

---

### Post by nynoah on 2007-11-27
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69df69df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30515   245111706   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe084e084

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36703   294816816   83  Linux
/dev/sdb2           36704       38913    17751825    5  Extended
/dev/sdb5           36704       38913    17751793+  82  Linux swap / Solaris

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24863058

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36481   293033601   83  Linux

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19bd19bc

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161   83  Linux
ubuntu@ubuntu:~$

---

### Post by nynoah on 2007-11-27
ubuntu@ubuntu:~$  sudo blkid
/dev/sda1: UUID="d7c45a9c-ead4-40e5-8f7d-826392d780dd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="cf69450a-1ac7-4ec4-a058-b4f40d688736" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="c5a6d004-da18-4c91-99d7-e0abe4446243" TYPE="swap" 
/dev/sdc1: UUID="ceda0f5a-7584-4193-8230-878d148ba6d6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda1: UUID="48e8d5b2-2eb3-4d8f-a773-dddb4dfc2da1" SEC_TYPE="ext2" TYPE="ext3" 
ubuntu@ubuntu:~$

---

### Post by nynoah on 2007-11-27
ubuntu@ubuntu:~$  /boot/grub/menu.lst
bash: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

---

### Post by meierfra on 2007-11-27
Which of the partitions is the Gutsy root partition? Is it  sda1? (If you don't know you should be able to tell from the "fdisk" information.

Assuming it is sda1 do this:
 (If it is not sda1,  replace sda1 by the correct name)

```
sudo mkdir /gutsy

sudo mount  -t ext3 /dev/sda1 /gutsy

```

Post the output of

```
 cat /gutsy/boot/grub/menu.lst
```

and

```
 df -h /dev/sda1 
```

---

### Post by meierfra on 2007-11-27
I just fixed a typo in my previous post.

---

### Post by nynoah on 2007-11-27
actually I think my Ubuntu is on sdb1 not sda1..........so I used that in your code.  Here is the output of it................and thank your for taking the time to help me.
> 
ubuntu@ubuntu:~$ sudo mkdir /gutsy
mkdir: cannot create directory `/gutsy': File exists
ubuntu@ubuntu:~$ sudo mount  -t ext3 /dev/sdb1 /gutsy
ubuntu@ubuntu:~$ cat /gutsy/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro

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
# defoptions=quiet splash vga=792

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

title           Ubuntu 7.10, kernel 2.6.22-14-rt
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.22-14-rt
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro single
initrd          /boot/initrd.img-2.6.22-14-rt

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$  df -h /dev/sda1
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             277G  221G   53G  81% /gutsy
ubuntu@ubuntu:~$  df -h /dev/sdb1
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             277G  221G   53G  81% /gutsy
ubuntu@ubuntu:~$ 

---

### Post by nynoah on 2007-11-27
why did that put happy faces into my code..................?

Well let me try that without the quote marks.




ubuntu@ubuntu:~$ sudo mkdir /gutsy
mkdir: cannot create directory `/gutsy': File exists
ubuntu@ubuntu:~$ sudo mount  -t ext3 /dev/sdb1 /gutsy
ubuntu@ubuntu:~$ cat /gutsy/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro

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
# defoptions=quiet splash vga=792

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

title           Ubuntu 7.10, kernel 2.6.22-14-rt
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.22-14-rt
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro single
initrd          /boot/initrd.img-2.6.22-14-rt

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$  df -h /dev/sda1
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             277G  221G   53G  81% /gutsy
ubuntu@ubuntu:~$  df -h /dev/sdb1
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             277G  221G   53G  81% /gutsy
ubuntu@ubuntu:~$

---

### Post by meierfra on 2007-11-27
The smiley face comes from 8 directly followed by ).

---

### Post by meierfra on 2007-11-27
I don't see anything wrong right now (although the df output looks a little bit fishy) I got to go now, but will be back in an hour or so)

---

### Post by meierfra on 2007-11-27
> tried to use the Gparted live disk to expand my linux partition and my swap.

How large was sdb1 before you extended it?

The fdisk and df data are kind of confusing:

According to fdisk sda1 has  245 G  but according to dh it is 277GB (221 used)
According to fdisk sdb1 has  294 G , but according to dh it is 277GB (221 used)

Are sda1 and sdb1 linked somehow?

---

### Post by nynoah on 2007-11-28
I dont think they are linked.  Let me try this to make it easier.  Its late..........so I know you are not around.  In the morning, I will disconnect all the extra hard drives and just leave the one with my Linux system on it.  The other drives are for storage alone.  I will run the commands you gave me that way and start from there.  Hopefully that will simplify things.  As it is, I have 4 hard drives in my computer.  Its too complicated to look at, so I should just go down to the one and later after it is all fixed add the others back in.

Thank you so much for taking the time to help me.  The Linux community here is great.  Don't know what I would do without you all.

Noah

---

### Post by nynoah on 2007-11-28
Ok I took out all my storage drives to make this less complicated.  I reran all the commands you gave me.  Here are the results.


> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe084e084

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36703   294816816   83  Linux
/dev/sda2           36704       38913    17751825    5  Extended
/dev/sda5           36704       38913    17751793+  82  Linux swap / Solaris
ubuntu@ubuntu:~$  sudo blkid
/dev/sda1: UUID="cf69450a-1ac7-4ec4-a058-b4f40d688736" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="c5a6d004-da18-4c91-99d7-e0abe4446243" TYPE="swap" 
ubuntu@ubuntu:~$ sudo mkdir /gutsy
ubuntu@ubuntu:~$ sudo mount  -t ext3 /dev/sda1 /gutsy
ubuntu@ubuntu:~$  cat /gutsy/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro

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
# defoptions=quiet splash vga=792

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

title           Ubuntu 7.10, kernel 2.6.22-14-rt
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.22-14-rt
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro single
initrd          /boot/initrd.img-2.6.22-14-rt

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=cf69450a-1ac7-4ec4-a058-b4f40d688736 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$  df -h /dev/sda1
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             277G  221G   53G  81% /gutsy
ubuntu@ubuntu:~$ 

---

### Post by PeterJS on 2007-11-28
> **nynoah said:**
> Ok I took out all my storage drives to make this less complicated.  I reran all the commands you gave me.  Here are the results.

Ok, well now that you've got the drives all taken out, put them back in. The part of the grub configuration that's failing is getting it pointed at the correct disk, and it looks like when you removed your storage disks your root partition got bumped from sdb to sda, so presumably when you put them back in that change will reverse itself and break your config again.

The easiest way to figure out where things are interms of grub numbering is to ask it. So we're trying to find which partition has /boot/vmlinuz-2.6.22-14-generic on it. So reboot, when grub comes up press 'c' to get to the grub shell, it operates a lot like bash with a very limited set of commands. Try running:
```

find /boot/vmlinuz-2.6.22-14-generic

```That's a rather long and awkward bit of typing I'd suggest making use of tab completion here. That's going to respond with a partition number. The partition number it gives you is what should be in the root directive of the boot configuration. So remember or write down which partition has the kernel, highlight the entry to boot ubuntu, and press 'e' to edit it, set the root directive to the right partition and then press 'b' to boot.

---

### Post by nynoah on 2007-11-28
OK I will try this now.  Be back in a few

---

### Post by meierfra on 2007-11-28
Before you put the drives back in, lets  try to boot into   ubuntu (that was the whole purpose of taking the other drives out)

Boot from the ubuntu LiveCD. and open a terminal.

mount you ubuntu partition via

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda /ubuntu
```
back-up and open the file menu.lst via
```
cd /ubuntu/boot/grub/
sudo cp menu.lst menu.lst.backup
gksudo gedit menu.lst 
```

Look for all the

title Ubuntu ....
root (hd1,0)

and change them to

title Ubuntu ....
root (hd0,0)


Save and close the  file 

In the terminal

```
sudo grub 
```

at the "grub>" prompt


```
root (hd0,0)
setup (hd0)
quit

```

Reboot.

---

### Post by nynoah on 2007-11-28
well I just got it all working now.  I think.............I am back in my Ubuntu system.  I am not sure if what I did was a temp fix or if is changed it and saved it.  When I went into the grub menu in the boot menu, it was set for Hd1.0  where my partition is on Hd0,0 .  So I just edited that.  

let me reboot and see if it is changed permanent or if I need to do something else to change it.

Noah

---

### Post by nynoah on 2007-11-28
OK well after reboot, I get the same problem.  I get the error code 15.  I then have to go in and edit the HD to Hd0,0 instead of Hd1,0.  So the question is, how can I get this to change and save it so I don't have to change the HD manually all the time.

Noah

---

### Post by saru411 on 2007-11-28
im not sure if this will help but this solved my grub issues. get and alt cd and follow this guide. 
[http://ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by meierfra on 2007-11-28
> OK well after reboot, I get the same problem. I get the error code 15. I then have to go in and edit the HD to Hd0,0 instead of Hd1,0. So the question is, how can I get this to change and save it so I don't have to change the HD manually all the time.

Just edit  menu.lst  according to my previous post.

---

### Post by nynoah on 2007-11-28
I did, but how do I save it?

---

### Post by nynoah on 2007-11-28
Is there a way for me to change this without having to boot into the live CD?

Noah

---

### Post by meierfra on 2007-11-28
Edit:   It even easier from ubuntu. See next post.

---

### Post by meierfra on 2007-11-28
Boot into ubuntu.  Open a terminal:

backup and open "menu.lst" via

```
cd /boot/grub
sudo  cp menu.lst menu.lst.backup
gksudo gedit menu.lst
```

Change "#groot (hd1,0)" to "#groot (hd0,0)"

Save and close the file.

 In the terminal:

```

sudo update-grub
```

Reboot.

---

### Post by nynoah on 2007-11-28
That FIXED it.................thank you so much.  People like you make Ubuntu the best OS period.

Thanks a million.  I just hope I can help someone in the future too.

Noah

---

