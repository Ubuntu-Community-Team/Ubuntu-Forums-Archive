---
title: "[SOLVED] aClean Slate"
date: 2008-05-03
forum: General Help
---

### Post by bilijoe on 2008-05-03
I have a disastrously mangled 8.04 installation that I just want to wipe off the disk, and start over from a backup.  I know there's the dreaded "rm ..." command, that everyone seems to warn about, and I am sure I can figure that out by reading the man, if no one is comfortable with sharing it.  But isn't there a better way?  Something akin to a re-formatting of the disk?  I'd appreciate any suggestions anyone can offer.:)

---

### Post by tamoneya on 2008-05-03
the command the people don't recommend you ever use is ```
sudo rm -rf /
```DO NOT USE THIS

This however will not solve your problem.  It will delete EVERYTHING.  That isnt want you want.  What you should do is just put the liveCD and do a fresh install.  First you should make sure to copy your home directory so that you dont loose any documents.

One thing that I suggest while you are doing a new install is that you make /home its own partition.  That way you will be able to keep your fules in their own patition and not have to worry about them if you ever have to reinstall the operating system again. To do this you should select the manual partitioning option.

---

### Post by bilijoe on 2008-05-03
Won't doing an install over a mess leave behind parts of the mess that don't get overwritten during the install?:confused:

---

### Post by stream303 on 2008-05-03
When you come to partitioning, and let the partitioner "use the whole disk", it will wipe out any existing partitions, repartition it automatically, and continue on with installation.

Very clean. :)

---

### Post by bingoUV on 2008-05-03
As tamoneya suggests, use manual partition. In that, you have to choose partitions for / , /home and swap (possibly more but you do not need them). There is an option that asks you whether these need to be formatted prior to the installation. Select them to agree to the format. This wil give you almost a clean state. 

If you want a condition where determined disk search (without opening your hard drive) cannot retrieve information, do the following from live cd
```

sudo dd of=/dev/sda if=/dev/zero bs=1G count=500

