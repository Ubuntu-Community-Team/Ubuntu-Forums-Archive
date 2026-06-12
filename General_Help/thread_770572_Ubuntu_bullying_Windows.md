---
title: "Ubuntu bullying Windows"
date: 2008-04-27
forum: General Help
---

### Post by CorruptNoob on 2008-04-27
So I used gparted to split my windows partition into 2, so I could install ubuntu on its own little comfortable space, so it could move around and such without being windows' bitch (which it was when I had my wubi install)

Anyway, so I did the partitions and restarted to see if I could still get into windows, and I can't! computer just keeps restarting when it tries to boot from disk


So I'm a bit sad, a bit confused, a bit disappointed in ubuntu for not taking the high-road and instead stooping down to poor windows' level, and trapping it somewhere in my HDD.

How do I free my windows?

It's a Vista installation, it came pre-installed, I have a DELL recovery CD, so I don't know if I can use that to go into recovery mode and type whatever command.


I'm on the LiveCD atm, installing ubuntu, I can see the partition called "OS" which windows is on, but I can't open it (no response when clicked)

so yeah.. yet another sad day for CorruptNoob

SoS!

---

### Post by CorruptNoob on 2008-04-27
Ubuntu is now installed.

I tried to load Windows Vista via GRUB, it just restarts the machine.. help.

---

### Post by CorruptNoob on 2008-04-27
I can access my OS drive through Ubuntu now (the windows one)

Just an update, don't know if it helps anyone help me

---

### Post by jsgarvin on 2008-04-27
I had a very similar issue recently.  I resized a windows partition to make room for Ubuntu and after doing so, couldn't boot into Windows. This was before GRUB or Ubuntu got installed, so Windows just didn't like having it's partition resized.

Now I just run Windows inside VMWare on top of Ubuntu for those rare times that I actually NEED to do something in Windows.

---

### Post by CorruptNoob on 2008-04-27
Also there seems to be lost+found folders inside / and /home taking up a considerable amount of space, how do I get rid of them.. or what are they

---

### Post by TeoBigusGeekus on 2008-04-27
Post the results of 
```
sudo fdisk -l
```
(-L)

and the contents of your menu.lst file
```
sudo gedit /boot/grub/menu.lst
```
(.LST)

---

### Post by CorruptNoob on 2008-04-27
> **jsgarvin said:**
> I had a very similar issue recently.  I resized a windows partition to make room for Ubuntu and after doing so, couldn't boot into Windows. This was before GRUB or Ubuntu got installed, so Windows just didn't like having it's partition resized.

Now I just run Windows inside VMWare on top of Ubuntu for those rare times that I actually NEED to do something in Windows.


You didn't get it working then? Also, what's VMWare?

---

### Post by ghost_ryder35 on 2008-04-27
Did you defrag your hard drive before re-sizing your partiton.  If not this is why this is happening.  You might beable to recover windows by booting into the UBCD4WIN cd or the Windows Recovery option on the vista CD and issuing 
```

fixmbr
fix boot

```
this will kill grub, so you will have to defrag and then reinstall grub via the live cd (see signature)  you will probally have lost some files in windows

---

### Post by CorruptNoob on 2008-04-27
> **TeoBigusGeekus said:**
> Post the results of 
```
sudo fdisk -l
```
(-L)

and the contents of your menu.lst file
```
sudo gedit /boot/grub/menu.lst
```
(.LST)




Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            7650       16907    74364885   83  Linux
/dev/sda2           16908       19387    19920600   83  Linux
/dev/sda3   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda4           19388       19457      562275   82  Linux swap / Solaris

Partition table entries are not in disk order








AND


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
# kopt=root=UUID=d06ab294-acdd-4e7c-acc8-fdb30eaa0e48 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d06ab294-acdd-4e7c-acc8-fdb30eaa0e48 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d06ab294-acdd-4e7c-acc8-fdb30eaa0e48 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

---

### Post by CorruptNoob on 2008-04-27
> **ghost_ryder35 said:**
> you didnt defrag your hard drive before re-sizing your partiton



Yes I didn't and I realise that was not exactly the smartest thing to do, however I still need to fix this problem.. I have lost+found directories inside /home and / which I can't access, and Vista won't load!

