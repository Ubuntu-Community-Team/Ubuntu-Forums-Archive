---
title: "Help ASAP- WIndows XP won't load"
date: 2007-01-31
forum: General Help
---

### Post by jesus5511 on 2007-01-31
Sorry if this has already been posted, but I'm completely new to this and I Just installed Ubuntu, but now my Windows XP Partition won't load, it just sits at the "starting up" screen and I need it fixed ASAP because other people use the computer. I noticed that it's set to "0,0", but I know that windows is located on HDA1, so if someone could please help ASAP I'd appreciate it very much. I tried going into the terminal and using the command lines to change the root password so I could edit the grub list and change it, but whenever I try to change the password it won't let me type.

Thanks.

---

### Post by meng on 2007-01-31
Type at terminal:
sudo nano -B /boot/grub/menu.lst

and enter your user password when prompted.

hda1 = (hd0,0), in case you didn't know.

---

### Post by jesus5511 on 2007-01-31
I didn't know actually, but I feel helpless right now with this, is their any explanation  for WIndows just hanging at the start up screen? Thanks a lot for the reply, I'm desperate to fix this.

---

### Post by meng on 2007-01-31
Show the output of the following:

sudo fdisk -l


and


cat /boot/grub/menu.lst

---

### Post by jesus5511 on 2007-01-31
For some reason when it asks me to put in a password it won't let me type, no matter what key I press nothing shows up in the terminal, but the second thing I typed in brought up this:



darold@darold-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=fc4d4849-896a-4f7b-99f9-3d15e08992bc ro
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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by meng on 2007-01-31
When it asked for a password, your typing doesn't get echoed to the screen, not even as asterisks. It's an important security feature! So just type it in and press enter!

Your menu.lst looks fine to me, and when you said that it gets to the windows startup screen (I assume you mean the one where the green or blue chunks keep moving within a white frame), that doesn't sound like a grub error to me. Something funny may have happened to the Windows installation itself - did you defragment the partition before installing Ubuntu? Did you back up your data? You may ultimately need to reinstall Windows, unless someone here has a better fix. But Ubuntu should be able to access all your Windows data if you hadn't backed up already.

---

### Post by jesus5511 on 2007-01-31
Ohh, thanks a lot for telling me about that, I had no idea.

Ah sorry for the misunderstanding, but when I say start up screen I mean after I click on windows XP in grub and a black screen comes up saying "Starting up..." in white letters at the top, it just sits their forever.

And when I go into "HD1" on the Ubuntu desktop, everything is their, including my windows folder and the application data folders..

Here are the results for the first thing you told me to type in:

bash: darold@darold-desktop:~$: command not found
IC KERNELS LIST

# This is a divider, added to sedarold@darold-desktop:~$ # menu.lst - See: grub(8), info grub, update-grub(8)
parate the menu items below from the Debian
# ones.
tdarold@darold-desktop:~$ #            grub-install(8), grub-floppy(8),
itle           Other operating systems:
root

darold@darold-desktop:~$ #            grub-md5-crypt, /usr/share/doc/grub

