---
title: "Dal boot but cant boot to Xp"
date: 2008-03-03
forum: General Help
---

### Post by StarThorn1 on 2008-03-03
I dual booted Linux and XP. I already had xp installed. I installed linuz on a different partion on the same hard drive. When I restart the laptop there is no menu asking me which OS I want.

I cant get to my windows. Help plz

---

### Post by li10 on 2008-03-03
I'm not really knowledgable about this but you'll probably have to change something in the BIOS.
You probably already knew that but if you didn't, don't do anything about it based on my advice! Wait a while for some more educated people to post.

---

### Post by StarThorn1 on 2008-03-03
I dont know much about linux. Im hoping Grub or what ever linux's boot.ini file is, is what someone will tell me to change.

---

### Post by nlong on 2008-03-03
You'll have to change the config for grub.  Here is the Ubuntu Grub HowTo:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

If you're not comfortable with config files installing this may help:
 [http://www.ubuntugeek.com/qgrubeditor-a-visual-grub-configuration-editor.html](http://www.ubuntugeek.com/qgrubeditor-a-visual-grub-configuration-editor.html)

---

### Post by teamkiller87 on 2008-03-03
I don't know if this would work but you may try the following. Run:

```
sudo gedit /boot/grub/menu.lst
```

You probably don't have a section dedicated to Windows XP. You should add one. Unfortunately other than showing how mine looks I can't help any further.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Hope this could help you somehow.

---

### Post by StarThorn1 on 2008-03-03
I read the links provided but they didnt really talk about my problem. I've hit esc and I dont see anything that has to do with XP. Can anyone tell me the code an i'll write it in.

---

### Post by StarThorn1 on 2008-03-03
...anyone?

---

### Post by Aldanga on 2008-03-03
OK, this isn't too hard. I actually just did it last night.

Firstly, do you know what partition your XP install is on? I'm assuming the first.

If that's the case, you've already gotten good advice.

Run the command teamkiller87 provided.

```
sudo gedit /boot/grub/menu.lst
```

Then input this at the end of the file, where you see the option for 'Ubuntu some-random-kernel-stuff' and a failsafe and memtest:

```
title		Microsoft Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1
```
You can change the title to whatever you wish. That's your call. I'm just listing what's in my menu.lst file.

Hope this helps. :)

---

### Post by Hilko on 2008-03-03
If you still have trouble take a look at [the GRUB page]("http://users.bigpond.net.au/hermanzone/p15.htm#splash"). You can find almost anything that has to do with GRUB there.

---

### Post by StarThorn1 on 2008-03-03
> **Aldanga said:**
> OK, this isn't too hard. I actually just did it last night.

Firstly, do you know what partition your XP install is on? I'm assuming the first.

If that's the case, you've already gotten good advice.

Run the command teamkiller87 provided.

```
sudo gedit /boot/grub/menu.lst
```

Then input this at the end of the file, where you see the option for 'Ubuntu some-random-kernel-stuff' and a failsafe and memtest:

```
title		Microsoft Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1
```
You can change the title to whatever you wish. That's your call. I'm just listing what's in my menu.lst file.

Hope this helps. :)

I copy and pasted your stuff. When I hit esc and pick windows it tells me "error 12:invalid device requested.

I did install windows. Then I used partion magic to split it in 2. Then I went to install linux. I deleted the unused 2nd partiation so I could make a swap file, a ext3 (my main for linux) and a shared partion fat32. In that order I think. I have a STAT hard drive in my laptop if that matters with the hd0,0 thing

Heres what I have
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
# kopt=root=UUID=1bf49648-875d-44f9-83d4-0a57115012e8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1bf49648-875d-44f9-83d4-0a57115012e8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1bf49648-875d-44f9-83d4-0a57115012e8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by StarThorn1 on 2008-03-03
i seemed to have hit a nerve. I tried (hd0,1)  and I got a new error. NTLDR is missing. Dunno what this means though

---

### Post by StarThorn1 on 2008-03-04
bump

---

### Post by MeURi on 2008-03-04
NTLDR is the Windows loader - see it as GRUB for Windows (quick'n'dirty explanation :-P)