---

### Post by ghost_ryder35 on 2008-04-27
> **CorruptNoob said:**
> You didn't get it working then? Also, what's VMWare?
VMware virualizes hardware in a application so you can Vitualize an operating system while in another operating system

---

### Post by Martin Witte on 2008-04-27
> **CorruptNoob said:**
> Also there seems to be lost+found folders inside / and /home taking up a considerable amount of space, how do I get rid of them.. or what are they[here's a lost and found description]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html")

---

### Post by hyper_ch on 2008-04-27
for vista partitioning you should use the vista partitioner :(

---

### Post by ghost_ryder35 on 2008-04-27
> **CorruptNoob said:**
> Yes I didn't and I realise that was not exactly the smartest thing to do, however I still need to fix this problem.. I have lost+found directories inside /home and / which I can't access, and Vista won't load!
read my post again, i told you how to boot into vista

---

### Post by TeoBigusGeekus on 2008-04-27
Do you get any error messages when you choose vista in grub?

---

### Post by CorruptNoob on 2008-04-27
So what do I do? and how do I get rid of the lost and found dir?

---

### Post by the8thstar on 2008-04-27
Nothing wrong with fstap and grub reports. Your Vista is still there and Grub tries to load it... but Vista can't.

From there, you can try several options. For one, sometimes Vista gets a heart attack if its partition is not set to 'boot' with the flag manager. If you go in the terminal and type

> sudo gparted

you will get a GUI with a list of all your partitions. Select the Vista one, right click and choose manage flags'; set it to boot and restart the computer. Choose Vista in Grub and see what happens.

If this doesn't work, you can try to repair the Vista partition with Vista's install DVD (not some recovery disc of some sort). Do you have it?

---

### Post by ghost_ryder35 on 2008-04-27
> **ghost_ryder35 said:**
> Did you defrag your hard drive before re-sizing your partiton. If not this is why this is happening. You might beable to recover windows by booting into the UBCD4WIN cd or the Windows Recovery option on the vista CD and issuing 
```

fixmbr
fix boot

```
this will kill grub, so you will have to defrag and then reinstall grub via the live cd (see signature) you will probally have lost some files in windows
:guitar:

---

### Post by CorruptNoob on 2008-04-27
> **the8thstar said:**
> Nothing wrong with fstap and grub reports. Your Vista is still there and Grub tries to load it... but Vista can't.

From there, you can try several options. For one, sometimes Vista gets a heart attack if its partition is not set to 'boot' with the flag manager. If you go in the terminal and type



you will get a GUI with a list of all your partitions. Select the Vista one, right click and choose manage flags'; set it to boot and restart the computer. Choose Vista in Grub and see what happens.

If this doesn't work, you can try to repair the Vista partition with Vista's install DVD (not some recovery disc of some sort). Do you have it?



sudo: gparted: command not found


First problem!


Also no, it's a Dell laptop, so it came with the dell restore CD only!

---

### Post by CorruptNoob on 2008-04-27
> **TeoBigusGeekus said:**
> Do you get any error messages when you choose vista in grub?

No error messages


The link in the persons sig for reinstall grub asks me for an admin user/pass!

---

### Post by ghost_ryder35 on 2008-04-27
you can download the UBCD4WIN or uses an old Windows XP cd or the Dell CD probally will allow you to boot to the restore command prompt

---

### Post by the8thstar on 2008-04-27
> sudo: gparted: command not found

Okay... that's a bit odd, but whatever.

type:

> apt-get install gparted

in the terminal. And follow my previous post indications.

> Also no, it's a Dell laptop, so it came with the dell restore CD only!

That bites the big one. Looks like you will have to download UBCD4WIN then.

---

### Post by ghost_ryder35 on 2008-04-27
> **CorruptNoob said:**
> No error messages
 
 
The link in the persons sig for reinstall grub asks me for an admin user/pass!
reinstalling grub before fixing the vista **fixmbr** and **fix boot** will not do any good. you have to do it in this order or else it wont work because when you **fixmbr** it is going to KILL grub, that is why these commands must be entered in this order

---

### Post by CorruptNoob on 2008-04-27
> **ghost_ryder35 said:**
> you can download the UBCD4WIN or uses an old Windows XP cd or the Dell CD probally will allow you to boot to the restore command prompt

I have an old Windows XP disk, if you're sure this is fine for Windows Vista.


Are you sure I need to FIXMBR and FIXBOOT? I will probably mess up the GRUB installation!

---

### Post by ghost_ryder35 on 2008-04-27
yes i am sure the xp disc will work, and yes i am sure you need fixmbr and fix boot and yes i am positive it will kill grub thats why i have provided the link to reinstall grub via the live cd

---

### Post by CorruptNoob on 2008-04-27
This is a screenshot from gparted

---

### Post by ghost_ryder35 on 2008-04-27
> **CorruptNoob said:**
> This is a screenshot from gparted
y are you worring about gparted?  you should be booted into your windows xp cd by now in the recovery console issuing those commands so you can save your vista install

---

### Post by CorruptNoob on 2008-04-27
> **ghost_ryder35 said:**
> yes i am sure the xp disc will work, and yes i am sure you need fixmbr and fix boot and yes i am positive it will kill grub thats why i have provided the link to reinstall grub via the live cd

Okay, by the way the link to the guide in your sig is broken!


If I decided that reinstalling GRUB was beyond my ability right now, can I re-install vista onto a partition? or does it eat the whole disk?

---

### Post by CorruptNoob on 2008-04-27
> **ghost_ryder35 said:**
> y are you worring about gparted?  you should be booted into your windows xp cd by now in the recovery console issuing those commands so you can save your vista install

Ok ok ok I'll reboot into the recovery, type FIXMBR and FIXBOOT, and hopefully be back here on vista..

---

### Post by ghost_ryder35 on 2008-04-27
vista is still installed on your computer, you just cant boot into it. when you issue the commands i am talking about your computer will not have grub anymore and just boot into windows vista. if later you want to boot into ubuntu you will have to reinstall grub.  And when you reinstall grub you will be able to dual boot with windows and ubuntu.  the only reason your dual boot was messed up is because you didnt defrag first before resizing.
 
p.s. the link in my sig in fine.

---

### Post by CorruptNoob on 2008-04-27
Hi, I just tried to enter those commands in the recovery console.


FIXMBR does nothing, doesn't say it's an invalid command or anything, just does nothing.

FIXBOOT worked, anyway, when I restarted, GRUB loaded, I tried windows, it just restarts as per usual, and ubuntu loads fine which is why i'm back here..

---

### Post by ghost_ryder35 on 2008-04-27
hmmm..... its definetly fixmbr
[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)
you can try to specify the location to install
try 
```

fixmbr \Device\HardDisk0

```
make sure you specify the correct hard drive if you have more than one.  Master is 0 Slave is 1

---

### Post by CorruptNoob on 2008-04-27
> **ghost_ryder35 said:**
> hmmm..... maybe its fix mbr
you can type help in the recory console and see the correct syntax but it is correct



fix mbr is an invalid command, fixmbr doesn't tell me it's invalid just.. does nothing..


anyway.. I will go type help as you suggested and brb

---

### Post by ghost_ryder35 on 2008-04-27
yea it is definetly fixmbr
try specifying a location for the mbr to be written to like above post

---

### Post by CorruptNoob on 2008-04-27
> **ghost_ryder35 said:**
> hmmm..... its definetly fixmbr
[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)
you can try to specify the location to install
try 
```

fixmbr \Device\HardDisk0

```
make sure you specify the correct hard drive if you have more than one.  Master is 0 Slave is 1

It's a laptop so one hdd, I tried the specific command in the quote, said invalid Mbr detected would I like to proceed, said yes, restarted, grub still loads windows still has same problem, I'm on iPhone now so i don't have to bot ubuntu again, please help

---

### Post by CorruptNoob on 2008-04-27
Do you think I should just re-install vista?


and can I reinstall vista onto the currently broken partition where the broken vista is installed, will GRUB automatically pick it up?

---

### Post by CorruptNoob on 2008-04-27
someone save me :D

---

### Post by the8thstar on 2008-04-27
> **CorruptNoob said:**
> Do you think I should just re-install vista?


and can I reinstall vista onto the currently broken partition where the broken vista is installed, will GRUB automatically pick it up?

That depends.

1. If you are using a Vista Install disk, you will be able to reinstall Vista by choosing 'repair disk'.

2. If you are using a recovery disk, you will restore the factory settings on your computer and both Ubuntu and your current Vista partition will be destroyed.

**[COLOR="Red"][B]In either case, save your important documents to a CD / USB key NOW before they are erased by accident.**[/COLOR][/B]

After that, when you reinstall Ubuntu from the LiveCD, Grub will pickup the Vista bootloader and incorporate it into the menu.lst file.

---

### Post by CorruptNoob on 2008-04-27
> **the8thstar said:**
> That depends.

1. If you are using a Vista Install disk, you will be able to reinstall Vista by choosing 'repair disk'.

2. If you are using a recovery disk, you will restore the factory settings on your computer and both Ubuntu and your current Vista partition will be destroyed.

**[COLOR="Red"][B]In either case, save your important documents to a CD / USB key NOW before they are erased by accident.**[/COLOR][/B]

After that, when you reinstall Ubuntu from the LiveCD, Grub will pickup the Vista bootloader and incorporate it into the menu.lst file.

Dells cd let me choose what partition to install to, currently reinstalin vista to desired partition, I'm on iPhone right now, how will this affect grub?

---

### Post by the8thstar on 2008-04-27
Reinstalling Vista will erase the info that Grub wrote in the MBR (the Master Boot Record). This will not affect the program itself, since Grub resides in /boot/Grub on your Ubuntu partition.

However, you will only be able to access Vista from there on. In order to use Ubuntu again, you will need to reinstall the Grub into the MBR. You can do it as ghost_ryder35 advised, or by using the Ubuntu liveCD.

---

### Post by Rainstride on 2008-04-27
to fix the boot problem with vista/ubuntu install all you have to do is put in you recovery cd DO NOT RESTORE EVERYTHING!! look for where it says check repair options or something of the like, im not sure what its like on the dell disk. there should be a option to repair windows errors or check for problems. it will scan and find that the boot manager is "damaged" or so it thinks, it should fix the problem automaticly. then you can boot into vista and config the win boot manager, so you can choose at startup what OS you want.

---

### Post by the8thstar on 2008-04-27
> **Rainstride said:**
> then you can boot into vista and config the win boot manager, so you can choose at startup what OS you want.

That is not 100% fullproof. In all the instances I had before, Vista bootloader never recognized Ubuntu as a valid OS. This is why I was avdvising our friend to use Grub, which does.

*Another option would be to install EasyBCD in Windows, but this is adding another layer of complexity, which **CorruptNoob** doesn't need right now, IMO.*

---

### Post by CorruptNoob on 2008-04-27
> **the8thstar said:**
> That is not 100% fullproof. In all the instances I had before, Vista bootloader never recognized Ubuntu as a valid OS. This is why I was avdvising our friend to use Grub, which does.

*Another option would be to install EasyBCD in Windows, but this is adding another layer of complexity, which **CorruptNoob** doesn't need right now, IMO.*



I've installed vista and am on it now,

how do I reinstall Grub using the LiveCD?

---

### Post by ghost_ryder35 on 2008-04-27
> **CorruptNoob said:**
> I've installed vista and am on it now,
 
how do I reinstall Grub using the LiveCD?
my sig

---

### Post by CorruptNoob on 2008-04-27
Hi, i'm still on Windows, I can't access my external HDD through windows anymore since I used it in linux, it says it's corrupt or unreadable, uhoh! This is 400gb worth of my life :(

---

### Post by the8thstar on 2008-04-27
*Edited from Ghost_Ryder35 signature - Original post by Catlett*
**How to restore Grub from a live Ubuntu cd.** 

This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)


Code:
> sudo grub
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


Code:
> find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


Code:
> root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:
> setup (hd0)

Finally exit the grub shell

Code:
> quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Now the explanation.
Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition, grub will use the mbr. hd0 is the grub label for the first drive's mbr.
Quit will exit you from the grub shell.


**End of edit**

Your Windows install should be picked up automatically and added to Grub at startup.

---

### Post by ghost_ryder35 on 2008-04-27
> **CorruptNoob said:**
> Hi, i'm still on Windows, I can't access my external HDD through windows anymore since I used it in linux, it says it's corrupt or unreadable, uhoh! This is 400gb worth of my life :(
run a check disk on it and everything will be fine :) make sure to auto recover or whatever the option is
 
