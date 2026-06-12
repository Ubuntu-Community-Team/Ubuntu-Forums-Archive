---
title: "GRUB error 17 - help needed"
date: 2007-04-24
forum: General Help
---

### Post by Buz_Light on 2007-04-24
I have dual boot on my laptop with win xp pro on one side and ubuntu feisty beta (still not updated to the official release... still testing feisty, i<m new to linux).

from xp, I tried to give more place to my ubuntu partition using partition magic 8 but I was not able to do so. NOTHING was changed by partition magic.
But when I rebooted to come back to feisty, I had a grub error 17 message and I<m not able to boot on nothing. I,m writting from the live CD.

Could someone help me try fixing this... Im totally lost right now...

---

### Post by srhlefty on 2007-04-24
from the live cd, can you access your partition with feisty on it?

---

### Post by Buz_Light on 2007-04-24
> **srhlefty said:**
> from the live cd, can you access your partition with feisty on it?

yes

in gnome GParted, /dev/sda6 contains my linux partition (ext3) and /dev/sda7 my swap partition

---

### Post by srhlefty on 2007-04-24
then I think it would work to reinstall grub.  The command is something like 

grub-install /dev/hda

But you may not want to trust me on this--I've never done it personally

---

### Post by Buz_Light on 2007-04-24
> **srhlefty said:**
> then I think it would work to reinstall grub.  The command is something like 

grub-install /dev/hda

But you may not want to trust me on this--I've never done it personally

Thanks for your help. Can someone confirm??

Would this do the job??

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

---

### Post by Herman on 2007-04-24
Yes,  'sudo grub-install /dev/sda' would do the job all right.  

The second method you described, re-installing Grub using a grub shell is good too, that's the method I prefer most of the time.

Either of those should work.

Regards, Herman :)

---

### Post by Herman on 2007-04-24
Here is what that error message may mean quoted from the Gnu/[GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html"), plus some of my own comments I added to that from the [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"),
> [COLOR=Red]17 : Cannot mount selected partition 
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.                                        [/COLOR]

Most commonly this is caused by using the 'root' command instead of 'rootnoverify' when booting Windows having the NTFS file system.
                                      Edit your commands in your menu.lst or grub.conf file with 'rootnoverify' to get rid of this error message.
                                      
                                      If you get this error when trying to boot Linux, check your grub conf. or menu.lst file and make sure to check your operating system entry's 'root (hdx,y)' details are correct.
                                      
                                      You can use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to boot Linux for you so that you can easily check and repair your operating system's entry in menu.lst. 
                                      Super Grub can boot your operating system by symlinks to the kernel if you use, from the Main Menu,--> Boot Gnu/Linux and  Other OSes --> Boot Gnu/Linux -->...
                                      
[COLOR=Red]                                       If you have used hard disk partitioning software recently and you have copied and pasted your partition that contains Grub, it probably has a different partition number now than it had before.[/COLOR] You can use Super Grub Disk to re-install Grub.[COLOR=Red] You will also need to edit /etc/fstab if your partition numbers have changed.[/COLOR] You should check with a [GParted LiveCD]("http://gparted.sourceforge.net/") to see if your partition numbers have changed. I wouldn't use Partition Magic anymore, that's commercial software and you won't need it anymore now that you have Open Source software. I recommend [GParted LiveCD.]("http://gparted.sourceforge.net/") instead, it's free and only a small download, (about 45 Mb). It's the most advanced partitioning software you can get nowadays and it is fully compatible with Ubuntu and other Open Source operating systems and Windows too.

You may need to edit your /boot/grub/menu.lst with the new partition numbers if Partition Magic changed them on you. If you need more help don't be shy to ask for more details.

Regards, Herman :)

---

### Post by strabes on 2007-04-24
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Buz_Light on 2007-04-25
I have been able to reinstall GRUB, which allowed me to boot in XP. However, I am still unable to boot in Ubuntu.