So you have two possible issues: either your Windows installation got corrupted, or you specified a partition which doesn't contain NTLDR - likely to be the latter, if you changed your hd(0,x) at random

The first thing is to figure out exactly how your partition table looks like. From console launch *parted* using *sudo*, and print your partition table - my output is as follows:
```

[m3ur1@Daemia: ~]$ sudo parted
[sudo] password for m3ur1:
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print all                                                        

Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  236GB  236GB   primary  ntfs         boot 
 3      236GB   249GB  12.9GB  primary  ext3              
 4      249GB   250GB  938MB   primary  linux-swap

```

So my */boot/grub/menu.lst* is as follows:
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=39e390ee-39e4-41fc-914d-adba8414d3f7 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

# Other entries for failsafe session and memtest

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
chainloader     +1

```

As you see, GRUB's numbers are the ones from the partition table, decremented by 1.
If you had a clean install of Windows on your hard disk, then partitioned it and installed Ubuntu (on a logical partition, as I guess from the numbers of your *menu.lst*, you are likely to have Windows on your hd(0,0) partition...

Tell us how your partition table looks like, using parted as I said above, and then we'll see what we can do to help :-)

---

### Post by StarThorn1 on 2008-03-04
[sudo] password for brandon:
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)                                                                  
(parted) print all                                                        

Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  40.0GB  40.0GB  extended                    
 5      64.5kB  33.0GB  33.0GB  logical   ext3              
 6      33.0GB  35.0GB  1999MB  logical   linux-swap        
 7      35.0GB  40.0GB  5009MB  logical   fat32             
 2      40.0GB  80.0GB  40.0GB  primary   ntfs         boot 



Disk /dev/sdb: 257MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      50.7kB  257MB  257MB  primary  fat16            





PS I posted my menu.lst back one page.

---

### Post by MeURi on 2008-03-04
Ok, so it's correct to have hd(0,1) as Windows root, as you said earlier in your post.

Since that causes the "NTLDR is missing" problem, this could be due to some partition move-create-delete operation you did prior to install Ubuntu

I remember creating a primary partition *before* the linux ext3 for backup purpose, which made my linux partitions get a +1 in their numbering, and then deleting it: well, the partition numbering is still with that +1, even if I had no partition 2 :-)

Maybe it's your situation, too - but 'reversed': I could not boot Ubuntu, you can't boot Windows.

I actually had never Windows main partition on partition numbers greater than 1, so I may be wrong, yet *my* general path to recover Windows boot errors is:
[LIST]
[*]boot from Windows setup cd
[*]skip every attempt to automatically recover a previous installation
[*]access to the repair console (maybe it has a slightly different name, since I'm italian and I'm translating 'on the fly' from what I remember :-P)
[*]from the console (you may need to 'login' as Administrator) input *fixboot* and, as a separate command,  *fixmbr*
[*][cross your fingers and] reboot :-)
[/LIST]

Those two commands give you a warning about making the partition table unreadable, and to proceed only if you know what you're doing. I have *never* had such disasters, but it could be related to my partition numbering (I know it's not a kind of magic, but I'm warning you :-)); actually, I advise you not to try unless you have a backup, just in case something goes wrong

Assuming everything goes well, when you reboot you'll get only Windows booting... so have your Ubuntu setup cd at hand; then follow the second post of this thread [thread]24113[/thread], using your partitions layout from the *parted* output (run it again after the *fixboot* and *fixmbr* procedure, just to be sure you don't mess up ;-))

Prior to the final reboot, check your */boot/grub/menu.lst* to see if it needs some corrections - e.g. the Windows boot section, or some erroneous numbers for partitions

After that, you should be capable of dual booting happily :-D

---

### Post by StarThorn1 on 2008-03-04
ok...This has a lot of steps. Its a work laptop and I got them to make an image of my windows before I tried linux. If all fails I will have to get them to image it. My linux experience is over if I cant make it boot to windows.

...now to find a windows CD.

---

### Post by GnomicGhost on 2008-03-04
You can obviously get into Linux ok since you're editing the grub file.
Let's try something before I have my guess of what you've done.

Log in to your main account on linux and go to;
Places > Computer.
When that window comes up, can you see your XP partition in the list on the left hand side?  If so, can you click on it and get into it to browse the files on your XP partition?

---

### Post by MeURi on 2008-03-04
@ StarThorn1:
> My linux experience is over if I cant make it boot to windows
Messing with partitions is always a delicate task, and the fact that actually windows tries to boot, but fails, tells you that the problem is not with linux itself ;-)

@ GnomicGhost:
Simple things, first. You're right :-)

---

### Post by StarThorn1 on 2008-03-04
I checked out computer places...and no I cant. I see 2 things.  one said back up and the other file system. Im going to try booting from the windows cd

---

### Post by StarThorn1 on 2008-03-04
Im in the windows repair console now. it said C and I typed dir. It showed me linux files.

do i still want to fixboot and all that?

---

### Post by StarThorn1 on 2008-03-04
lol after I fixmbr and rebooted I cant log in at all. It just tells me missing NTLDR and to restart by pressing crtl alt del

I know where this file is on the disk. When I try to copy it it said Access Denied. When I type LOGON I cant log on as an admin. nothing happens.

---

### Post by MeURi on 2008-03-04
Hmm

I assume you still can boot into Ubuntu, since you post :-)

The *back up* you see in *Places>Computer* is the label of which partition?
Did you specify a mount point for the Windows NTFS partition?

---

### Post by StarThorn1 on 2008-03-04
No. I have another PC in front of me. I cant boot on my laptop.

---

### Post by StarThorn1 on 2008-03-04
so am I totally screwed now?

---

### Post by MeURi on 2008-03-04
Oh, ok.

Well, you have to repair GRUB installation, as I said before (see [thread]24113[/thread])

After that you will be able to boot again into Ubuntu. The next step is to see if you can read your Windows files - see [this page](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot) for reference

From that point on, you should see your Windows partition label in the left pane of Nautilus - if the partition has no label you should see the name of the directory you mount in (correct me if I am wrong)

If you can see your Windows files, there is something gone bad with your NTLDR (it should be somewhere and it's somewhere else - speaking of disk sectors, not directories ;-)), but the only way I was able to repair it, it's following the steps I mentioned ealrier in this thread :-(

If you can't see your Windows files, yes, you're screwed :-(

---

### Post by StarThorn1 on 2008-03-04
ok I just pressed manual partion. I see this

/dev/sda
     /dev/sda5 Ext3 /media/sda5
    /dev/sda6 swap
    /dev/sda7 fat32 /media/sda7
    /dev/sda2 ntfs /media/sda2

I dont know which mounting points to use

---

### Post by MeURi on 2008-03-04
If you chose manual partition, it seems you are reinstalling Ubuntu - if you just need to restore GRUB (as you have to, since you fixmbr'ed from Win repair console), follow the second post on the thread 24113, it's quicker

Anyway, if you manually repartition, and you intend to do a clean install of Ubuntu, you partitioning scheme has to be changed a bit:
```