to do that
**1. Right click on external drive in my computer**
**2. Choose properties**
**3. Click tools tab**
**4. Then click check disk**
**5. Then click auto recover**

---

### Post by the8thstar on 2008-04-27
I don't want to sound selfish here, but I believe **Ghost_Ryder 35 **and I both deserve that you check the little gold star next to our posts. That would be a great way to thank us for our efforts for you.

---

### Post by ghost_ryder35 on 2008-04-27
> **the8thstar said:**
> I don't want to sound selfish here, but I believe **Ghost_Ryder 35 **and I both deserve that you check the little gold star next to our posts. That would be a great way to thank us for our efforts for you.
"Agreed :cough: :cough: Agreed" ;)

---

### Post by CorruptNoob on 2008-04-27
> **ghost_ryder35 said:**
> "Agreed :cough: :cough: Agreed" ;)

hi in on my iPhone, in regards to the thanking, I was planning in batch-thanking once I'm sorted :p currently booting ubuntu live

---

### Post by Rainstride on 2008-04-27
i though grub wasn't able to load into vista.... atleast thats what i was lead to belive(lies?)... witch is why i just went full ubuntu insted of bothering with a vista dual. oh well, worked out better this way...

---

### Post by ghost_ryder35 on 2008-04-27
> **Rainstride said:**
> i though grub wasn't able to load into vista.... atleast thats what i was lead to belive(lies?)... witch is why i just went full ubuntu insted of bothering with a vista dual. oh well, worked out better this way...
:confused: Grub just tells the hard drive where to boot from.  As long as Vista/XP/ME/2000/98/95/3.1.1/3.1 are installed first and defragged fully before you resize your partitions and install Ubuntu there is no problem.

