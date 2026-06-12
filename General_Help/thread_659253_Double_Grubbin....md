---
title: "Double Grubbin..."
date: 2008-01-05
forum: General Help
---

### Post by cdaringe on 2008-01-05
This could be a fun one (well maybe... I already ruined my fat32 partition doing all sorts of willy nilly things...but whatever, ive solved that problem already)

Objective: Have a bootable copy of ubuntu/mint on my external HDD that is inactive unless I select in my BIOS to boot from USB
Heres the scoop:  I've got a dual boot on my primary internal hd, sda.  My usb external is registered as sdb.  Everything is peachy on my internal drive.  I can boot into Ubuntu, Vista, and access my copy of ubuntu-mint that i installed on my external.  When i did install it on my external it did NOT give me the option of setting up grub on the external.  Its only option was on (hd0) which was my internal drive.

When I go to install grub from internal ubuntu, i'll type:
grub-install /dev/sdb1

That renders:
cdaringe@cdcraptop:~$ grub-install /dev/sdb1
/dev/sda3 does not have any corresponding BIOS drive.

Where does sda3? come into the picture??

When I fdisk - l :
cdaringe@cdcraptop:~$ fdisk -l

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3039    24410736   83  Linux
/dev/sdb2            3040        3161      979965   82  Linux swap / Solaris


Pointers?  tips?  I felt that this forum was most appropriate for the post.  I can move it elsewhere if someone finds it fit.  Thanks!

---

### Post by yellowbread on 2008-01-05
I have no idea where the sda3 came from either, but try

```
grub-install /dev/sdb
```

instead of

```
grub-install /dev/sdb1
```

leave the 1 off the end.

---

### Post by yellowbread on 2008-01-05
I just tried my own suggestion to install grub to a usb flashdrive and it didn't work 

Here's what did work. The flash drive is /dev/sdh.

```
filbert@filbert-desktop:~$ sudo grub-install --recheck /dev/sdh
Probing devices to guess BIOS drives. This may take a long time.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/hdb
(hd1)   /dev/sda
(hd2)   /dev/sdb
(hd3)   /dev/sdc
(hd4)   /dev/sdh
filbert@filbert-desktop:~$ sudo grub-install hd4
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/hdb
(hd1)   /dev/sda
(hd2)   /dev/sdb
(hd3)   /dev/sdc
(hd4)   /dev/sdh
filbert@filbert-desktop:~$ 
```

---

### Post by cdaringe on 2008-01-05
oh man, you are TOO cool.
everything said it worked just fine, but its not quite 100% yet.

cdaringe@cdcraptop:~$ grub-install --recheck /dev/sdb1
Probing devices to guess BIOS drives. This may take a long time.
/dev/sda3 does not have any corresponding BIOS drive.
cdaringe@cdcraptop:~$ sudo grub-install --recheck /dev/sdb
Probing devices to guess BIOS drives. This may take a long time.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb
cdaringe@cdcraptop:~$ 

i then ran the setup w/ hd1.

Booting from the usb external, it shows the exact screen that i get when i boot from the internal HD. i have a grxboot setup, so it was pretty obvious that when it installed grub on sdb it just copied my grub config files over.  this i thought was interesting and didnt quite understand.  when i try to boot to ubuntu, console, or windoze from the usb, it doesnt execute any of them.  that sort of made sense, considering that if it just copied my menu.lst over, there would be some sort of linking/address issues.  However, perhaps even more important.

I cant find my grub config files on the usb drive.  Where could they be?  They aren't in the usb /boot/grub.../boot/grub doesnt even exist.

hey man, thanks again for the first step too, that was a big step forward

---

### Post by yellowbread on 2008-01-05
Glad its worked so far.

My flash drive also seems to be using the menu.lst file from one of my hard drives when I boot from it . I'm going to try copying the menu.lst file from the hard drive to the flash drive and see what happens when I boot from the flash drive again.

The rest of what to do depends on it if works or not. Be back in a while.

---

### Post by yellowbread on 2008-01-05
Ok here's what we were missing -- the option "--root-directory" for grub-install. In the Ubuntu I'm installing grub from, my flash drive is mounted as /media/disk, so the following:

```
sudo grub-install --root-directory=/media/disk hd3
```

tells the grub I'm installing on the flash drive where to look for menu.lst and other stuff. The default root directory is the root directory of whatever you happen to be booted into when you invoke grub-install. (By the way, after rebooting and with other usb stuff attached, my flash drive is now hd3 which maps to sdc.)