Following this guide : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         383     3076416   12  Compaq diagnostics
/dev/sda2   *         384        3234    22900657+   7  HPFS/NTFS
/dev/sda3            3235       12161    71706127+   f  W95 Ext'd (LBA)
/dev/sda5            3235        9423    49713111    7  HPFS/NTFS
/dev/sda6            9424       11646    17856216   83  Linux
/dev/sda7           11647       12161     4136706   82  Linux swap / Solaris

```

where sda2 is XP partition, sda5 is a NTFS data partition, sda6 is linux partition.
I was able to...

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda6 /mnt/root
ubuntu@ubuntu:~$ ls /mnt/root
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old
ubuntu@ubuntu:~$ ls /mnt/root/boot
abi-2.6.20-12-generic             initrd.img-2.6.20-14-generic.bak
abi-2.6.20-14-generic             initrd.img-2.6.20-15-generic
abi-2.6.20-15-generic             initrd.img-2.6.20-15-generic.bak
config-2.6.20-12-generic          memtest86+.bin
config-2.6.20-14-generic          System.map-2.6.20-12-generic
config-2.6.20-15-generic          System.map-2.6.20-14-generic
grub                              System.map-2.6.20-15-generic
initrd.img-2.6.20-12-generic      vmlinuz-2.6.20-12-generic
initrd.img-2.6.20-12-generic.bak  vmlinuz-2.6.20-14-generic
initrd.img-2.6.20-14-generic      vmlinuz-2.6.20-15-generic

```

now, I have to idea where to reinstall GRUB using
```
grub-install --root-directory=/mnt/root /dev/sda?
```????????????? My bet is on sda1 but i,m not certain.

Thanks

---

### Post by confused57 on 2007-04-25
You might want to post your menu.lst, using the live cd...mount it as before, then:

```
gedit /mnt/root/boot/grub/menu.lst
```

this may give us some idea of what's going on...also, you might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
the SGD should be able to boot your Ubuntu partition, as Herman has already suggested.

---

### Post by Buz_Light on 2007-04-25
> **confused57 said:**
> You might want to post your menu.lst, using the live cd...mount it as before, then:

```
gedit /mnt/root/boot/grub/menu.lst
```

this may give us some idea of what's going on...also, you might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
the SGD should be able to boot your Ubuntu partition

Right,

Here is the content of /mnt/root/boot/grub/menu.lst
```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=51ea6a0c-e932-4a7f-ae16-2e4ae04f8302 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=51ea6a0c-e932-4a7f-ae16-2e4ae04f8302 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.20-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=51ea6a0c-e932-4a7f-ae16-2e4ae04f8302 ro quiet splash
initrd		/boot/initrd.img-2.6.20-14-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=51ea6a0c-e932-4a7f-ae16-2e4ae04f8302 ro single
initrd		/boot/initrd.img-2.6.20-14-generic

title		Ubuntu, kernel 2.6.20-12-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=51ea6a0c-e932-4a7f-ae16-2e4ae04f8302 ro quiet splash
initrd		/boot/initrd.img-2.6.20-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-12-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=51ea6a0c-e932-4a7f-ae16-2e4ae04f8302 ro single
initrd		/boot/initrd.img-2.6.20-12-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professionnel
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Please refer to my last post above to have a better idea of what<s is going on.

Will give a try to the SuperGrubDisk next time I boot on XP. However, Iwould like to fix the problem from Ubuntu if possible. Any idea??

---

### Post by confused57 on 2007-04-25
What you can try is to boot your computer, in the grub menu, highlight your Ubuntu entry, press "e" to edit, then change root to (hd0,5), then press "b" to boot...this change is temporary, but it'll let you know if it will work or not.

If it doesn't you might want to try the SGD.   Another possibility is that the UUID of the root partition changed, I'm not sure, but here's some excellent info on Herman's website explaining how to determine your UUID's:
[http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst)
and this page:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

Added:  You could also use the gparted live cd(see Herman's previous reply)  perform a filesystem check on your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
I believe what you do is "right-click" on the partition & select "check".

---

### Post by Buz_Light on 2007-04-25
Hummm, I,m getting more and more confused... 
I've ran the SGD and tried

1. fix boot of GNU LINUX
2. selected sda6 as my LINUX partition (the only one available)
3. received the "SDG as succeeded" message
4. rebooted without SGD cd, tried to boot on latest kernel and received

error 17 : cannot mount selected partition...

I'm stucked there... Please help...

P.S. Sorry for asking so much... But I'm totally lost now... It's the first time I have to deal with boot issues.

---

### Post by confused57 on 2007-04-25
> **Buz_Light said:**
> Hummm, I,m getting more and more confused... 
I've ran the SGD and tried

1. fix boot of GNU LINUX
2. selected sda6 as my LINUX partition (the only one available)
3. received the "SDG as succeeded" message
4. rebooted without SGD cd, tried to boot on latest kernel and received

error 17 : cannot mount selected partition...

I'm stucked there... Please help...

P.S. Sorry for asking so much... But I'm totally lost now... It's the first time I have to deal with boot issues.

Have you tried booting your Ubuntu, using the SGD, & did you try the first method I mentioned in my reply(highlight & press "e"...)?

If neither method works, you might want to try to determine if the UUID's are correct using the link(s) I gave to Herman's site.  Something like:
```
 sudo vol_id -u /dev/sda6