---

### Post by CorruptNoob on 2008-04-27
> **ghost_ryder35 said:**
> run a check disk on it and everything will be fine :) make sure to auto recover or whatever the option is
 
to do that
**1. Right click on external drive in my computer**
**2. Choose properties**
**3. Click tools tab**
**4. Then click check disk**
**5. Then click auto recover**

Hi, it says it cannot access the disk when I select that! :popcorn:

---

### Post by Rainstride on 2008-04-27
oh, i need to find better linux reading it seems..... although iv mostly been reading about security... maybe thats my problem...

---

### Post by ghost_ryder35 on 2008-04-27
what happens if you saftley remove it and unplug the cable and replug it in, can you do it then?

---

### Post by CorruptNoob on 2008-04-27
> **ghost_ryder35 said:**
> what happens if you saftley remove it and unplug the cable and replug it in, can you do it then?


when I try to safely remove it says

"windows can't stop your 'generic volume' device because it is in use ...... "

!?

---

### Post by ghost_ryder35 on 2008-04-27
go to the start button "or in vista the windows logo and choose the arrow that points to the right and then "Shutdown".  Let it fully shutdown the system.  Then reboot and as soon as it is booted back up try to saftley remove it again.

---

### Post by CorruptNoob on 2008-04-27
Currently installing windows updates, should be able to shut down soon!