/dev/sda5 Ext3 /media/sda5  <-- this have to be '/'
/dev/sda6 swap
/dev/sda7 fat32 /media/sda7 <-- it's more intuitive if you use '/media/shared', here
/dev/sda2 ntfs /media/sda2  <-- it's more intuitive if you use '/media/windows', here

```
All my suggestions have to be used without quotes ;-)

If you choose the Ubuntu setup (note that reinstalling Ubuntu will probably erase your previous installation), at reboot you'll have your NTFS partition mounted in */media/windows*, and you should see it in the Nautilus sidebar: browse it and see if it shows your Windows files

If you choose to just repair GRUB, then, once rebooted, you have to do, from terminal:
```

$ cd /media
$ sudo mkdir windows
$ sudo mount /dev/sda2 /media/windows

```
The code above will mount your Windows partition in the directory just created, but *for this session only* (to have it mounted automatically, see the page on the wiki I linked before on this thread). Once you're done with mounting, you should be able to browse the content of folder /media/windows from Nautilus

Once again, you *should* see your files

---

### Post by StarThorn1 on 2008-03-04
Ill repair.

I dont know how to do the 2nd post

1. Pop in the Live CD, boot from it until you reach the desktop. (**check**)
2. Open a terminal window or switch to a tty. (**huh? whats tty**)
3. Type "grub" (**I could do this**)
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub). (**I dont know how mines set up**)
5. Type "setup (hd0)", ot whatever your harddisk nr is. (**Whats mine?**)
6. Quit grub by typing "quit".(**I could do that**)
7. Reboot.(**I could do that**)

---

### Post by StarThorn1 on 2008-03-04
Bump

---

### Post by MeURi on 2008-03-04
I had dinner in the meantime :-P

I assume you opened a terminal and typed in *grub* - actually I'd rather do *sudo grub*, to be sure grub does everything he needs without bumping on some missing priviledges (I actually dunno if I'm right)

The command *root hd(x,y)* tell GRUB where to find your kernel(s). Some users keep their /boot on a separate partition; according to your partition table, you're not the case, which means you have your /boot in the main partition. Your code should then be:
```
grub> root hd(0,4)
```
assuming *grub>* is the GRUB prompt (still on Windows, too lazy to check :-P)

The command *setup hd(0)* instructs GRUB to install itself on the MBR of the hard disk, thus replacing Windows bootloader. From your old menu.lst, *hd(0)* is correct for you :-)

Next two steps are simple, as you noted before

---

### Post by StarThorn1 on 2008-03-04
Sweet I did what you said with the grub and i can boot into linux now. I cant see windows stuff yet but im going into terminal and

$ cd /media
$ sudo mkdir windows
$ sudo mount /dev/sda2 /media/windows

---

### Post by StarThorn1 on 2008-03-04
I typed in /media/windows in the location/address bar. It brought me to a folder with QGRUBEditor and system Volume information in it. It sys volume, I see 2 files. One called MountPoint ManagerRemote Database and the other tracking.log.

so it didnt bring me to windows. I think i might be doomed

---

### Post by MeURi on 2008-03-04
Bad news... you actually wiped something, but don't know exactly when you could have done that.

I think during partitioning - IMHO is not very clear for an unexperienced user, especially the mountpoint thing (don't want to start a flame, just thinking about the user who tries to install Ubuntu coming from Windows, with no experience and no non-windows culture :-))

Said that, and also *sad that* (horrible pun, i know :-D), you have to reinstall Windows, either performing a clean install on that NTFS partition, leaving other partitions untouched, or using the backup image you made

In the former case, you will have to rerun the GRUB repair process (Windows installs its bootloader in the MBR, always); in the latter, you will have to do a clean Ubuntu install

In the latter case, I suggest you to partition the hard disk pace from Windows, using some tools like Partition Magic*, keeping your Windows partition in the first place (number 1) (it's my kind of magic for troubleshooting :-P). A layout similar to yours could be:
[LIST]
[*]Windows main partition, NTFS [takes number 1]
[*]Extended partition [actually invisible, takes number 2]
[*]Shared FAT32 partition, FAT32 [takes number 5]
[*]Ubuntu main partition, EXT3 [takes number 6]
[*]swap partition, SWAP [takes number 7]
[/LIST]

During the following Ubuntu setup, use manual partition configuration, and specify the NTFS partition to be mounted as, let's say, /media/windows; your FAT32 to be mounted as /media/shared; your EXT3 to be mounted as / (probably the setup will reformat it); your SWAP partition, if you choose swap, should be disabled for mounting (could be reformatted by setup, too). Do NOT reformat the NTFS partition ;-)

After setup completes, reboot, and you should be able to boot Ubuntu, Windows, and to see Windows mounts from Nautilus

* I know about Acronis Disk Director, also; both are commercial. Maybe a trial version will suffice. If there are any free tools which support perfect NTFS partition managing, you can use them, I actually don't know any (here again, no flame, I know those two).

---

### Post by StarThorn1 on 2008-03-04
Its not me who has to image it. Its desktop support. I wont be trying this again on a work PC because I dont want to bug him.

When my hard drive ships for my home pc I will do a vista/ubuntu boot. There are some manuals online I saw. Thanks for all the help!

---

### Post by MeURi on 2008-03-04
Ok, then. Good dual boot at home :-)

And glad of being of some help

PS: won't you increment my thanks counter? :-D (I don't know how to thank someone, though, I'm a forum newbie :oops:) Just jokin'... :-)

---

