---
title: "Edgy Clean Install - random freezing during boot/shutdown"
date: 2006-12-01
forum: General Help
---

### Post by Tezcatlipoca on 2006-12-01
I'm completely new to Ubuntu, & to GNU/Linux in general.

I did a clean install of 6.10 "Edgy Eft" last week, & while I think it's great, I've been having some problems.........

Sometimes when I go to shutdown, or reboot, or boot, the PC will freeze during the Ubuntu splash, & not do anything. I have to turn the PC off by holding in the power button.

This is extremely annoying. It doesn't do it every time, but it's been doing it enough times to really irritate me & make me consider not bothering with it. I don't have boot/reboot/shutdown problems with XP.

I've re- clean installed over half a dozen times now in the past week & a half, & it still happens.

[Also, some of the install attempts were screwed from the start - one time it froze during the first reboot after installation, another time there was no display on reboot, & a third time the mouse & keyboard were extremely slow & unresponsive after installation.]

I used the normal 6.10 desktop install CD. The MD5 hash is correct, & Nero did a data verification after I burnt the disc.


My PC:

Intel Pentium 4, 3GHz, with HT.

512MB RAM

ATI Radeon 9800XT

200GB Seagate HDD (IDE, Ultra ATA?)

DVD-ROM

DVD+/-RW

Wireless USB mouse & keyboard

Onboard ethernet & wireless-G

etc.


The HDD is partitioned like this:

Primary partition (hda1), formatted in NTFS, with Windows XP Home SP2 installed (which uses it as the "C" drive).

Extended partition (hda2), containing an NTFS Logical partition (hda5), used by XP as the "D" drive (my media, backups, etc).

Primary partition (hda3), ext3, Ubuntu 6.10.

Primary partition (hda4), linux-swap.

It originally came with just a C primary (hda1) & a D logical (hda5, within the hda2 extended). I resized the C drive during my first Edgy install to create space for Edgy.




I've edited my grub.lst to change the splash from quiet to verbose, & the last couple of times I rebooted it hung while mentioning unmounting temporary file systems, and I think there was also mention of the swap.

---

### Post by Thumper322 on 2006-12-01
Can you post the results of **cat /boot/grub/menu.lst**? (You may need to run that with a **sudo** in front, if you get a permission error.)

You might have an ACPI (or APIC?) problem; I'm afraid I don't know that much about booting, since I just installed Ubuntu a couple of weeks ago.

---

### Post by Tezcatlipoca on 2006-12-02
I'm in XP at the moment, but will post that later.

Also, IIRC, one of the logs said something about "ACPI: Looking for DSDT ... not found!". 

I've read various threads where people suggest adding either acpi=force or acpi=off to the boot option. Not tried that yet though.

What I don't understand is that sometimes it's perfectly fine...it doesn't freeze during every reboot/shutdown.

I've read loads of threads here where people seem to have a similar/same problem - Ubuntu freezes when rebooting or shutting down - yet haven't seen a single definite fix for it.

I'm tempted to try out Dapper instead, but I've seen threads where people have the exact same problem with that too, plus also some sort of mounting problem caused by UUIDs (??).



