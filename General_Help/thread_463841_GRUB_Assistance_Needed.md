---
title: "GRUB Assistance Needed"
date: 2007-06-04
forum: General Help
---

### Post by flowingfire on 2007-06-04
Greetings!

GRUB is creating some trouble for me.  Kubuntu is my primary operating system, but I need other operating systems for various reasons.

I installed SUSE and instructed it not to install a bootloader, because I thought the Ubuntu GRUB would be able to detect it.

So, I went into the Ubuntu terminal and typed "sudo grub-update."  But it didn't work.  In fact, it made it so Windows Vista can't boot either.

Windows will not load and neither will SUSE.  I then tried editing /boot/grub/menu.lst, but then it didn't improve anything.  I could have sworn I put in all the correct booting locations in the menu.lst file, too.  Obviously, I am non-plussed by the whole situation-- lol.  NON-PLUSSED!  

My setup is as follows: 

Hard Drive 1: SCSI, 3 partitions:   sda1: Windows Vista   sda2: Swap   sda3: SUSE Linux

Hard Drive 2: EIDE, 2 partitions: 1: Kubuntu Feisty 2: Swap

I am not an expert and I can't spend hours and hours figuring this out.  Please help me find an easy way to fix this... And at least get Windows back.

---

### Post by flowingfire on 2007-06-04
Just bumping this to visibility..I'd really appreciate an answer for this.  Thanks. :)

---

### Post by louieb on 2007-06-04
Try adding this to /boot/grub/menu.lst for vista
```
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
chainloader    +1
```See the **dual boot link**  in my signature got all kinds of good stuff on how to boot multiple operating systems. Probally can figure out how to get Suse to boot by going through this site.

---

### Post by confused57 on 2007-06-04
Boot into Kubuntu, open a Konsole, and post the output of:
```
sudo fdisk -l
```
in case you aren't aware...the -l is a lowercase "L"

and your menu.lst:
```
cat /boot/grub/menu.lst
```

Hopefully it won't be to difficult to get your other OS booting from grub.

Added:  Hello louieb, you beat me by a matter of nanoseconds...between the 2 of us, "maybe" we can find a solution.

---

### Post by flowingfire on 2007-06-04
Thank you for the awesome support with this!  I really appreciate it. 

The output of my fdisk -l is:

david@porch-computer-linux:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            9487        9729     1951897+  82  Linux swap / Solaris
/dev/hda2               1        9486    76196263+  83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       34345   275868672    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           34346       34411      530145   82  Linux swap / Solaris
/dev/sda3           34412       38913    36162315   83  Linux

--------------------------------------------------------------------------------
The output of cat menu.lst is:

david@porch-computer-linux:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=4ab6a66b-f468-4937-882e-f174d8d873dc ro

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

## ## End Default Options ##

title           Kubuntu
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4ab6a66b-f468-4937-882e-f174d8d873dc ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

# on /dev/sda1
title           Windows Vista
root            (hd1,0)
savedefault
makeactive
map             (hd0)(hd1)
map             (hd1)(hd0)
chainloader     +1

# linux installation on /dev/sda3
title           SUSE
root            (hd1,1)
kernel          /vmlinuz root=/dev/sda3 ro
savedefault
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Recovery:
root

title           Kubuntu text-mode
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4ab6a66b-f468-4937-882e-f174d8d873dc ro single
initrd          /boot/initrd.img-2.6.20-16-generic

---

### Post by flowingfire on 2007-06-04
Louieb: I tried adding what you suggested, but that entry cannot boot into Windows either. :(

---

### Post by louieb on 2007-06-04
Just looking at your fdisk output for your second drive. 
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       34345   275868672    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           34346       34411      530145   82  Linux swap / Solaris
/dev/sda3           34412       38913    36162315   83  Linux

```and your Vista and Suse entries.
 ```

# on /dev/sda1
title           Windows Vista
root            (hd1,0)
savedefault
makeactive
map             (hd0)(hd1)
map             (hd1)(hd0)
chainloader     +1

# linux installation on /dev/sda3
title           SUSE
root            (hd1,1)
kernel          /vmlinuz root=/dev/sda3 ro
savedefault
boot

```Don't see  any reason Vista would not boot. 
The root statement for Suse is pointing to your swap partition. it should be 
```
root (hd1,2)
```Not that it matters but fdisk has the drives in reverse order from what you thought they are. The GRUB config file and fdisk both agree that the drive with Kubuntu is the 1st.  
>  Hard Drive 1: SCSI, 3 partitions:   sda1: Windows Vista   sda2: Swap   sda3: SUSE Linux
Hard Drive 2: EIDE, 2 partitions: 1: Kubuntu Feisty 2: Swap

Maybe confused57 will have some idea on whats wrong with Vista.  I'm clueless there. What I'm seeing should work.

---

### Post by confused57 on 2007-06-04
I'm not sure either, but I think your menu.lst entries should look something like this:
```
## ## End Default Options ##

title Kubuntu
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=4ab6a66b-f468-4937-882e-f174d8d873dc ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Kubuntu text-mode
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=4ab6a66b-f468-4937-882e-f174d8d873dc ro single
initrd /boot/initrd.img-2.6.20-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Recovery:
root

# on /dev/sda1
title Windows Vista
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

# linux installation on /dev/sda3
title SUSE
root (hd1,1)
kernel /vmlinuz root=/dev/sda3 ro
savedefault
boot

title  SUSE test
savedefault
configfile (hd1,1)/boot/grub/menu.lst
```

I'm not sure if SUSE uses menu.lst or grub.conf...you can try the above suggested entries, shouldn't hurt anything to try...you definitely need the Vista & Suse boot entries below the ###END DEBIAN ....I don't know, but it didn't look like you had a space between (hd0) (hd1) in your map lines.

---

### Post by flowingfire on 2007-06-05
Confused57 and Louieb: Thanks.  

Confused: I actually just copied and pasted your code example, and Windows boots again!  Yay!  Could it have something to do with the Debian comments that weren't present in my version?  I have no idea why it worked, but thanks!!!!

I did make the one alteration to the SUSE part that you mentioned, Louieb.  Unfortunately, SUSE still isn't working... hmmm... That's no big deal though, because the SUSE part is a new install without anything important on it.  

But I think I'll play around and see it I can actually coerce it into booting...

-David

---

### Post by confused57 on 2007-06-05
> **flowingfire said:**
> Confused57 and Louieb: Thanks.  

Confused: I actually just copied and pasted your code example, and Windows boots again!  Yay!  Could it have something to do with the Debian comments that weren't present in my version?  I have no idea why it worked, but thanks!!!!

I did make the one alteration to the SUSE part that you mentioned, Louieb.  Unfortunately, SUSE still isn't working... hmmm... That's no big deal though, because the SUSE part is a new install without anything important on it.  

But I think I'll play around and see it I can actually coerce it into booting...

-David

Glad you were able to get Windows booting again...did you try to boot Suse with the configfile entry?  May not work, but worth a shot.

---

