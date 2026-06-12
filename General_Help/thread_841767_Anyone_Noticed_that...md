---
title: "Anyone Noticed that.."
date: 2008-06-26
forum: General Help
---

### Post by xdavidx on 2008-06-26
when you install ubuntu in a pc partitioned that already had Winxp the Xp slows down a lott!!!??!!!!

Any fix to this?

---

### Post by change_mode on 2008-06-26
That's impossible unless you mess up the partitioning.

---

### Post by |{urse on 2008-06-26
Probably xp has always been that slow and now that you are using ubuntu beside it you realize just how darn slow that crap really is.

---

### Post by xdavidx on 2008-06-26
> **change_mode said:**
> That's impossible unless you mess up the partitioning.

I've installed in 3 different computers and the result it's the same after some days, the winxp gets slow like hell..
And i've installed in diferent hard drives.. my friend told me the same, and i told him to test "install xp and then ubuntu" and after some days using both the system slows..not "ubuntu thought" but WinXp.

i'm searching for it and some users say the same, and i think it's because the grub being "together"..but don't really know.

---

### Post by xdavidx on 2008-06-26
> **|{urse said:**
> Probably xp has always been that slow and now that you are using ubuntu beside it you realize just how darn slow that crap really is.

No, after a clean installation of Xp i installed the Ubuntu, and Xp was fasttt after i installed Ubuntu and boot on Xp..Xp get slow..

---

### Post by lisati on 2008-06-26
> **xdavidx said:**
> when you install ubuntu in a pc partitioned that already had Winxp the Xp slows down a lott!!!??!!!!

Any fix to this?

Option 1: Click Start->Run, enter "%temp%", without the quotes, click "OK", and remove as much Windows will allow from the temporary directory. Then use the Windows cleanup tool from the "System accessories" menu, and then defrag the Windows partion several times. This can help, even if you choose not to install *nix.
Option 2: Ditch Windows
Option 3:......Anyone else?

---

### Post by xdavidx on 2008-06-26
> **lisati said:**
> Option 1: Click Start->Run, enter "%temp%", without the quotes, click "OK", and remove as much Windows will allow from the temporary directory. Then use the Windows cleanup tool from the "System accessories" menu, and then defrag the Windows partion several times. This can help, even if you choose not to install *nix.
Option 2: Ditch Windows
Option 3:......Anyone else?

After a fresh installation..u don't have %temp%..it's not windows..i know windows suck, but it was good before i was installed ubuntu next to windows..

---

### Post by xdavidx on 2008-06-26
if anyone has some kind of solution or explanation to this..i apreciate..btw i'm not a noob..

---

### Post by manfer on 2008-06-26
Have you updated Windows? Have you installed SP3?

---

### Post by xdavidx on 2008-06-26
> **manfer said:**
> Have you updated Windows? Have you installed SP3?

No..

---

### Post by manfer on 2008-06-26
Which computer? Laptop, desktop? How you installed ubuntu? Had Windows XP all disk space before the installation? If you had to repartition disk space how did you do it? ...

If you don't post as many data as you think could be useful to help you, I don't see how someone could help you with: "Windows XP slow after installing ubuntu" is not enough I think. It is the first time I hear such a thing and I'm sure most in here too. It is very rare, an ubuntu installation should not affect the Windows XP at all. It is very rare too, grub bootloader should not affect Windows XP at all, because after chosing an entry in grub it pass total control to the Operating System chosen.

You could post your /boot/grub/menu.lst too to see if Windows entry there has any error.

Besides looking for "xp slow after ubuntu install" on www and I can't see those people reporting the same you say, Could you point where?

---

### Post by Greyed on 2008-06-26
> **xdavidx said:**
> if anyone has some kind of solution or explanation to this..i apreciate..btw i'm not a noob..

There simply is not enough information for us to intelligibly suggest anything.  All I can say is that I have had KUbuntu installed along side WinXP on my game machine and WinXP isn't slowing down because of it.  There are dozens, if not hundreds, of reasons why Windows would slow down.  None are really appropriate to go into here other than this:
It's not Ubuntu and it's not Grub.

---

### Post by manfer on 2008-06-26
> **xdavidx said:**
> i think it's because the grub being "together"..but don't really know.

That makes no sense for me. Could you explain better what you mean?

Have you installed grub yourself or the installation made it for you? If you did it, how did you do it?

---

### Post by xdavidx on 2008-06-26
> **manfer said:**
> Which computer? Laptop, desktop? How you installed ubuntu? Had Windows XP all disk space before the installation? If you had to repartition disk space how did you do it? ...

If you don't post as many data as you think could be useful to help you, I don't see how someone could help you with: "Windows XP slow after installing ubuntu" is not enough I think. It is the first time I hear such a thing and I'm sure most in here too. It is very rare, an ubuntu installation should not affect the Windows XP at all. It is very rare, grub bootloader should not affect Windows XP at all, because after chosing an entry in grub it pass total control to the Operating System chosen.

You could post your /boot/grub/menu.lst too to see if Windows entry there has any error.

i've installed it on 2laptops and on 1 desktop. In the desktop i've installed in diferent hard drives. i had one with winxp and another free so i've installed ubuntu on it. After that i noticed that winxp was slowed down a bit..i started to use ubuntu and only sometimes entered in xp 2 or 3 always noticing that was worst..but i was like "maybe it's just because ubuntu is a lot faster than xp", after 2 month i've entered on it again an xp was the "chaos" so i have made a format of it and also format the ubuntu "to change ubuntu to the other disc" so i've installed once again Winxp first and then ubuntu in the same day the speed of booting on Xp was very different after i installed ubuntu, it was like it get "stucked" and "consuming all my memory" and cpu, a thing that it haven't done before. And in my father's laptop the same happened, until he couldn't be able to read his emails, because the "slowliness?!" of Xp after the ubuntu instalation, and he have the newer sony vaio..so..i can't get it..cause ubuntu works fine when u boot on it(always),it seems ubuntu "consumes everything" when i use it and make xp a trash..

btw..and my post was to know if anyone noticed this "problem", if so someone would had the solution..but i see this is a new thing so..thks.

---

### Post by avtolle on 2008-06-26
I'm wondering if the OP defragged the drive before installing Ubuntu. For me, Vista runs no slower than it otherwise did (awful) after installed both 8.04 and LinuxMint Elyssa. Also, wondering how the partitions are set up.

---

### Post by xdavidx on 2008-06-26
> **avtolle said:**
> I'm wondering if the OP defragged the drive before installing Ubuntu. For me, Vista runs no slower than it otherwise did (awful) after installed both 8.04 and LinuxMint Elyssa. Also, wondering how the partitions are set up.

I have no partitions on the desktop and the hard drive where i installed ubuntu was new..that's why i can't understand why he make xp that why..btw i've taking of ubuntu of it and xp got normal again...

---

### Post by manfer on 2008-06-26
Only trying to guess. Could someone tell if mounting the NTFS filesystem where Windows XP resides and not properly being unmounted at shutdown could affect?.

I don't know how ubuntu could be affecting your XP. Think of how the boot process in a computer takes place. In your case when you run Windows XP. First the BIOS is loaded, BIOS pass control to grub on MBR, grub pass control to XP loader. As you see ubuntu is not implied in that process unless grub passing control to XP loader. If you post menu.lst as I suggested we could see how Windows XP entry looks in grub.

---

### Post by xdavidx on 2008-06-26
> **manfer said:**
> That makes no sense for me. Could you explain better what you mean?

Have you installed grub yourself or the installation made it for you? If you did it, how did you do it?

sorry, i haven't seen this response, when i say "together" is in the same hardrive where winxp is installed..since ubuntu is on another..i know that's is the default..but don't know..and it installed grub itself, not me.

---

### Post by xdavidx on 2008-06-26
> **manfer said:**
> Only trying to guess. Could someone tell if mounting the NTFS filesystem where Windows XP resides and not properly being unmounted at shutdown could affect?.

I don't know how ubuntu could be affecting your XP. Think of how the boot process in a computer takes place. In your case when you run Windows XP. First the BIOS is loaded, BIOS pass control to grub on MBR, grub pass control to XP loader. As you see ubuntu is not implied in that process unless grub passing control to XP loader. If you post menu.lst as I suggested we could see how Windows XP entry looks in grub.

i'll post it tomorrow, cause it's 1am here and i've to wake up earlier tomorrow..and i'm not with the computer in this moment. thks too all anyway, and tomorrow we will try to figure out what happened..again.

---

### Post by manfer on 2008-06-26
> **xdavidx said:**
> sorry, i haven't seen this response, when i say "together" is in the same hardrive where winxp is installed..since ubuntu is on another..i know that's is the default..but don't know..and it installed grub itself, not me.

Grub and XP are on same disk but not in same location. While XP is in a partition on disk, grub is on MBR of disk. That is why I asked you if ubuntu installation installed grub for you, or you installed it by yourself. But as grub loads properly seems no error there, you said you can boot ubuntu and Windows XP and the only thing you are reporting is bad performance in XP.

Let's see tomorrow the menu.lst.

---

### Post by ad_267 on 2008-06-26
Did you defrag the windows partition first?

My windows definitely didn't get slower but it seems so much slower now in comparison to Ubuntu.

---

### Post by xdavidx on 2008-06-27
> **manfer said:**
> Grub and XP are on same disk but not in same location. While XP is in a partition on disk, grub is on MBR of disk. That is why I asked you if ubuntu installation installed grub for you, or you installed it by yourself. But as grub loads properly seems no error there, you said you can boot ubuntu and Windows XP and the only thing you are reporting is bad performance in XP.

Let's see tomorrow the menu.lst.

Here is the grub menu.lst of my father's laptop, in this case the situation is the same, the difference was the instalation of it that was made in a clear partition and not in a different hard drive like my desktop was.. the boot u see in this line "title	Windows NT/2000/XP" it's just the recovery boot of sony vaio. i haven't change anything.


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
# kopt=root=UUID=7d4f0c96-c2b2-4661-8b73-670c05e496b5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
# defoptions=quiet splash locale=pt_PT

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7d4f0c96-c2b2-4661-8b73-670c05e496b5 ro quiet splash locale=pt_PT
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7d4f0c96-c2b2-4661-8b73-670c05e496b5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7d4f0c96-c2b2-4661-8b73-670c05e496b5 ro quiet splash locale=pt_PT
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7d4f0c96-c2b2-4661-8b73-670c05e496b5 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7d4f0c96-c2b2-4661-8b73-670c05e496b5 ro quiet splash locale=pt_PT
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7d4f0c96-c2b2-4661-8b73-670c05e496b5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by manfer on 2008-06-27
That looks correct. If Windows XP was loading properly, it was unlikely an error in menu.lst. So if XP is booting and with the control of the computer I don't see how could ubuntu affect XP.

How did you do the partitioning in those cases needed? Ubuntu installation did it for you?

You can list a disk partition table with fdisk in the terminal. Try:

promp:~$ **sudo fdisk -l /dev/sda**

-l option list partition table.
/dev/sda parameter must be your disk device. If not that one, you must change it.

Then post it here and maybe someone could see something strange on partition table.

Have you tried the defrag in windows as someone suggest too?

---

### Post by Topsiho on 2008-06-27
Installing Ubuntu alongside XP does not affect XP of course, but for one thing, which I don't think is explicitly mentioned in the other reactions (if it is, I apologise :)  ): Space on the disk.
To install Ubuntu you need to give it space in which you install it, space that probably was available for XP, and now is not.
If the space in which XP now has to operate on the HD is too small, it will certainly go slower and possibly even halt.

Topsiho

---

### Post by manfer on 2008-06-27
Another question too, which option are you choosing for installation, are you using wubi?

For what you said I think you are installing on other disk and other partition and not using wubi, but only to confirm it.

---

### Post by imbjr on 2008-06-27
> **Topsiho said:**
> Installing Ubuntu alongside XP does not affect XP of course, but for one thing, which I don't think is explicitly mentioned in the other reactions (if it is, I apologise :)  ): Space on the disk.
To install Ubuntu you need to give it space in which you install it, space that probably was available for XP, and now is not.
If the space in which XP now has to operate on the HD is too small, it will certainly go slower and possibly even halt.

Topsiho

I was thinking of this too. If one mercilessly cuts down the HD space allotted to XP, it will not be able to create a swap file of much utility and therefore, indeed, XP will run like a dog.

---

### Post by xdavidx on 2008-06-27
> **manfer said:**
> Another question too, which option are you choosing for installation, are you using wubi?

For what you said I think you are installing on other disk and other partition and not using wubi, but only to confirm it.

yes, in my desktop i've done that, Xp in one hard drive and Ubuntu on another Hard drive, no partition, and ubuntu disc had 230gb.

---

### Post by xdavidx on 2008-06-27
> **Topsiho said:**
> Installing Ubuntu alongside XP does not affect XP of course, but for one thing, which I don't think is explicitly mentioned in the other reactions (if it is, I apologise :)  ): Space on the disk.
To install Ubuntu you need to give it space in which you install it, space that probably was available for XP, and now is not.
If the space in which XP now has to operate on the HD is too small, it will certainly go slower and possibly even halt.

Topsiho

in my father's laptop it was installed on a partition with 90gb..

---

### Post by xdavidx on 2008-06-27
i haven't used wubi for both installations.

---

### Post by chrisccoulson on 2008-06-27
I definately don't see how Ubuntu on a separate partition can directly be responsible for making XP slower. It just isn't at all possible - they are completely separate systems and don't interact at all (perhaps apart from mounting the partition of one operating system from the other). 

The only possible way's have already been mentioned by other posters, and relate to the fact that XP now resides on a smaller partition. A smaller NTFS partition will fragment faster (especially if it is quite full), and that is not the fault of Ubuntu. Have you de-fragmented the partition since you resized it? You're also meant to defragment NTFS partitions before resizing them.

I run XP dual-boot with Ubuntu, and I know plenty of other people that do as well. I've never come across this phenomenon before.

You'd be better off asking this type of question in a Microsoft support forum. After all, it is the XP system which is exhibiting these 'slowing down' problems.

---

### Post by xdavidx on 2008-06-27
> **chrisccoulson said:**
> I definately don't see how Ubuntu on a separate partition can directly be responsible for making XP slower. It just isn't at all possible - they are completely separate systems and don't interact at all (perhaps apart from mounting the partition of one operating system from the other). 

The only possible way's have already been mentioned by other posters, and relate to the fact that XP now resides on a smaller partition. A smaller NTFS partition will fragment faster (especially if it is quite full), and that is not the fault of Ubuntu. Have you de-fragmented the partition since you resized it? You're also meant to defragment NTFS partitions before resizing them.

I run XP dual-boot with Ubuntu, and I know plenty of other people that do as well. I've never come across this phenomenon before.

You'd be better off asking this type of question in a Microsoft support forum. After all, it is the XP system which is exhibiting these 'slowing down' problems.

i know, that's not normal that's why i asked..because only when i've installed ubuntu on it i noticed that..but i will try to reinstall everything again..making de defrag and everything else..and then i'll post how the system is going.. thks for all of your help..since i'm the only one with the same problem in 2 different computers maybe something's wrong..and i didn't realize..

---

### Post by manfer on 2008-06-27
The defrag suggestion is on Windows XP now. No need to reinstall nothing, just try the defragmentation of the drive with Windows XP in it. Just booting into Windows XP. Try it before going to reinstall. Maybe it helps. 

And the space suggestion, is there little space in Windows XP after installation of ubuntu? How much free space do you have in Windows XP? No matter the space you gave ubuntu, what would be important to know is the space windows XP has free for itself now.

Please try defrag and answer this questions before reinstall.

I suppose you know how to do the defragmentation of disk in Windows. I right-click on the drive you want to defrag and on the menu that pop you select properties. In the window that comes up you would find the utility to do defragmentation.

---

### Post by issih on 2008-06-27
Doubtful this will really be the problem, but bear in mind that a great many of the programs we install these days have auto update facilties. If you have a dual boot machine and only start into windows occasionally, all of those little update agents are going to suddenly fire up, because they haven't had access to the internet for quite some time. These things could easily slow down the pc whilst they merrily download things in the background, this will have a particularly noticeable effect on any web browsing etc.

Anyone unfortunate enough to have run Norton antivirus will know exactly how bad this kinf of thing can be.

Does the pc speed up again if you leave it to its own devices for a while? if so, its probably just something to do with update services kicking in.

---

### Post by manfer on 2008-06-27
That suggestion looks interesting. It could be the problem.

The release of SP3 is very recent. I don't know if it is downloaded automatically by windows update if automatic updates are enable. But if so, that could be a long and large download and mostly if you don't have a fast internet line. That and the other program updates could be causing the problem.

---

### Post by Canis familiaris on 2008-06-27
> **xdavidx said:**
> i know, that's not normal that's why i asked..because only when i've installed ubuntu on it i noticed that..but i will try to reinstall everything again..making de defrag and everything else..and then i'll post how the system is going.. thks for all of your help..since i'm the only one with the same problem in 2 different computers maybe something's wrong..and i didn't realize..

How much space did you give to XP? Anything less than 3GB and it will be slow like hell.
BTW With time the slowing down of Windows in inevitable. Happens with me too. But installing Ubuntu has nothing to do with it.

---

### Post by Canis familiaris on 2008-06-27
Also run msconfig and try to run Windows in diagnostic mode and see whether it helps.

---

### Post by Austin_KW on 2008-06-27
If windows was paging/swaping onto the spare disk, windows may slow down if the second disk is not available and it has to page onto the same disk that the OS is running from.

---

### Post by Habbit on 2008-06-27
This may be a bit naïve, but if you've already checked all that "free space on XP disk" things, maybe this is the explanation that remains: you said you started using only ubuntu and entering XP occasionally. Well, it is possible that since you boot XP just once in, say, a week, it always finds updates to perform (which means slow internet), and then on reboot those updates have to be applied, which results on slow boots.

I know it sounds stupid, but its the only think I could think that did not involve the memory/swapfile rationale (again, did you check that Windows has a swapfile with enough size? how much RAM do you have?) and I've personally experienced it with XP Pro x64: I boot it just once in a while for wine-resistant gaming and it has a rough time starting :popcorn:

---

### Post by xdavidx on 2008-06-27
> **manfer said:**
> The defrag suggestion is on Windows XP now. No need to reinstall nothing, just try the defragmentation of the drive with Windows XP in it. Just booting into Windows XP. Try it before going to reinstall. Maybe it helps. 

And the space suggestion, is there little space in Windows XP after installation of ubuntu? How much free space do you have in Windows XP? No matter the space you gave ubuntu, what would be important to know is the space windows XP has free for itself now.

Please try defrag and answer this questions before reinstall.

I suppose you know how to do the defragmentation of disk in Windows. I right-click on the drive you want to defrag and on the menu that pop you select properties. In the window that comes up you would find the utility to do defragmentation.

okay i'll try that, about 50gb free on xp.

---

### Post by xdavidx on 2008-06-27
> **issih said:**
> Doubtful this will really be the problem, but bear in mind that a great many of the programs we install these days have auto update facilties. If you have a dual boot machine and only start into windows occasionally, all of those little update agents are going to suddenly fire up, because they haven't had access to the internet for quite some time. These things could easily slow down the pc whilst they merrily download things in the background, this will have a particularly noticeable effect on any web browsing etc.

Anyone unfortunate enough to have run Norton antivirus will know exactly how bad this kinf of thing can be.

Does the pc speed up again if you leave it to its own devices for a while? if so, its probably just something to do with update services kicking in.

i have a good connection speed, cable 18Mb, and i don't use norton it eats all the memory..:P

---

### Post by xdavidx on 2008-06-27
> **Anurag_panda said:**
> How much space did you give to XP? Anything less than 3GB and it will be slow like hell.
BTW With time the slowing down of Windows in inevitable. Happens with me too. But installing Ubuntu has nothing to do with it.

90Gb.

---

### Post by xdavidx on 2008-06-27
> **Anurag_panda said:**
> Also run msconfig and try to run Windows in diagnostic mode and see whether it helps.

i'll try that to. ;)

---

### Post by xdavidx on 2008-06-27
> **Habbit said:**
> This may be a bit naïve, but if you've already checked all that "free space on XP disk" things, maybe this is the explanation that remains: you said you started using only ubuntu and entering XP occasionally. Well, it is possible that since you boot XP just once in, say, a week, it always finds updates to perform (which means slow internet), and then on reboot those updates have to be applied, which results on slow boots.

I know it sounds stupid, but its the only think I could think that did not involve the memory/swapfile rationale (again, did you check that Windows has a swapfile with enough size? how much RAM do you have?) and I've personally experienced it with XP Pro x64: I boot it just once in a while for wine-resistant gaming and it has a rough time starting :popcorn:

have 2GB RAM, and the swap never made any changes, windows is managing it.

---

### Post by xdavidx on 2008-06-27
> **Austin_KW said:**
> If windows was paging/swaping onto the spare disk, windows may slow down if the second disk is not available and it has to page onto the same disk that the OS is running from.

Have to check that too..

---

### Post by xdavidx on 2008-06-27
Okay, i just want to say that i'll perform those tests and everything and see what happens, then i'll repost if i've found out the problem of it or not, anyway thanks to all that gave me advices, i'll try them. Hope i can solve this "unique" problem :P

Cheers, Ubuntu rocks!!

---