I just want to get this thing to work! :(

---

### Post by Tezcatlipoca on 2006-12-02
Here's my original /boot/grub/menu.lst:

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
# kopt=root=UUID=18c3948a-8373-48b4-91d3-5cb6d2379799 ro
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
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```


All I've since changed is to password protect the grub editing menu, & I've changed "quiet splash" to "verbose" so I can see all the boot up info.

---

### Post by Tezcatlipoca on 2006-12-03
Still doing it.

I tried installing *again* last night, nice clean (re)install...after the first boot, the mouse & keyboard had the slow/unresponsive problem I'd had a few times before. Thought sod it, I'll try again...same problem.

I think I must have done about 10 clean installs now of "Edgy". Each time there's always some issue which pisses me off...the main ones being the boot/shutdown random freezing, or the screwy mouse/keyboard


I'm now downloading 6.06.1 Dapper & will try that instead of 6.10 Edgy.


If that messes me around, then I'll say goodbye to my brief period of trying Linux/Ubuntu, & go back to the cold embrace of Uncle Bill. XP may be a huge PITA sometimes, but at least it works.

---

### Post by Tezcatlipoca on 2006-12-03
It's getting quite boring replying to myself...

Still looking for some of this "Ubuntu spirit"...


Does anyone have any ideas/help/advice? Anyone?



I tried a clean install of 6.06.1 "Dapper Drake" (times 3).

It was worse. 

Seemed to hit an error when "mounting root filesystem" during boot. Found some threads on it here, & tried the workaround (putting the UUID into the fstab & grub menu.lst in place of e.g. /dev/hda3). Didn't work, still kept hanging while trying to mount the root filesystem.

So....

I have, once again, done a clean install of 6.10 Edgy.

I've had one boot where the mouse & keyboard went slow & unresponsive. They were OK though after rebooting again.

I've had another boot where it froze at some point & I had to turn it off using the power button.

As reinstalling doesn't help, & I'm quite bored of it now (11 installs of Edgy, 3 of Dapper), I'll stick with it & see how it goes.

But something is obviously wrong, at least intermittently, and it would be nice to fix it.

Windows doesn't freeze when I shutdown or reboot. It'd be nice for Ubuntu to actually behave that well.

---

### Post by Thumper322 on 2006-12-04
Yikes.

Sorry for not responding; my ISP decided to perform an "upgrade" which borked the Internet connection.

I really have no idea what's causing this. Could it be related to some bit of hardware on your laptop?

First off, how well does Ubuntu Edgy perform off the LiveCD? Do you have any of these problems? My computer worked out of the box, though I had to manually install my wireless card.

If Edgy doesn't perform well from the CD, barring the obvious slowdown from running it that way, then try changing boot parameters from the CD boot menu. It may be slower, but you can try appending various commands and not worry about messing up your main partition. (Again.) Then, once you find what works, you can modify GRUB and everything should work fine.

If Edgy works fine from CD, then I imagine something went wrong during installation. What tool have you been using to partition your drive? The LiveCD installer, or a Windows utility? I would suggest using gparted (from Knoppix) or something like Partition Magic (from Windows) to delete all Linux partitions from your computer, make two new partitions manually (swap and ext3), and then try installing directly onto those. I think that if you erase all traces of Linux from your system and then reinstall, you might get better luck.

Unfortunately, I'm no expert; you'll have to enlist the support of a boot guru. :-?

---

### Post by Tezcatlipoca on 2006-12-05
Cheers :) . At least you've replied!

It's a desktop, not laptop, btw. Doesn't have any special hardware, nothing fancy, nothing too old, nothing too new.

Edgy is OK using the LiveCD (barring the obvious slowness).

Doesn't freeze when booting from the LiveCD.

The only hardware I had to faff around with to get to work was my built-in wireless card. The prism54 driver wouldn't work with WPA, so I had to blacklist it & use ndiswrapper & my XP wifi driver instead.

I used the Edgy Live CD's installer to partition my HDD - I believe it actually uses gparted for the partitioning part of the install?


The first time I installed, I used it to resize my NTFS Windows C drive (after first CHKDISKing & defragging it), to create space to then be used to make Ubuntu partitions (an ext3 partition for Ubuntu, plus a swap partition).


gparted did hang after it completed the resizing that very first time, but then formatted OK & no errors were then mentioned. The Windows partitions on the drive have been CHKDISKed & defragged plenty of times since & had no problems.


During each of the many subsequent Ubuntu installs, I've deleted the two partitions (hda3 in ext3, and the hda4 swap), then re-created them & reformatted them, so each of the dozen-plus Ubuntu installs has been completely fresh.


Thanks for your help & advice.


EDIT:

Oh, I had a few more boot-freezes last night. None tonight, as I've not used it today.

On one of the freezes, it seemed to hang shortly after the "mounting root filesystem" (??) appeared on screen during the verbose splash, & on at least one other it froze just after it popped up "setting up network" or "configuring networking" (?) during the verbose splash.

---

### Post by Tezcatlipoca on 2006-12-06
Any help anyone? :(

---

### Post by Thumper322 on 2006-12-06
> **Tezcatlipoca said:**
> Any help anyone? :(

Hey...

Sorry; I can't get online very often and for much time. :( 

So you get no trouble running from the LiveCD, and loads of troubles running from the computer... Can you pop in the LiveCD and see what arguments are passed to your computer, and compare that with the arguments passed by GRUB on your installed system?

Maybe it's a funky module or something...

I'm afraid there's not much I can do to help; as I said, I'm no boot guru...

---

### Post by Kross on 2006-12-07
Try This=
[http://ubuntuforums.org/tags/index.php/shutdownpower-hang-ezfix/]("http://ubuntuforums.org/tags/index.php/shutdownpower-hang-ezfix/")

Maybe this can help.
Let Me Know..

<=Kross=>

---

### Post by Tezcatlipoca on 2006-12-07
> **Thumper322 said:**
> Hey...

Sorry; I can't get online very often and for much time. :( 

So you get no trouble running from the LiveCD, and loads of troubles running from the computer... Can you pop in the LiveCD and see what arguments are passed to your computer, and compare that with the arguments passed by GRUB on your installed system?

Maybe it's a funky module or something...

I'm afraid there's not much I can do to help; as I said, I'm no boot guru...


Not a problem - at least you're trying to help :) (5 day old thread, 259 views, & only you & Kross have ever replied to it :( )


How would I check what arguments are passed to the computer when using the LiveCD? 



> **Kross said:**
> Try This=
[http://ubuntuforums.org/tags/index.php/shutdownpower-hang-ezfix/]("http://ubuntuforums.org/tags/index.php/shutdownpower-hang-ezfix/")

Maybe this can help.
Let Me Know..

<=Kross=>


Cheers, I'll give that a try :)


Not sure if it will help my particular problem though - it does the freezing more often when booting/rebooting than shutting down, & I've seen the logs mention APM being disabled ("apm: disabled - APM is not SMP safe"), so I'm not sure if I should use it.

---

### Post by tlanglois on 2006-12-07
> **Tezcatlipoca said:**
> Not a problem - at least you're trying to help :) (5 day old thread, 259 views, & only you & Kross have ever replied to it :( )


How would I check what arguments are passed to the computer when using the LiveCD? 






Cheers, I'll give that a try :)


Not sure if it will help my particular problem though - it does the freezing more often when booting/rebooting than shutting down, & I've seen the logs mention APM being disabled ("apm: disabled - APM is not SMP safe"), so I'm not sure if I should use it.



Are you sure that your computer really freeze ? Isn't it taking very long to boot and shutdown ? I am asking this because I am having the same problem (sort of) I installed Ubunto 6.10 twice because after the first install, my computer "freezed" at boot time. I thought that something went wrong during the install so I did it again. It did not solve the problem 
but I noticed that it was not really freezing but it is taking ~3 minutes to boot. 

Thibault

---

### Post by Tezcatlipoca on 2006-12-07
> **tlanglois said:**
> Are you sure that your computer really freeze ? Isn't it taking very long to boot and shutdown ? I am asking this because I am having the same problem (sort of) I installed Ubunto 6.10 twice because after the first install, my computer "freezed" at boot time. I thought that something went wrong during the install so I did it again. It did not solve the problem 
but I noticed that it was not really freezing but it is taking ~3 minutes to boot. 

Thibault



It normally takes around 35 seconds for my PC to get from the Grub menu to the Gnome login, if it doesn't freeze up.

When it freezes, it just gets stuck...I've never left it particularly long when it freezes, I just notice it's not got anywhere, & is still frozen at some point in the boot up after a minute or two, so then turn it off with the power button. I may try leaving it next time, to see what happens if I wait a while.

---

### Post by Kross on 2006-12-07
I am not sure what I have said would really help,
But maybe it was worth a try....

As far as ACPI problems I have also seen where many tell you to disable ACPI power in the bios,,
If it a laptop I think you need this enabled..

Sorry I can help farther,,I am still new myself..
And What works for me I post..
But I know it doesn't always work for all.

Maybe you could go in the Konsole, type dmegs and post it.
my help the helpers.
<=kross=>

---

### Post by Tezcatlipoca on 2006-12-08
> **Kross said:**
> I am not sure what I have said would really help,
But maybe it was worth a try....

As far as ACPI problems I have also seen where many tell you to disable ACPI power in the bios,,
If it a laptop I think you need this enabled..

Sorry I can help farther,,I am still new myself..
And What works for me I post..
But I know it doesn't always work for all.

Maybe you could go in the Konsole, type dmegs and post it.
my help the helpers.
<=kross=>


Don't be sorry, I'm grateful for any help :)


I'll try the acpi disabling anyway - I guess I can just do it as a one-off by changing the boot parameters at the grub menu, instead of editing my menu.lst.

---

### Post by Tezcatlipoca on 2006-12-08
Attached is my most recent dmesg output (from when I booted this evening - worked fine).

(zipped as the txt file was too big to attach)

---

### Post by jessecollins on 2006-12-12
I am having this same problem with Edgy.  Does this picture look familar?  :)

[IMG]http://www.jessejcollins.com/files/ubuntu_freeze.JPG[/IMG]

That is where I freeze about 50% of the time.  Any sugestions would be appreciated.

---

### Post by lusis89 on 2006-12-13
I experienced this problem too,
the ony hardware I have in common with you is the
CPU: Pentium 4 3.0GHz HT,

My ubuntu & kubuntu OSes doesn't shutdown (appears an X-like pattern on the screen, --not grey but yellow--), the keyboard freezes up about 2 minutes after login, unless I am root.

Also the monitor insists to stand-by if I don't move the mouse...

I have this problem with Ubuntu 6.10, KUbuntu 6.10 and openSUSE 10.2, note that these are all x86_64 distros, since x386 distros does not install (the installer cannot locate the CD/DVD.... terrible...).

My motherboard, probably the cause of all problems, is an ASRock ??? dual-VSTA. (VSTA sounds like "vista", maybe it contains a Chip-Fritz that confuses the Linux Kernel?)

---

