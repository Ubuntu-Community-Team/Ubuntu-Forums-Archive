---
title: "Booting problems"
date: 2007-05-04
forum: General Help
---

### Post by lauragee on 2007-05-04
[SIZE="7"][/SIZE]Hi,
i'm new to Ubuntu Linux and i'm having problems after installing it so i do hope someone can answer my question.
at the moment i am an XP user and i installed Ubunto onto a seperate drive that is connected to the mother board via an IDE controller card. After installing Ubunto i fully expected to be confronted by a dual boot option on startup but insteat my system booted right into windows xp.
Thinking that it was my bios boot option i rebooted into my bios and made the drive with Ubunto on it the main boot device and rebooted yet again only to get a blank screen with the cursor flashing in the top left corner.
i'm pretty sure that Ubuntu installed properly and that i followed the correct procedure. i also had no errors reported.
Does anyone have any ideas please.
LG

---

### Post by m.musashi on 2007-05-04
If you have two drives (HD0 and HD1) and you installed ubuntu to HD1, the problem could be the location of GRUB. If your BIOS is set to HD0, does XP load with no boot menu? If so, I'm going to guess that GRUB is on HD1. If you then make HD1 your first boot drive (which will cause it to become HD0) then it still won't boot because the files it is looking for are on HD1. You will need to boot the live CD and then edit GRUB.

If this seems to be the case, let us know and we can explain how to fix it. If I'm way off base then just ignore me :).

---

### Post by phidia on 2007-05-04
I would also add that when you boot from the livecd open a terminal and type fdisk -l <enter> to see how ubuntu is seeing your drives.From there using the terminal and  sudo gedit or vim you can edit /boot/grub/menu.lst to make your install compatible with bios boot order.

---

### Post by lauragee on 2007-05-04
Hi again,
i have to tell you that i'm a little bit lost and confused. Remember, this is my first experience with Linux **smile**.
Just what is GRUB.
In the meantime i shall boot on the CD and fiddle about with both your sugestions .

LG

---

### Post by confused57 on 2007-05-04
Here's some excellent info on grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Boot the live cd, open a terminal(Applications--Accessories--Terminal), copy & paste:
```
sudo fdisk -l
```
the -l is a small "L"

This will show your partition tables on both your hard drives.

Once you determine which is your Ubuntu root partition, you can mount it using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
after mounting it(see instructions in the link), you can access your /boot/grub/menu.lst.

You might want to post the output of:
```
sudo grub
find /boot/grub/stage1
quit
```

Added:  You might want to download a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it should be able to boot your Ubuntu drive...it's only a few Mb download

---

### Post by m.musashi on 2007-05-04
Oops, sorry. It's hard to know sometimes a persons level of knowledge.

GRUB is the thing that will allow you to dual-boot. It will install a menu that opens at boot and allows you to choose between XP and Ubuntu (and any other OS you want to install).

We need to figure out why GRUB is not loading at boot and fix it. It's not hard. From the live CD there is an easy couple steps that will fix it in many cases. Let me do some searching and I'll post a link.