Is there any way to re-order GRUB's OS list?

I'd rather vista be first so it automatically boots into it after time-out

---

### Post by the8thstar on 2008-04-27
Gee, this is a tough one.

Okay, Vista is not capable to read ext2/ext3 partition natively (that's the Ubuntu file system) which is why you can't do squat with your Ubuntu formatted drive from within Vista.

Thankfully there is a program called [ext2FS]("http://www.fs-driver.org/") which you are going to download and install in Vista. Then go to the Control Pnael, select the ext2FS applet and assign a letter to your Ubuntu drive. From there, you will be able to access your Ubuntu files within Vista.

You can select Vista to be the default OS!

1. Log into Ubuntu
2. Launch the terminal
3. Type:
> sudo gedit /boot/grub/menu.lst
4. add the following line the config after the ##default paragraph
> default=4
5. Save
6. Reboot your computer.

---

### Post by CorruptNoob on 2008-04-27
> **the8thstar said:**
> Gee, this is a tough one.

Okay, Vista is not capable to read ext2/ext3 partition natively (that's the Ubuntu file system) which is why you can't do squat with your Ubuntu formatted drive from within Vista.

Thankfully there is a program called [ext2FS]("http://www.fs-driver.org/") which you are going to download and install in Vista. Then go to the Control Pnael, select the ext2FS applet and assign a letter to your Ubuntu drive. From there, you will be able to access your Ubuntu files within Vista.

You can select Vista to be the default OS!

1. Log into Ubuntu
2. Launch the terminal
3. Type:

4. add the following line the config after the ##default paragraph

5. Save
6. Reboot your computer.

Hi, I understand that Vista cannot read ext3, I was planning on using that software so vista and ubuntu could share my big /home partition.

The problem here is Vista can no longer read my external 400gb hdd, ntfs!

---

### Post by CorruptNoob on 2008-04-27
I still can't access my external HDD from windows.. sad times :(

---

### Post by CorruptNoob on 2008-04-27
bump for great justice

---

### Post by ghost_ryder35 on 2008-04-27
can you defrag it?

---

### Post by CorruptNoob on 2008-04-27
I think it's defragging.. it's not giving me any indication of which disk it's defragging, but it's defragging something...

This is quite worrying, if I lose this hdd I'll be screwed!


Whilst it's defragging, let's see if we can make this thread any longer!

How do I delete the lost+found folder in /home and in /

---

### Post by ghost_ryder35 on 2008-04-27
which hard drive has activity your computer or the external?  You can tell this by seeing which ones activity light is flashing more rapidly.

---

### Post by CorruptNoob on 2008-04-27
The external Light isn't flashing at all,, the internal one is though

---

### Post by CorruptNoob on 2008-04-27
> **ghost_ryder35 said:**
> can you defrag it?



"Corrupted or unreadable"


screenshots below

---

### Post by ghost_ryder35 on 2008-04-27
this drive is formatted NTFS right?  Download and burn the UBCD4WIN and see if you can run a check disk from there.  THE CD wont mount the drive so it "should" work hopefully.

---

### Post by CorruptNoob on 2008-04-27
Yep it's NTFS, downloading the ultimate bootCd now.. will be a while


Can I put it onto a USB stick or does it have to be CD?

---

### Post by ghost_ryder35 on 2008-04-27
> **CorruptNoob said:**
> Yep it's NTFS, downloading the ultimate bootCd now.. will be a while
 
 
Can I put it onto a USB stick or does it have to be CD?
that I do not know.  But it would be good to have on CD because it can save your *** multiple times.  It will boot into a LIVE Windows enviorment right off the CD...
P.S> you will need your Windows XP CD for this adventure as you will have to build the iso image if I remember correctly.

---

### Post by CorruptNoob on 2008-04-27
I ran CMD as administrator whilst waiting for this download to finish:




C:\Windows\system32>chkdsk E:
The type of the file system is NTFS.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
  56000 file records processed.
File verification completed.
  130 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 3)...
Index entry $Quota in index $I30 of file 11 is incorrect.
  208776 index entries processed.
Index verification completed.

Errors found.  CHKDSK cannot continue in read-only mode.

---

### Post by CorruptNoob on 2008-04-27
Huh.. I need my XP disk for what :D?

---

### Post by CorruptNoob on 2008-04-27
I'm running chkdsk /F E:    apparently locks the HD so that it doesn't have to run as read-only, it seems to be creating and inserting things... and it's done:


C:\Windows\system32>chkdsk /F E:
The type of the file system is NTFS.

CHKDSK is verifying files (stage 1 of 3)...
  56000 file records processed.
File verification completed.
  130 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 3)...