# This entry automatically added by the Debian idarold@darold-desktop:~$ #            and /usr/share/doc/grub-doc/.
nstaller for a non-linux OS
# on /dev/hda1
darold@darold-desktop:~$ 
t
darold@darold-desktop:~$ ## default num
root          
darold@darold-desktop:~$ # Set the default entry to the entry number NUM. Numbering starts from 0, and
savedefault
makeactive
chainloader     +1
darold@darold-desktop:~$ # the entry number 0 is the default if the command is not used.
darold@darold-desktop:~$ #
darold@darold-desktop:~$ # You can specify 'saved' instead of a number. In this case, the default entry
darold@darold-desktop:~$ # is the entry saved with the command 'savedefault'.
darold@darold-desktop:~$ # WARNING: If you are using dmraid do not change this entry to 'saved' or your
darold@darold-desktop:~$ # array will desync and will not let you boot your system.
darold@darold-desktop:~$ default         0
bash: default: command not found
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## timeout sec
darold@darold-desktop:~$ # Set a timeout, in SEC seconds, before automatically booting the default entry
darold@darold-desktop:~$ # (normally the first entry defined).
darold@darold-desktop:~$ timeout         10
bash: timeout: command not found
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## hiddenmenu
darold@darold-desktop:~$ # Hides the menu by default (press ESC to see the menu)
darold@darold-desktop:~$ #hiddenmenu
darold@darold-desktop:~$ 
darold@darold-desktop:~$ # Pretty colours
darold@darold-desktop:~$ #color cyan/blue white/blue
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## password ['--md5'] passwd
darold@darold-desktop:~$ # If used in the first section of a menu file, disable all interactive editing
darold@darold-desktop:~$ # control (menu entry editor and command-line)  and entries protected by the
darold@darold-desktop:~$ # command 'lock'
darold@darold-desktop:~$ # e.g. password topsecret
darold@darold-desktop:~$ #      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
darold@darold-desktop:~$ # password topsecret
darold@darold-desktop:~$ 
darold@darold-desktop:~$ #
darold@darold-desktop:~$ # examples
darold@darold-desktop:~$ #
darold@darold-desktop:~$ # title         Windows 95/98/NT/2000
darold@darold-desktop:~$ # root          (hd0,0)
darold@darold-desktop:~$ # makeactive
darold@darold-desktop:~$ # chainloader   +1
darold@darold-desktop:~$ #
darold@darold-desktop:~$ # title         Linux
darold@darold-desktop:~$ # root          (hd0,1)
darold@darold-desktop:~$ # kernel        /vmlinuz root=/dev/hda2 ro
darold@darold-desktop:~$ #
darold@darold-desktop:~$ 
darold@darold-desktop:~$ #
darold@darold-desktop:~$ # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ### BEGIN AUTOMAGIC KERNELS LIST
darold@darold-desktop:~$ ## lines between the AUTOMAGIC KERNELS LIST markers will be modified
darold@darold-desktop:~$ ## by the debian update-grub script except for the default options below
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## DO NOT UNCOMMENT THEM, Just edit them to your needs
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## ## Start Default Options ##
darold@darold-desktop:~$ ## default kernel options
darold@darold-desktop:~$ ## default kernel options for automagic boot options
darold@darold-desktop:~$ ## If you want special options for specific kernels use kopt_x_y_z
darold@darold-desktop:~$ ## where x.y.z is kernel version. Minor versions can be omitted.
darold@darold-desktop:~$ ## e.g. kopt=root=/dev/hda1 ro
darold@darold-desktop:~$ ##      kopt_2_6_8=root=/dev/hdc1 ro
darold@darold-desktop:~$ ##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
darold@darold-desktop:~$ # kopt=root=UUID=fc4d4849-896a-4f7b-99f9-3d15e08992bc ro
darold@darold-desktop:~$ # kopt_2_6=root=/dev/hda3 ro
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## default grub root device
darold@darold-desktop:~$ ## e.g. groot=(hd0,0)
darold@darold-desktop:~$ # groot=(hd0,2)
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## should update-grub create alternative automagic boot options
darold@darold-desktop:~$ ## e.g. alternative=true
darold@darold-desktop:~$ ##      alternative=false
darold@darold-desktop:~$ # alternative=true
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## should update-grub lock alternative automagic boot options
darold@darold-desktop:~$ ## e.g. lockalternative=true
darold@darold-desktop:~$ ##      lockalternative=false
darold@darold-desktop:~$ # lockalternative=false
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## additional options to use with the default boot option, but not with the
darold@darold-desktop:~$ ## alternatives
darold@darold-desktop:~$ ## e.g. defoptions=vga=791 resume=/dev/hda5
darold@darold-desktop:~$ # defoptions=quiet splash
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## should update-grub lock old automagic boot options
darold@darold-desktop:~$ ## e.g. lockold=false
darold@darold-desktop:~$ ##      lockold=true
darold@darold-desktop:~$ # lockold=false
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## altoption boot targets option
darold@darold-desktop:~$ ## multiple altoptions lines are allowed
darold@darold-desktop:~$ ## e.g. altoptions=(extra menu suffix) extra boot options
darold@darold-desktop:~$ ##      altoptions=(recovery) single
darold@darold-desktop:~$ # altoptions=(recovery mode) single
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## controls how many kernels should be put into the menu.lst
darold@darold-desktop:~$ ## only counts the first occurence of a kernel, not the
darold@darold-desktop:~$ ## alternative kernel options
darold@darold-desktop:~$ ## e.g. howmany=all
darold@darold-desktop:~$ ##      howmany=7
darold@darold-desktop:~$ # howmany=all
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## should update-grub create memtest86 boot option
darold@darold-desktop:~$ ## e.g. memtest86=true
darold@darold-desktop:~$ ##      memtest86=false
darold@darold-desktop:~$ # memtest86=true
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## should update-grub adjust the value of the default booted system
darold@darold-desktop:~$ ## can be true or false
darold@darold-desktop:~$ # updatedefaultentry=false
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ## ## End Default Options ##
darold@darold-desktop:~$ 
darold@darold-desktop:~$ title           Ubuntu, kernel 2.6.17-10-generic
bash: title: command not found
darold@darold-desktop:~$ root            (hd0,2)
bash: syntax error near unexpected token `hd0,2'
darold@darold-desktop:~$ kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
bash: kernel: command not found
darold@darold-desktop:~$ initrd          /boot/initrd.img-2.6.17-10-generic
bash: initrd: command not found
darold@darold-desktop:~$ quiet
bash: quiet: command not found
darold@darold-desktop:~$ savedefault
bash: savedefault: command not found
darold@darold-desktop:~$ boot
bash: boot: command not found
darold@darold-desktop:~$ 
darold@darold-desktop:~$ title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
bash: syntax error near unexpected token `('
darold@darold-desktop:~$ root            (hd0,2)
bash: syntax error near unexpected token `hd0,2'
darold@darold-desktop:~$ kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
bash: kernel: command not found
darold@darold-desktop:~$ initrd          /boot/initrd.img-2.6.17-10-generic
bash: initrd: command not found
darold@darold-desktop:~$ boot
bash: boot: command not found
darold@darold-desktop:~$ 
darold@darold-desktop:~$ title           Ubuntu, memtest86+
bash: title: command not found
darold@darold-desktop:~$ root            (hd0,2)
bash: syntax error near unexpected token `hd0,2'
darold@darold-desktop:~$ kernel          /boot/memtest86+.bin
bash: kernel: command not found
darold@darold-desktop:~$ quiet
bash: quiet: command not found
darold@darold-desktop:~$ boot
bash: boot: command not found
darold@darold-desktop:~$ 
darold@darold-desktop:~$ ### END DEBIAN AUTOMAGIC KERNELS LIST
darold@darold-desktop:~$ 
darold@darold-desktop:~$ # This is a divider, added to separate the menu items below from the Debian
darold@darold-desktop:~$ # ones.
darold@darold-desktop:~$ title           Other operating systems:
bash: title: command not found
darold@darold-desktop:~$ root
bash: root: command not found
darold@darold-desktop:~$ 
darold@darold-desktop:~$ 
darold@darold-desktop:~$ # This entry automatically added by the Debian installer for a non-linux OS
darold@darold-desktop:~$ # on /dev/hda1
darold@darold-desktop:~$ t
bash: t: command not found
darold@darold-desktop:~$ root          
bash: root: command not found
darold@darold-desktop:~$ savedefault
bash: savedefault: command not found
darold@darold-desktop:~$ makeactive
bash: makeactive: command not found
darold@darold-desktop:~$ chainloader     +1
bash: chainloader: command not found
darold@darold-desktop:~$ 

Thanks for the help so far.

---

### Post by meng on 2007-01-31
Hmm, I don't know how to solve this, but try adding this line within the last stanza of the menu.lst (the Windows stanza)

rootnoverify (hd0,0)


Use the 'sudo nano -B /boot/grub/menu.lst' command to edit


EDIT: where's the output of 'sudo fdisk -l' ???

---

### Post by jesus5511 on 2007-01-31
Okay, I went into the terminal to add it in, this is going to sound really pathetic, but how exactly so I save it after I add it in? Thanks a lot for the help btw.


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8453    67898691    7  HPFS/NTFS
/dev/hda2            8454        8584     1052257+  82  Linux swap / Solaris
/dev/hda3            8585        9729     9197212+  83  Linux
darold@darold-desktop:~$

---

### Post by meng on 2007-01-31
ctrl-x and choose save.
On second thoughts, just try replacing the root line with my rootnoverify line
At this stage, I have no idea what rootnoverify does, but it can't do any harm.

---

### Post by jesus5511 on 2007-01-31
Thanks a lot for the help, but it still doesn't seem to load..

---

### Post by dcstar on 2007-01-31
> **jesus5511 said:**
> Sorry if this has already been posted, but I'm completely new to this and I Just installed Ubuntu, but now my Windows XP Partition won't load, it just sits at the "starting up" screen and I need it fixed ASAP because other people use the computer. I noticed that it's set to "0,0", but I know that windows is located on HDA1, so if someone could please help ASAP I'd appreciate it very much. I tried going into the terminal and using the command lines to change the root password so I could edit the grub list and change it, but whenever I try to change the password it won't let me type.

Thanks.

At last resort you can use your Windows install CD to boot to Recovery Mode, and use the "fixmbr" utility to restore the Windows boot loader.

There are also freeware utilities that do this available on the web (do a search).

---

### Post by oracle5 on 2007-01-31
When I first dual booted my laptop I had to go back and set the windows partition to be active/boot. You can do it inside ubuntu. Go to the terminal. Applications>Accessories>Terminal and type or copy and paste

> sudo apt-get install gparted

Then go to System>Administration>Gnome Partition Editor and right click on your windows partition and select manage flags. Click in the box beside boot and click ok. You might have to click apply but I'm not sure since its been a while since I've done that. 

If that doesn't work for you I have other things you can do like using a gparted live cd or system rescue disc but I don't want to overwhelm you.

oracle5

---

### Post by oracle5 on 2007-01-31
You should be warned that if you use fixmbr in the xp recovery console you won't be able to boot into ubuntu.

oracle5

---

### Post by jesus5511 on 2007-02-01
I downloaded gparted and went into the manage flags for the HDA1, but boot was already ticked, so I guess that can't be the problem.

I forgot to mention, after Ubuntu was done installing it brought up an error (with a black background and white text) saying something about a memory error or something cannot be read, but I forgot about it, but I'm now guessing that is the problem...

Also, it says that HDA1 is 'Mounted on on /media/hd1." I have no idea if that has anything to do with anything but I figured it was worth mentioning.

Thanks a lot for the help so far.

---

### Post by jesus5511 on 2007-02-01
Well, I appear to have dug myself deeper.

I put in the WIndows disk and did the fixdbr, but it ended up screwing everything up and when I try I turn my computer on it gives me a disk read error, but luckily I still have the Ubuntu disk...

I also just realised, I installed grub into "HD0" when I set it up not really knowing what to put their, could this be a problem?

I just really hope I didn't ruin my windows partition..

---