EDIT: Okay, check [this link](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) for the steps to recover GRUB. And here is [some good info on GRUB in general](https://help.ubuntu.com/community/GrubHowto)

ANOTHER EDIT: [Here](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) is another similar page with a bit more info[/url]

---

### Post by lauragee on 2007-05-04
well i managed to do the fdisk thing and below is a cut/paste of what came up on all my drives.
i also did a "grub-install hdh" which, looking at the printout, is when my linux is installed. This is my smallest drive and not surprising, i got an error and i don't have permission.
Hope someone can give me a solution. 
BTW, i'm working from the livecd even to post this note thru firefox on the cd.

Begin paste..........

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1        8414    67585423+   7  HPFS/NTFS
/dev/hde2            8415       16708    66621555    f  W95 Ext'd (LBA)
/dev/hde5            8415       16708    66621523+   7  HPFS/NTFS
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/hdg: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1        3356    26957038+   7  HPFS/NTFS
/dev/hdg2            3357        6543    25599577+   7  HPFS/NTFS
/dev/hdg3            6544        9729    25591545    f  W95 Ext'd (LBA)
/dev/hdg5            6544        9729    25591513+   7  HPFS/NTFS
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/hdh: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1   *           1        2388    19181578+  83  Linux
/dev/hdh2            2389        2498      883575    5  Extended
/dev/hdh5            2650      260269  2069331968   ff  BBT

Disk /dev/sda: 320.0 GB, 320072933376 bytes
102 heads, 51 sectors/track, 120173 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60104   156330472+   7  HPFS/NTFS
/dev/sda2           60104      120173   156239463    f  W95 Ext'd (LBA)
/dev/sda5           60105      120173   156239437+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
37 heads, 15 sectors/track, 1126382 cylinders
Units = cylinders of 555 * 512 = 284160 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      563031   156241095    7  HPFS/NTFS
/dev/sdb2          563032     1126382   156329902+   5  Extended
/dev/sdb5          563032     1126382   156329891+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7267    58372146    7  HPFS/NTFS
/dev/sdc2            7268       14593    58846095    5  Extended
/dev/sdc5            7268       14593    58846063+   7  HPFS/NTFS

end paste.....

LG

---

### Post by confused57 on 2007-05-04
You can use the live cd to install grub to your Ubuntu drive mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

It would be something like this:
```
sudo grub
find /boot/grub/stage1
```
this should return your root partition, e.g. "root (hdx,0)"
you would then enter:
```
root (hdx,0)
setup (hdx)
quit
```

substitute "x" for whatever the first command results are.

Then boot first to your Ubuntu drive, you should get a grub menu, highlight your Ubuntu entry, press "e", then change the line with root from (hdx,y) to (hd0,y), then press "b" to boot...if this works, it's only temporary, but it can be made permanent in your /boot/grub/menu.lst.

---

### Post by lauragee on 2007-05-04
hi again,
i did as you suggested (and and the site of the link you sent....thank you ) and below is the output.

begin paste......

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub> find/boot/grub/stage1

Error 27: Unrecognized command

grub> find /boot/grub/stage1

Error 15: File not found

grub> 

end paste...

so right now i have no idea what to do.

LG

---

### Post by m.musashi on 2007-05-04
Are you doing this from a live CD? If so, you will probably have to mount the partiton that has Linux. From your fdisk -l above it looks like hdh1. Is that correct? If so, you can mount it like this:
```
sudo mkdir /mnt/feisty
sudo mount /dev/hdh1 /mnt/feisty
```
Then try the above grub commands.

You have a lot of drives it looks like. GRUB will need to be on the drive that boots. In my experience, it gets a bit confusing if it boots one drive and then has to "go" somewhere else. I'm not sure if the steps above will fix it if things are on different drives. I think it will but I don't have a lot of experience with that setup.

---

### Post by lauragee on 2007-05-04
so am i right in assuming that i insert ubuntu in place of Feisy given that i have installed the ubuntu version of linux.

LG

---

### Post by confused57 on 2007-05-04
m. musashi is right, you can try mounting your Ubuntu partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

You would need to do something like this, using the above link:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdh1 /media/ubuntu
```

then you can access these configuration files:
```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```
and
```
gksudo gedit /media/ubuntu/boot/grub/device.map
```

I would still recommend you try the Super Grub Disk.

---

### Post by lauragee on 2007-05-04
i'm getting the following error after just the second line of code input in your last post.


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

begin paste ...
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdh1 /media/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/hdh1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ 

End paste ....

LG

LG

---

### Post by lauragee on 2007-05-04
i'm also getting this printout when i try what is sugested.

begin ...
ubuntu@ubuntu:~$ syslog
bash: syslog: command not found
ubuntu@ubuntu:~$ dmesg | tail 
[  208.807027] Bluetooth: L2CAP ver 2.8
[  208.807033] Bluetooth: L2CAP socket layer initialized
[  209.384390] Bluetooth: RFCOMM socket layer initialized
[  209.384404] Bluetooth: RFCOMM TTY layer initialized
[  209.384406] Bluetooth: RFCOMM ver 1.8
[  238.710837] hdf: DMA timeout retry
[  240.790786] PDC202XX: Primary channel reset.
[  242.870729] PDC202XX: Secondary channel reset.
[  242.871121] hdf: timeout waiting for DMA
[  661.825376] VFS: Can't find ext3 filesystem on dev hdh1.
ubuntu@ubuntu:~$ 

end....

LG

---

### Post by confused57 on 2007-05-04
You might want to download and burn a copy of the gparted live cd(45 Mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

The gparted live cd is an excellent partitioning tool and it'll give you more information about your partition filesystems and enable you to do a filesystem check:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
this link explains how to use the gparted live cd to do a filesystem check and what to do if you have a bad superblock.

Another idea is to set your hdh drive as the first hard drive in your bios hard drive boot sequence and reinstall Ubuntu...when grub is installed, this drive "should" be recognized as (hd0) and install grub to it's mbr...just to make sure, you could type in "/dev/hdh"(if that is how the drive is designated when you install) as the location to install grub to.

Added:  Grub may have been installed to the mbr of one of your other hard drives, you could always try booting first to each of them, in turn,  to see if you can get the grub menu.

---

### Post by m.musashi on 2007-05-04
@confused57. I'm going to stay out of this one for a while. I'm getting confused as to who has what drive set up and such.

---

### Post by confused57 on 2007-05-04
> **m.musashi said:**
> @confused57. I'm going to stay out of this one for a while. I'm getting confused as to who has what drive set up and such.

Check back in occasionally, with all these hard drives & error messages, it's a little more complicated than my expertise can handle...you'll probably see a possible solution that I'm not aware of or haven't thought of, I respect your knowledge & always welcome your input.  I agree, helping 2 different people in 2 threads gets a little "confusing" for me and for the OP.

---

### Post by m.musashi on 2007-05-04
> **confused57 said:**
> Check back in occasionally, with all these hard drives & error messages, it's a little more complicated than my expertise can handle...you'll probably see a possible solution that I'm not aware of or haven't thought of, I respect your knowledge & always welcome your input.  I agree, helping 2 different people in 2 threads gets a little "confusing" for me and for the OP.

Thanks for the vote of confidence but I'm not much of an expert. I've just fried grub (and my install in general) so many times I got pretty good at these. Not always for sure but pretty good.

I'll review this thread it a bit and see where things stand and what is actually going on.

---

### Post by m.musashi on 2007-05-04
Okay, I've looked this over and to be honest there are a lot of possible problems/solutions here and I'm not sure where to start.

Based on the fact that you can't mount the file system in question suggests that there could be more or different problems besides GRUB. Lets collect a little info and see if we can map out a solution. Also, all the drives you seem to have is going to make this confusing. What drive do you normally boot from?

Boot the live CD and then open a terminal. type
```
mount
```
You don't need sudo for this. Copy and paste the output. Basically, it will tell us what the file system type is for each of the drives. We are most interested in hdh as I think this is your Ubuntu drive. Correct me if I'm wrong.

Also, you can try mounting the partition like this
```
sudo mkdir /media/feisty
sudo mount /dev/hdh1 /media/feisty
```
The feisty part is just a name to use. It could be anything you like. This is just an easy way to keep track. I'm suggesting to leave out the -t ext3 bit because it will usually mount a linux partition without being told what it is (I don't know if this works with other file system types because I've only used ext3 but with Ubuntu this works fine). If this doesn't work, then I'm willing to bet you have some drive problems. Let us know how this goes and we can go from there.

---

### Post by lauragee on 2007-05-05
well i have tried pretty much everything previously sugested and i have reinstalled ubuntu probably 8-9 times.
i'm at the point right now where i have made the drive that i am installing linux on my primary boot drive, rebooted with the live CD and reinstalled once again. Ubuntu installed with no errors and on reboot,the system just sits there with a black screen and a cursor flashing in the top left corner.
i'll keep stumbling along looking for answers altho i feel i'm pretty much at a loss what to do now.Thanks for all your help tho.

LG

Added.
i even got to enter all my email info and set up my email during the install so i AM making some progress lol

---

### Post by lauragee on 2007-05-05
> **m.musashi said:**
> Okay, I've looked this over and to be honest there are a lot of possible problems/solutions here and I'm not sure where to start.

Based on the fact that you can't mount the file system in question suggests that there could be more or different problems besides GRUB. Lets collect a little info and see if we can map out a solution. Also, all the drives you seem to have is going to make this confusing. What drive do you normally boot from?

Boot the live CD and then open a terminal. type
```
mount
```
You don't need sudo for this. Copy and paste the output. Basically, it will tell us what the file system type is for each of the drives. We are most interested in hdh as I think this is your Ubuntu drive. Correct me if I'm wrong.

Also, you can try mounting the partition like this
```
sudo mkdir /media/feisty
sudo mount /dev/hdh1 /media/feisty
```
The feisty part is just a name to use. It could be anything you like. This is just an easy way to keep track. I'm suggesting to leave out the -t ext3 bit because it will usually mount a linux partition without being told what it is (I don't know if this works with other file system types because I've only used ext3 but with Ubuntu this works fine). If this doesn't work, then I'm willing to bet you have some drive problems. Let us know how this goes and we can go from there.

 your correct in thinking that my linux drive is hdh1.
Also i tried what you sugested over mounting my drive (hdh1) and below id the error......it seems to be expecting the item you said to leave out...ie. -t ext3....but i'm not sure where to place this command.

begin paste.....

ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount /dev/hdh1 /media/ubuntu
mount: you must specify the filesystem type

end paste...

LG

also

begin paste......

 sudo mkdir /media/ubuntu
mkdir: cannot create directory `/media/ubuntu': File exists
ubuntu@ubuntu:~$ sudo mount /dev/hdh1/-t ext3 /media/ubuntu
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

End paste....

so i'm unsure what commands to use.
Sorry for being a PITA lol

---

### Post by confused57 on 2007-05-05
Since you've reinstalled Ubuntu, have you retried mounting the way I mentioned in reply #12.

---

### Post by lauragee on 2007-05-05
yes i did.
i only have one more option left that i can come up with and thats to disconnecct all but my main drive and the drive that i intend putting linux onto. 
i shall leave them both connected to their original connectors and see what happens.

LG

Ok.....after disconnecting all my drives 'cept 2, i rebooted using the CD and was able to do the first thing you sugested...ie. 
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdh1 /media/ubuntu
ubuntu@ubuntu:~$ gksudo gedit /media/ubuntu/boot/grub/menu.lst

and i got a seperate window with that list but i wasn't able to do the mapping.
What do i do with the list info.

LG

Adding
Well now i am going to try and install on one of my main drives. i have emptied a SATA drive which is on the main SATA bus on the motherboard. If this fails then i'm at a TOTAL loss as to what to do.
BTW, my main XP boot drive is on an IDE buss directly on the mother board.

LG

---

### Post by lauragee on 2007-05-05
Well everyone....thanks for the help, those who tried to help anyway, but i'm all out of idea's on how i can get this thing installed. As much as i'd LOVE to use linux instead of microsoft i just can't seem to get it to work.
i have done pretty much everything that has been sugested in this thread as well as a lot of my own ideas like disconecting all my devices 'cept for my Xp drive and a blank reformated SATA drive.
Other than striping my system down to just one drive and just trying that then i have no more ideas. i need Xp on my system if for nothing else than the transition over to linux so i dunno what else to say.......'cept bill gates has won out again lol.
Thanks all tho.

LG

---

### Post by confused57 on 2007-05-05
> **lauragee said:**
> Well everyone....thanks for the help, those who tried to help anyway, but i'm all out of idea's on how i can get this thing installed. As much as i'd LOVE to use linux instead of microsoft i just can't seem to get it to work.
i have done pretty much everything that has been sugested in this thread as well as a lot of my own ideas like disconecting all my devices 'cept for my Xp drive and a blank reformated SATA drive.
Other than striping my system down to just one drive and just trying that then i have no more ideas. i need Xp on my system if for nothing else than the transition over to linux so i dunno what else to say.......'cept bill gates has won out again lol.
Thanks all tho.

LG
Sorry it didn't work out, looks like you tried everything you could...it may be something with your hardware, possibly your mobo hard drive controllers?   Probably not the problem and know you're getting very frustrated with all your attempts, but you might try redownloading another iso and burning another cd(at a low speed, 8x or less)...I really don't know what's going on.

---

### Post by lauragee on 2007-05-05
thanks again......i may do as you suggest and DL the iso again but i need to give it a rest after working on it for 2 days str8 pretty much **smile**.
i DL Ubuntu 7.04, i think thats the latest ver tho i'm not too sure.
Is that ver stable? Is there a previous ver thats more stable?
i tried installing Ubuntu ver 6.xx about 6 months ago with even more disastrous results and i recently updated all my hardware, mother board, drives, memory, dual core processor etc so i'm hoping your wrong about my hardware lol.i'm putting it down to a learning experience :-).

