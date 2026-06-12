---
title: "Read Only"
date: 2007-08-25
forum: General Help
---

### Post by ewloe on 2007-08-25
Sorry if this has been asked before I have searched but can't find anything relative.

I have tried Ubuntu running it from the CD and I like it, managed to get internet connection and most things working, the only problem I found (so far) is that when trying to save files etc it says my drives are READ ONLY, is this because I am running from the CD or is it something that will still need fixing when I go for the full install.

I am currently running (reluctantly) XP but I want to get rid of all Microsoft products if at all possible.

---

### Post by pizzutz on 2007-08-25
It's because windows drives are formatted NTFS which is a propriatary file system.  We have pretty much figured out how to read and write to them safely, but the default installation makes them read-only for absolute safety.  If you would like, you can give me the output of the following command from the terminal, and I can give you a set of commands for making them read-write with the live CD. This will of course only work till you reboot.  Once you have installed, at least a partition of your HD will be formatted ext3 and be automatically writeable, and if you dual boot, there are permanent ways of mounting the windows partition read-write.

```
sudo mount
```

---

### Post by ewloe on 2007-08-26
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdb6 on /media/Dump type ntfs (rw,nosuid,nodev,umask=222,utf8)
ubuntu@ubuntu:~$

---

### Post by merlinus on 2007-08-26
Once you install, you can get the drivers that will allow you to write to ntfs-formatted partitions.

-merlin

---

### Post by ewloe on 2007-08-26
Thank You

I am preparing for installation now

---

### Post by ewloe on 2007-08-26
I have now installed ubuntu and I have tried following some of the advice on here for installing ntfs-3g but its not working for me. I am not using duel boot so I only need to access the files from ubuntu. 

Can someone please tell me what to do in plain english? 

thank you

---

### Post by merlinus on 2007-08-26
Enter these commands in a terminal (Appiications/Accessories):

```

sudo apt-get install ntfs-config

```

then

```

sudo ntfs-config

```Tick the appropriate boxes and restart.

-merlin

---

### Post by ewloe on 2007-08-26
did as you said merlin and this is what I got

ewloe@top:~$ sudo apt-get install ntfs-config
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  ntfs-config: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages
ewloe@top:~$ sudo ntfs-config
sudo: ntfs-config: command not found
ewloe@top:~$ 


thanks

---

### Post by merlinus on 2007-08-26
What version of ubuntu are you using?

-merlin

---

### Post by ewloe on 2007-08-26
Feisty Fawn 7.04

---

### Post by merlinus on 2007-08-26
Try searching for ntfs-3g in Applications/Add Remove, and make sure Show: All Available Applications is selected in the upper right dropdown menu.

-merlin

---

### Post by ewloe on 2007-08-26
This application conflicts with other installed software. To install 'ntfs-config' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

---

### Post by ewloe on 2007-08-27
ntfs-config:
 Depends: libdbus-1-2 (>=0.60) but it is not installable

---

### Post by gary0 on 2007-08-27
Immediately after you install ubuntu, go to the terminal and type:

sudo apt-get update

you will be asked for your password, you won't see anything as you type, but it is there so don't worry.

This will update your apt sources.
Then again in terminal type:

sudo apt-get upgrade

This will update all your packages.

Then type:

sudo apt-get install ntfs-3g

which will install ntfs-3g.

Go into your media directory and create a directory call D_drive, or Data or whatever.

sudo gedit /etc/fstab

will open a text editor with your fstab file. add this line right at the end:

/dev/hda5	/media/Data	ntfs-3g	defaults,locale=en_gb.utf8	0	0

replacing Data with whatever you called your new dir in /media.

Reboot, and away you go.

HTH

Gary.

---

### Post by ewloe on 2007-08-28
Go into your media directory and create a directory call D_drive, or Data or whatever.

I can't create any directories its grayed out everything was working uptil that point

---

### Post by gary0 on 2007-08-28
Ok, at the terminal type:

cd /media

sudo mkdir Data

and continue from there.

Gary.

BTW, /dev/hda5 is the second partition on your C: drive in windows.

---

### Post by ewloe on 2007-08-29
everything seems to work fine but still only reading access

I think maybe the problem lies at this stage

sudo gedit /etc/fstab as I may have altered it to many times while trying, here is what I get

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d7146bba-a784-4176-a974-60ab06461c6c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=936e93c4-d8db-4135-a9b6-abf2c2cd58d9 none            swap    sw              0       0
/dev/hda5 /media/Data ntfs-3g defaults,locale=en_gb.utf8 0 0

if this is what should be there then i don't know where it could be going wrong.

 I will have to try partitioning and reformatting and moving stuff around, I have two empty partitons at the moment one 6gig and one 20gig but I need to move 70gig worth of stuff but I have 50gig free on the drive thaty contains the 70gigs so with moving 20 gig over and then partitionong that drive and copying the other 50gig I can then format the rest of the drive and have it all free but this seems a lengthy process and I would also have to dowload a bootable parttiton manager to do it, any recommendations?

thanks for help so far
cheers

---

### Post by gary0 on 2007-08-29
This is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=84288cf9-0346-4167-81f6-007f9d94c918 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=202332e2-704a-4a14-b892-adbfbd6593e0 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/Windows	ntfs-3g	defaults,locale=en_gb.utf8	0	0
/dev/hda5	/media/Data	ntfs-3g	defaults,locale=en_gb.utf8	0	0

The only difference I can see is that you have this identifier for hda5:

# /dev/hda5
UUID=936e93c4-d8db-4135-a9b6-abf2c2cd58d9 none swap sw 0 0

Back up your fstab file and try removing those lines, and then reboot.

I'm no expert on this, but to get it to work i followed this tutorial:

Quote

sudo apt-get install ntfs-3g

    * Read #How to list partition tables 

    * Create the local mount folder and edit the fstab file to mount the disks to this folder. 

    e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS) 
    Local mount folder: /media/windows 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

    * Append the following line at the end of file. 

/dev/hda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0

    * You can adjust your locale. Execute 'locale -a' in a terminal to know which one are supported by your system. 

    * Save the edited file. 

    * If you reboot now, the disk will be writable to every users. If you want the changes to take effect immediately without rebooting, execute the following command, ignoring the errors about "/" and others not being unmounted. 

sudo umount -a && sudo mount -a

Unquote

HTH

Gary.

---

### Post by ewloe on 2007-08-29
thanks gary but still no joy, I think I will reinstall from freash tomorrow and try your advice from the start, if that don't work then its copying files around and partitioning until I have access to all.

don't know if this makes a difference but I am not using duel boot I only use ubuntu now

---

### Post by ewloe on 2007-08-30
I have given up hope with being able to read the ntfs system I have now download gparted and used it to reformat two of my drives but I still can not write to them, I have tried both ext3 and fat32, am I missing something?

---