Deleting index entry $Quota in index $I30 of file 11.
  208776 index entries processed.
Index verification completed.
  5 unindexed files processed.
Creating quota file.
Inserting an index entry into index $I30 of file 11.
Creating index $O for file 17.
Creating index $Q for file 17.
Inserting default quota record into index $Q in file 17.
CHKDSK is verifying security descriptors (stage 3 of 3)...
  56000 security descriptors processed.
Security descriptor verification completed.
  3860 data files processed.
Correcting errors in the master file table's (MFT) BITMAP attribute.
CHKDSK discovered free space marked as allocated in the volume bitmap.
Windows has made corrections to the file system.

 390708800 KB total disk space.
 386957476 KB in 50638 files.
     19884 KB in 3863 indexes.
         0 KB in bad sectors.
    134212 KB in use by the system.
     65536 KB occupied by the log file.
   3597228 KB available on disk.

      4096 bytes in each allocation unit.
  97677200 total allocation units on disk.
    899307 allocation units available on disk.

C:\Windows\system32>

---

### Post by ghost_ryder35 on 2008-04-27
> **CorruptNoob said:**
> I ran CMD as administrator whilst waiting for this download to finish:
 
 
 
 
C:\Windows\system32>chkdsk E:
The type of the file system is NTFS.
 