LG

---

### Post by confused57 on 2007-05-05
> **lauragee said:**
> thanks again......i may do as you suggest and DL the iso again but i need to give it a rest after working on it for 2 days str8 pretty much **smile**.
i DL Ubuntu 7.04, i think thats the latest ver tho i'm not too sure.
Is that ver stable? Is there a previous ver thats more stable?
i tried installing Ubuntu ver 6.xx about 6 months ago with even more disastrous results and i recently updated all my hardware, mother board, drives, memory, dual core processor etc so i'm hoping your wrong about my hardware lol.i'm putting it down to a learning experience :-).

LG
Feisty is probably the best version for the newest hardware & it's relatively stable.  I thought you might be a little "burnt out" and needed a break.  Hopefully, it's not a hardware issue, which it probably isn't.
When you make another attempt, you may want provide as much info as you can about your system when you post & I don't know if posting in the Hardware section of the forum would help or not.  Sorry you didn't get it working, maybe the next time will be a "charm"...good luck.

---

### Post by lauragee on 2007-05-05
> **confused57 said:**
> Feisty is probably the best version for the newest hardware & it's relatively stable.  I thought you might be a little "burnt out" and needed a break.  Hopefully, it's not a hardware issue, which it probably isn't.
When you make another attempt, you may want provide as much info as you can about your system when you post & I don't know if posting in the Hardware section of the forum would help or not.  Sorry you didn't get it working, maybe the next time will be a "charm"...good luck.