```
see if the results agree with what's in your menu.lst kernel line.

Feel free to ask any questions you have, Herman will probably be able to help you & I'll attempt to if I can.

---

### Post by Herman on 2007-04-25
Hello, I'm still here but confused57 has beaten me to it. (It's the middle of the night here). I agree with confused57, don't bother restoring Grub to MBR anymore, just boot Ubuntu and fix your menu.lst. You should be able to do that either the way confused57 is saying. or this way here, whichever you think will be easier for you.
Boot Super Grub Disk and go 'English Super Grub DIsk'--> Gnu/Linux'-->'Boot Gnu/Linux Directly', and that should boot Ubuntu up for you. :)

Then when you are in Ubuntu, open your /boot/grub/menu.lst file 'sudo gedit /boot/grub/menu.lst', ```
sudo gedit /boot/grub/menu.lst
```Here is what your Ubuntu entry in mine looks like,
```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.20-15-generic [COLOR=Red][COLOR=Black]root=UUID=[/COLOR]51ea6a0c-e932-4a7f-ae16-2e4ae04f8302[/COLOR] ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```Okay, lets say here is you menu.lst entry now.  It may have the wrong UUID number because Partition Magic has interfered with it.  Partition Magic doesn't know anything about Linux, it's a primitive Windows application, SO I am guessing that's what's wrong. It's just a guess, but you can take a look and check by typing 'blkid' into a terminal and press 'enter' for a list of you current filesystem UUID numbers, like this,
```
herman@work:~$ blkid
/dev/sda1: UUID="f0ff07cb-3064-45fe-8ee5-a65a78cb20da" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="459F-9406" TYPE="vfat" 
/dev/hda1: UUID="2629-16F0" TYPE="vfat" 
/dev/hda5: UUID="7affdc27-ab39-4b16-91da-e9e8d9b672dd" TYPE="swap" 
/dev/hda6: UUID="[COLOR=Blue]fe7bf845-7ce9-4733-b6de-f70f2b62076d[/COLOR]" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb1: UUID="44F0-A71B" TYPE="vfat" 
/dev/hdb4: UUID="237f0cef-9905-41fb-82ba-bc360fb43a25" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: UUID="191d4618-7b62-41e6-ab41-7bd7a0708244" TYPE="swap" 
herman@work:~$ 
```Okay, so I highlighted in blue the one that is for my Ubuntu partition. The IIUD number in my menu.lst is wrong (just pretend), so I would copy the UUID number from my 'blkid' output and paste it over the old UUID number in menu.lst to cover it up and replace it, (overwrite it).
```
title        Ubuntu, kernel 2.6.20-15-generic
[COLOR=Red] root        (hd0,6)[/COLOR]
kernel        /boot/vmlinuz-2.6.20-15-generic [COLOR=Black]root=UUID=[/COLOR][COLOR=Blue]fe7bf845-7ce9-4733-b6de-f70f2b62076d[/COLOR] ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
``` Now it should be fixed.

Otherwise check to make sure the '[COLOR=Red]root (hd0,6)[/COLOR]' part is correct, that might be wrong too, maybe it should be something else now.

Will that fix your problem? I am guessing, but I am reasonably sure it will be a good guess that this will fix your error 17 problem, I hope so anyway, good luck,
Regards, Herman :)

confused57,
That blkid is a new one I picked up from here in the forums a few days ago that I like, it gives a nicer list than the other command, but I don't think it can be used from a LiveCD, we have to be booted into the OS first before we can use it. It gives a nice output though, I like it. :)

---

### Post by Buz_Light on 2007-04-25
> **Herman said:**
> Hello, I'm still here but confused57 has beaten me to it. (It's the middle of the night here). I agree with confused57, don't bother restoring Grub to MBR anymore, just boot Ubuntu and fix your menu.lst. You should be able to do that either the way confused57 is saying. or this way here, whichever you think will be easier for you.
Boot Super Grub Disk and go 'English Super Grub DIsk'--> Gnu/Linux'-->'Boot Gnu/Linux Directly', and that should boot Ubuntu up for you. :)

Then when you are in Ubuntu, open your /boot/grub/menu.lst file 'sudo gedit /boot/grub/menu.lst', ```
sudo gedit /boot/grub/menu.lst
```Here is what your Ubuntu entry in mine looks like,
```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.20-15-generic [COLOR=Red][COLOR=Black]root=UUID=[/COLOR]51ea6a0c-e932-4a7f-ae16-2e4ae04f8302[/COLOR] ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```Okay, lets say here is you menu.lst entry now.  It may have the wrong UUID number because Partition Magic has interfered with it.  Partition Magic doesn't know anything about Linux, it's a primitive Windows application, SO I am guessing that's what's wrong. It's just a guess, but you can take a look and check by typing 'blkid' into a terminal and press 'enter' for a list of you current filesystem UUID numbers, like this,
```
herman@work:~$ blkid
/dev/sda1: UUID="f0ff07cb-3064-45fe-8ee5-a65a78cb20da" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="459F-9406" TYPE="vfat" 
/dev/hda1: UUID="2629-16F0" TYPE="vfat" 
/dev/hda5: UUID="7affdc27-ab39-4b16-91da-e9e8d9b672dd" TYPE="swap" 
/dev/hda6: UUID="[COLOR=Blue]fe7bf845-7ce9-4733-b6de-f70f2b62076d[/COLOR]" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb1: UUID="44F0-A71B" TYPE="vfat" 
/dev/hdb4: UUID="237f0cef-9905-41fb-82ba-bc360fb43a25" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: UUID="191d4618-7b62-41e6-ab41-7bd7a0708244" TYPE="swap" 
herman@work:~$ 
```Okay, so I highlighted in blue the one that is for my Ubuntu partition. The IIUD number in my menu.lst is wrong (just pretend), so I would copy the UUID number from my 'blkid' output and paste it over the old UUID number in menu.lst to cover it up and replace it, (overwrite it).
```
title        Ubuntu, kernel 2.6.20-15-generic
[COLOR=Red] root        (hd0,6)[/COLOR]
kernel        /boot/vmlinuz-2.6.20-15-generic [COLOR=Black]root=UUID=[/COLOR][COLOR=Blue]fe7bf845-7ce9-4733-b6de-f70f2b62076d[/COLOR] ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
``` Now it should be fixed.

Otherwise check to make sure the '[COLOR=Red]root (hd0,6)[/COLOR]' part is correct, that might be wrong too, maybe it should be something else now.

Will that fix your problem? I am guessing, but I am reasonably sure it will be a good guess that this will fix your error 17 problem, I hope so anyway, good luck,
Regards, Herman :)

confused57,
That blkid is a new one I picked up from here in the forums a few days ago that I like, it gives a nicer list than the other command, but I don't think it can be used from a LiveCD, we have to be booted into the OS first before we can use it. It gives a nice output though, I like it. :)

Thanks Herman,
The UUIDs match in "blkid" output and menu.lst, exact same thing.
Hence, I guess the problem comes from the "hd0,x" string. 
How do I know which number to put there??

---

### Post by Herman on 2007-04-25
Well here is your fdisk ouput from a previous post, 
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         383     3076416   12  Compaq diagnostics
/dev/sda2   *         384        3234    22900657+   7  HPFS/NTFS
/dev/sda3            3235       12161    71706127+   f  W95 Ext'd (LBA)
/dev/sda5            3235        9423    49713111    7  HPFS/NTFS
[COLOR=Red] /dev/sda6            9424       11646    17856216   83  Linux[/COLOR]
/dev/sda7           11647       12161     4136706   82  Linux swap / Solaris
```Actually, now that I'm looking at that I can see that you should change (hd0,6) to (hd0,5).
Grub's numbering starts counting from 0, so it's always one less than the number you see from the Linux numbering scheme.
I reasd they are going to change that sometime soon, when Grub2 comes out. I guess they'll let us know when they do. But for now it's one number less than the Linux numbers say. [A Quick Guide to Grub's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")
Try something like this then, 
```
title        Ubuntu, kernel 2.6.20-15-generic
 root        [COLOR=Blue](hd0,5)[/COLOR]
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=51ea6a0c-e932-4a7f-ae16-2e4ae04f8302 ro quiet splash 
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```Try that,
Regards, Herman :)