So, go ahead and copy your menu.lst from sda to /boot/grub/menu.lst on your usb drive. Run the above with appropriate changes for how your usb drive is mounted and how the device map works. In your menu.lst, you will probably have to edit the new version on your usb drive, interchanging (hd0,x) and (hd1,x). Being a mathematician I can't resist the formula (hd[y],x)->(hd[1-y],x). 

Your windows partition might also need the lines 

```
map (hd0) (hd1)
map (hd1) (hd0)
```

added.

Here's my menu.lst entry for the windows partition:

```

title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

---

### Post by cdaringe on 2008-01-05
Awesome.  Another big step.
Though a big feat, my understanding is that by making those changes, I will have the same options whether i boot from usb drive or from the internal drive.  If i made those changes to the menu.lst on the external, I would essentially just be booting the OSs I already have configured and setup from the internal hard drive, but being commanded to do so by the external grub.  Am i correct..incorrect?  
My goal is to have the grub on the external usb be configured for the OS on the external USB.  I have other partions on the USB that I use for backup/storage in both windows and linux, but id like to be able to boot the OS on the USB independently time to time so i can have more or less a portable computer/distribution.

Using the tip you provided, I setup grub on the external.  Bingo.  I copied over my menu.lst and was able to edit it.  I stripped off the things that I didn't want to be accessed when booting from the USB, (both windows and my traditional ubuntu), and am now in process trying to figure out how to have grub configure itself for the LinuxMint (which is an Ubuntu deriviative) which is already installed on there.
Whew.

I'm a engineering student at OSU...so...bring on the math!  I finished all of my math courses, but practice keeps ya' sharp
:)

Thanks again

---

### Post by yellowbread on 2008-01-06
> **cdaringe said:**
> 
... my understanding is that by making those changes, I will have the same options whether i boot from usb drive or from the internal drive.  If i made those changes to the menu.lst on the external, I would essentially just be booting the OSs I already have configured and setup from the internal hard drive, but being commanded to do so by the external grub.  Am i correct..incorrect?  


That is correct. 

So for what you want, editing the menu.lst file on the usb drive by removing the entries for the stuff on the internal drive, and changing (hd1,x) to (hd0,x) ought to be all you need. 

Personally, I like to be able to boot any of my OSs from any of my hard drives in case something dies, or more likely, in case I screw something up.

---

### Post by cdaringe on 2008-01-06
Hey there,
so get this.
it got all those changes made, i get to my external HD grub menu, i choose my 'Mint' option, it begins and loads up the mint splash screen, yet boots ubuntu.
...
i.. i.. ?
recall when i first attempted to install grub without specifying the home dir?  could that be interfering somehow?  I wouldnt assume so because the system is obviously using the config that i edited. but im just eager to figure it out! so close...yet so far! i had a little celebration when mint started booting the first time. it was premature..

---

### Post by yellowbread on 2008-01-06
I think that means you have the boot information for your internal Ubuntu in the menu.lst file on the usb drive. You can probably get that figured out, but I would like to see the contents of each of the menu.lst files anyway, just to confirm my thoughts.

---

### Post by cdaringe on 2008-01-06
Yea, im sure thats the case...somehow.
the first is the standard grub menu.lst, and the second is the external menu.lst
note that on the external, i have the EXTERNAL marked as HD0, not HD1. it seems that the internal maps to hd1 when booting from the external. kind of the opposite from the internal.  the two different device.maps are exactly the same however. quirky.

---

### Post by yellowbread on 2008-01-06
Thanks for those files. You are using the UUID of the internal Ubuntu partition in the external menu.lst.

Where it says:

```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a6913ace-4c50-4882-ba89-cb9604f8d784 ro quiet splash vga=4
```

replace the "root=UUID=a6913ace-4c50-4882-ba89-cb9604f8d784" part with

```
/root=/dev/sdb1
``` 

Or, if 

 ```
sudo /sbin/vol_id -u /dev/sdb1

```

gives meaningful results, use the number it returns as UUID instead of what you have.

Of course, your external Mint partition might not be sdb1, it might be sda1 or even something else.

```
sudo fdisk -l
```

will tell you what it actually is. It is a 2.6.22-14-generic kernel on the external drive isn't it? if not, you will have to make the appropriate changes there also.

I hope this works.

---

### Post by cdaringe on 2008-01-07
givin it a shot, will report back

---

### Post by cdaringe on 2008-01-07
yellowbread,
theres no one cooler than you.  thank you so much. raving success.

for those who are surfing the net, trying to install an OS on mulitple hard drives and boot indepentently, read through the post, it may be of some assistance.

:)

---

### Post by yellowbread on 2008-01-07
I'm glad it all worked.

 Now that that's all taken care of, it occurred to me that there has got to be an easier more direct way to do this. If anyone knows of one, please fill us in.

---