WARNING! F parameter not specified.
Running CHKDSK in read-only mode.
 
CHKDSK is verifying files (stage 1 of 3)...
56000 file records processed.
File verification completed.
130 large file records processed.
0 bad file records processed.
0 EA records processed.
0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 3)...
Index entry $Quota in index $I30 of file 11 is incorrect.
208776 index entries processed.
Index verification completed.
 
Errors found. CHKDSK cannot continue in read-only mode.
try 
```

**[FONT=Arial][SIZE=2][COLOR=#000099]chkdsk e: /f /r[/COLOR][/SIZE][/FONT]**

```
This should try to recover and locate bad segments

---

### Post by RumorsOfWar on 2008-04-27
There is a slim chance the Windows partition got 'hidden'.
It shouldn't happen, but the first time I set up dual-boot my Windows partition got the hidden property set. Next time you open any partitioning tool, look for that too.

---

### Post by CorruptNoob on 2008-04-27
Another adventure.. so how do I get rid of lost+found folders?

I feel like I forgot to mention that the last chkdsk with the /f parameter fixed the hdd :P

---

### Post by ghost_ryder35 on 2008-04-27
> **CorruptNoob said:**
> Another adventure.. so how do I get rid of lost+found folders?
did you try the 
**[FONT=Arial][SIZE=2][COLOR=#000099]chkdsk e: /f /r[/COLOR][/SIZE][/FONT]**
**[FONT=Arial][SIZE=2][COLOR=#000099]yet?[/COLOR][/SIZE][/FONT]**

---

### Post by ghost_ryder35 on 2008-04-27
> **CorruptNoob said:**
> Another adventure.. so how do I get rid of lost+found folders?
 
I feel like I forgot to mention that the last chkdsk with the /f parameter fixed the hdd :P
yea I feel like that is the most important thing here :guitar: damn I rule :lolflag:

---

### Post by CorruptNoob on 2008-04-27
Haha, well I actually googled the use of chkdsk but you were right on the money a few minutes after :P! Seeing as you rule, tell me how to get rid of lost+found :D?

---

### Post by ghost_ryder35 on 2008-04-27
> **CorruptNoob said:**
> Haha, well I actually googled the use of chkdsk but you were right on the money a few minutes after :P! Seeing as you rule, tell me how to get rid of lost+found :D?
yea I dont rule that much.  What is in the lost+found folder.  I also have one but mine is empty....

---

### Post by ghost_ryder35 on 2008-04-27
Hey check this thread out
[http://ubuntuforums.org/showthread.php?t=229143](http://ubuntuforums.org/showthread.php?t=229143)
explains everything about it.

---

### Post by CorruptNoob on 2008-04-27
mines about 1gig big!

---

### Post by the8thstar on 2008-04-29
> **CorruptNoob said:**
> mines about 1gig big!

You'll be alright. The worse is behind you now! :D

---

### Post by dhysk on 2008-04-29
a bit late and a dollar short, but since vista comes with its own repartitioner its best to use it to create a new partition. Then load in a Linux distro in the freed space.  just FYI thats how I did it back in gusty worked like a charm

---