---

### Post by Buz_Light on 2007-04-25
> **Herman said:**
> 
I reasd they are going to change that sometime soon, when Grub2 comes out. I guess they'll let us know when they do. But for now it's one number less than the Linux numbers say. [A Quick Guide to Grub's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")
Try something like this then, 
```
title        Ubuntu, kernel 2.6.20-15-generic
 root        [COLOR=Blue](hd0,5)[/COLOR]
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=51ea6a0c-e932-4a7f-ae16-2e4ae04f8302 ro quiet splash 
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```Try that,
Regards, Herman :)

Right, it works :) 
Thanks a lot for your help!!!

What would you suggest to resize my linux partition? Gparted ran from Ubuntu or on a boot CD?
Also, since I have installed Feisty Beta, should I install final release from scratch to make sure everything is updated or the auto update popping time to time do the job for me?

Thanks again to everyone who contributed to help me!

---

### Post by Herman on 2007-04-26
>  What would you suggest to resize my linux partition? Gparted ran from Ubuntu or on a boot CD?Buz_Light,
I would download and burn the latest version of [GParted -- LiveCD]("http://gparted.sourceforge.net/") to a CD-RW disk and use that. At the time of typing this, the most recent version of [GParted -- LiveCD  ]("http://gparted.sourceforge.net/")is gparted-livecd-0.3.4-6.iso, released on the 25th of March 2007. It's the 36th release of GParted LiveCD.
The version of GParted that Ubuntu uses is version 0.2.5, which is only the 17th release of GParted, quite an old version of GParted and extremely outdated, I'm sorry to say. It lacks many useful features that modern GParted versions provide. An important one is the ability to 'move' a Linux file system and resize from the beginning of the partition (to the right) as well as from the end of the partition (to the left). There have been quite a lot of other improvements made in GParted liveCD as well. Filesystem checking is another that comes to mind, and there are many more. So if you want to do any partitioning work besides just resizing Windows to install Ubuntu or just looking at your partitions you really should get the latest [GParted -- LiveCD]("http://gparted.sourceforge.net/"). It's free and it's only a 45MB download. :)

>  Also, since I have installed Feisty Beta, should I install final release from scratch to make sure everything is updated or the auto update popping time to time do the job for me? As long as you keep your system up to date, that should be all you need. Your system is already probably more up to date then the release CD if you have been keeping it updated, so you already have the latest software. (Except for GParted, maybe we'll get a newer version of that in an update someday soon).

Regards, Herman :)

---