```assuming a 500 GB hard disk and device node /dev/sda (this will likely be correct if you have single sata hard disk).

Note that you will need professional help of the highest degree to retrieve stuff after the above step, so do the above only if you are sure of what you are doing and that you will never need the data again.

---

### Post by bilijoe on 2008-05-03
Believe me, I understand the implications of running the code you posted:```
sudo dd of=/dev/sda if=/dev/zero bs=1G count=500
``` In a previous life, I did a lot of programming and training for a company whose clients were; our government (including agencies that do not exist;);):-$8-[), all "friendly" governments, all branches of the military (ours and theirs), fortune 500 companies, and "private" government "security consultants".  Most of the programs I wrote fell into one of two categories: programs that "securely" removed data from disks (or any other medium), to the extent it could _never_ be recovered, and programs that retrieved data that had been "securely" removed from whatever medium it had been recorded on.  Although recovering data after securely deleting it is, in theory, possible, and its proof of concept has been accomplished and duplicated (on a very small scale), the reality is you not only need, as you said, "professional help of the highest degree", you will also need a _lot_ of money, as the equipment necessary is very sophisticated, and, to recover even a few bytes of data requires hours.  In addition, you probably won't be able to convince the few people in the world who know how to do this kind of recovery, to work for you.  Furthermore, even if all you do is ask, and get turned down (as you most certainly will), there will probably be an unmarked black sedan parked across the street from your house, and your phone (and cell phone, and internet connection, etc.) will be monitored for the rest of your life.  The "Men In Black" (and, yes Virginia, there really are Men In Black--I have met, and trained many of them) are a highly suspicious bunch, and would be more than a little interested in anyone who was willing to go to the lengths necessary to retrieve securely deleted data.  Moreover, their primary interest would be the data (even though they would have no idea what it was), making you an expendable inconvenience, unless you were really cooperative in helping them get their hands on whatever it was you had set out to recover.  The bottom line here is this; if you have deleted something that you later want to recover, and the recovery is beyond the skills of the local college hacker/I.T. specialist, STOP RIGHT THERE.  The data is _gone_, and approaching anyone beyond the hacker/guru kid down the block, will get your name on more government lists than you can imagine.  And you might even get to meet one of the Men In Black, which, believe me, is NOT a good thing.  Anyway, I appreciate your response, but the mere thought of someone making a serious attempt to recover securely deleted data, makes me feel, based on personal experience, that I need to proffer a warning to anyone who might have the inkling to do so... BE _VERY_VERY_ CAREFUL WHO YOU DISCUSS SUCH MATTERS WITH!  And if you do decide to discuss it with anyone, I recommend you first contact Maxwell Smart, and arrange to borrow the Cone of Silence, in which to conduct such discussions.

Obviously, I have had my tongue in my cheek for part of this dissertation, but the core message is, indeed, very serious.  Having worked very closely with many of the people who carry the highest of security credentials, I can assure you, it takes a _lot_less_ to get their attention than you probably think--especially when you are talking about what amounts to State Of The Art Computer Technology.   It's a very paranoid playing field, to say the least.  So whatever you may have securely deleted, it's gone--let it go, and continue to live your life free from government scrutiny.

Cheers,
Bili Joe

---

### Post by tamoneya on 2008-05-04
So did you fix your problem?

---

### Post by bilijoe on 2008-05-04
Actually, no.:(  But I think I'm real close.:)  Apparently, the entry for my boot partition is missing from my /dev/disk/by-uuid/ directory.:confused:  The boot process subsequently hangs, unfortunately before reaching the "recovery mode" console, but it does dump me into a minimally functional shell that I am not familiar with.  I hope, with the commands it has available, and the help of one or more of you certifiable geniuses out there, I can do what I need to, in order to get this installation to finish booting, so I don't have to start from scratch (again).  I did what tamoneya suggested, and let Ubuntu install itself over the mess that was there, and it did clean off all the old stuff, and write a clean installation, in its place.  I then restored my archived (via tar) system on top of the fresh install, which, as I understand it, _should_ have put me back where I wanted to be--except now the system won't boot.  The shell I end up with identifies itself as BusyBox (ash), and the prompt is "(initramfs)".  Using it, I was able to determine that an a symbolic link (or maybe a hard link, I don't know), in the form of "lrwxrwxrwx  1   0         0               10  <the uuid> --> ../../sda2", is missing from the /dev/disk/by-uuid/ directory.  There doesn't seem to be an editor available in the shell I'm stuck in, but I remember, from my Unix days, that an awful lot can be done by making creative use of the command line.  I don't remember hardly any of the tricks I used to know, and I don't know if I have the commands available that I would need, but I'm hoping one of you major Linux honchos out there can bail me out.  Some of the commands that seem to me like they may be able to be tricked into doing what I need are; echo, chmod, mkdir, mknod, mktemp, and ln.  There are more, but those (especially ln) seem like the most useful candidates to me.  Can someone please tell me, if it's possible, how to use this limited command set, and create the "missing link" that I need to bring my system back to life.  I'd really appreciate it.  PS. I just noticed I can get a grub command line by typing "c" at the boot loader menu.  This may be a more powerful command line, and may be more useful.  Again, I don't know.  Any help anyone can offer will be greatly appreciated.

---

### Post by tamoneya on 2008-05-05
it seems to me like the grub configuration file is wrong or possibly fstab.  Since the busy box prompt is so limited we will do all of this through terminal on the live CD.  If you mount your linux partition from inside the partition you should locate and post the contents of /boot/grub/menu.lst and /etc/fstab

---

### Post by bilijoe on 2008-05-05
OK,here's "fstab":
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cd28a3a8-25d8-40f0-9721-4716ca1431c0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e37932fa-a0cd-439c-bd6b-bb26b9330f57 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

And here's "menu.lst":
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=88bef3fc-22b7-454b-822b-7a04e6a8ca5b ro

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

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=88bef3fc-22b7-454b-822b-7a04e6a8ca5b ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (Show Boot Commands)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=88bef3fc-22b7-454b-822b-7a04e6a8ca5b ro
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=88bef3fc-22b7-454b-822b-7a04e6a8ca5b ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by tamoneya on 2008-05-05
try changing /boot/grub/menu.lst so that any references to the UUID are cd28a3a8-25d8-40f0-9721-4716ca1431c0 instead of 88bef3fc-22b7-454b-822b-7a04e6a8ca5b

---

### Post by bilijoe on 2008-05-05
You're a genius!  Thank you so very much.  This has ended days of headaches.:popcorn::popcorn::guitar::)

---

