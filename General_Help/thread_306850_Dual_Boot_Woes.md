---
title: "Dual Boot Woes"
date: 2006-11-25
forum: General Help
---

### Post by Scheater5 on 2006-11-25
I recently installed 6.06 on a friend's Dell 600m, dual booting with XP.  Install of Dapper went great, and she's loving Ubuntu - didn't even touch Windows for about a week.  But, she needed to boot into Windows for school.  So, she restarts the laptop, selects XP from grub...and nothing.  Literally.  The messages indicating mounting the partition flash on the screen, and then a blank screen.  
But here's where it gets freaky - the computer won't boot windows *at all*.  I've got a cracked copy of XP I keep for repair purposes, and I threw that in the drive hoping to just "repair" the partition - but it gets the same results, a blank screen.  Tried repairing the MBR with super grub, and nothing - but admittedly I don't know my way around super grub very well.  
I don't even know where to start on this on - no error messages, seems like there's nothing to fix.  Mounting the Windows partition in Ubuntu shows that some of the files got borked in the install - most notably her music files.  But it's a Dell, so it didn't ship with an OS disk - I saved one of the repair partitions, but I think it was the utilities and not the restore partition (hey, the restore partition was larger, and I've never encountered this kind of problem).  Anyone have any ideas?

---

### Post by Average Joe on 2006-11-25
I think it would help if you could post the content of your /boot/grub/menu.lst file.

---

### Post by edo333 on 2006-11-25
This situation calls for a do over.  
Use the ubuntu bootable CD to repartition the HD - create 3 or 4 partitions.  Partition one reserve as NTFS for the fresh win XP install, and the other two use for /root and swap partitions, the third I like to use as a shared hard drive between the two using virtual fat 32 both windows and ubuntu can write to this drive (at least for a while, I've never been able to mount the drive from both OS's for an extended period of time.)
As far as actually recovering windows, I'm afraid that I can't help you there.  It may be possible, but windows is kind of particular about it's boot directory so messing with it usually makes the problem worse.  

Just as a point of curiosity did you happen to let the ubuntu install create it's own space on the hard drive, or did you manually configure the partitions before install.

---

### Post by whitewiz on 2006-11-25
I have just tried re-installing on my AMD64 laptop. I too got the problem of not being able to boot from the WinXP CD.  I eventually got around this by booting from a copy of WinXP sp1 instead of sp2.  Which i can upgrade to sp2 later.

Layout, if it matters:
Logical partition Ubuntu 6.10 amd64
 /boot 128m
 linux swap 256m
 / 5g
WinXp sp1 part 110g

---

### Post by Scheater5 on 2006-11-25
Do over, huh?  ouch.  She's non-techie - not sure I'm gonna be able to explain that I have to "do it over" to her.  And yea, I let Ubuntu arrange the partitions for me - tried to do it manually and it wouldn't let me, so I tried again (the option that makes a partition out of the unused space) and it went through.

---

### Post by Scheater5 on 2006-11-25
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
# kopt=root=/dev/hda3 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by edo333 on 2006-11-25
[QUOTE=Scheater5;1806539

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1[/QUOTE]

Hi there, 
Debian usually sets the mount point correctly for windows, but in this case you may want to try setting the 
"root" line to 
root         (hd0,0)
Try to reboot at this mount point
note: I'm only sugesting this becuase I installed ubuntu second on my machine and that is the mount point my dual boot uses, and it works perfectly.

---

### Post by edo333 on 2006-11-25
> **Scheater5 said:**
> Do over, huh?  ouch.  She's non-techie - not sure I'm gonna be able to explain that I have to "do it over" to her.  And yea, I let Ubuntu arrange the partitions for me - tried to do it manually and it wouldn't let me, so I tried again (the option that makes a partition out of the unused space) and it went through.

I lucked out and happend to have an extra 10 gigs of unallocated space left over, so I just added the new partitions for ubuntu.  Unfortunately the utility that automatically rearranges the partitions isn't great.

Can you run the ubuntu boot and choose to manually configure it and post what partitions it is now showing and their positions on the drive?

Also before you let ubuntu do it's thing did you defrage the windows drive? and delete any restore points?

---

### Post by Scheater5 on 2006-11-25
Remember that I said I saved the utility partition?  Well, that's hd0,0.  Letting it do it's thing now, maybe the utilities will actually do some good - let you know if that works.  Redoing the OS's is an absolute last resort - this is no new pc, and she'd like to have all of her stuff back.

---

### Post by Scheater5 on 2006-11-29
Well, the diagnostic turned up nothing unusual - so it's not a physical problem with the harddrive.  I'm completely baffled.  
It's as if Windows slowly shut down - for a few days it worked seemingly normal, then it became more difficult to boot into Windows (sometimes required a reboot, but then functioned), then Windows wouldn't boot but I could mount the partition in Ubuntu, then files started 'disappearing,' then I finally couldn't access the partition at all.  
Someone suggested that she had tried to "fix it" herself, and they think she had been tinkering around with boot.inf in Windows - but I'm not sure she's capable of this.  The good news is she's not mad, doesn't blame me or "Linux" and will continue using Ubuntu - she says she'd been having trouble anyway and "that windows was just destined to die."

---