do you mean Ubuntu Linux "Feisty Fawn" Release as thats all i can find info on.

LG

---

### Post by confused57 on 2007-05-05
> **lauragee said:**
> do you mean Ubuntu Linux "Feisty Fawn" Release as thats all i can find info on.

LG
Yes, that's the one.  Another possibility for you blank screen when trying to boot Ubuntu...are you using a DVI connected LCD or possibly a PCIe video card?  If you are, this might be something to mention when you repost(if you're still having problems), I couldn't help you personally, but I'm sure there are plenty of other people who can.

---

### Post by m.musashi on 2007-05-06
Sorry I drop off the scene on this one. I had family here yesterday and never logged in once (very rare:)).

I'm not sure I can add much at this point but one thing you said got me thinking. At what point do you see the blank screen and flashing cursor? Is it before the grub menu (i.e. nothing happens after POST) or after some part of GRUB? Can you actually get to the menu and after you select an item you get the blank screen?

I have had problems in the past where peripherals attached via usb cause the system to freeze. If I remove them then it boots fine (although sometimes it takes two reboots before it will).

It's a long shot but I thought I'd mention it.

EDIT: oh, one more thing. I've never had to use the -t ext3 bit when mounting an Ubuntu drive. Certainly when mounting a windows drive but not one with Ubuntu. Anyway, if it cannot recognize the file system that does suggest a problem with the drive. I'm not sure I followed all that transpired the last day or so but what happened when you tried to install to a SATA drive? I know it wouldn't boot, but did you try the grub steps mentioned before from a live CD? Were you able to mount the drive or did the same problem appear?

Also, what are the details of the system? Did you build it? What mobo do you have and are we sure it's Linux friendly? I had a lot of problems with my mobo and 5.10. It wasn't until 6.06 (Dapper) that things finally worked "out of the box" as they say. If the board is really new that could be a factor. If it's older, you might need to check into a BIOS update.

---

