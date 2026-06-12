---
title: "switch between partitions"
date: 2006-12-03
forum: General Help
---

### Post by Jack of Fables on 2006-12-03
i installed ubuntu months ago, but recently needed to reinstall windows for a couple apps, i resized my ubuntu partition in sabayon, and liked sabayon so installed that on a small partition of spare memory. now i have 3 operating systems on my computer and can't figure out how to switch between them. a little help would be appriciated.

---

### Post by Sef on 2006-12-03
Upon boot up, you should have the option of choosing which operating system you want to go into.   If you go into ubuntu automatically that is your default.  To go into another one, just use the down arrown when ubuntu is highlighted in the boot process.

---

### Post by Jack of Fables on 2006-12-03
it automaticaly goes into windows, and i don't recal seeing a list of what i could go into

---

### Post by nikhilk on 2006-12-03
> **Jack of Fables said:**
> it automaticaly goes into windows, and i don't recal seeing a list of what i could go into
That is weird! Post your "/boot/grub/menu.lst".

---

### Post by Jack of Fables on 2006-12-03
which is?
i know that the partitions are there because i see them on gparted or something like that in the sabayon live dvd

---

### Post by nikhilk on 2006-12-03
> **Jack of Fables said:**
> i know that the partitions are there because i see them on gparted or something like that in the sabayon live dvd
Thats alright. In order for you to see those partitions at boot time the "/boot/grub/menu.lst" file must contain the proper entries.

---

### Post by bulldog on 2006-12-03
Did you overwrite the MBR?
If so reinstall GRUB with the live cd,
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Finally exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by Jack of Fables on 2006-12-03
so i need to use a live cd, could xubuntu work, cause i can't find my ubuntu cd, and im out of cds. but i do have xubuntu that i installed on my dads computer.or sabayon. and with grub it should let me chose which operating system to boot into? would it be bad to install os x86 on another partition (lots of space on my hd), if not, how much space should i give?

---

### Post by dmartinsca on 2006-12-03
Any bootable linux system will work. If you still have the disk for sabayon, just use that. Follow bulldog's post on how to restore grub to the MBR and you should be good to go!

---

### Post by Jack of Fables on 2006-12-03
ok, thanks for all the help!

---

### Post by Jack of Fables on 2006-12-06
its not the same as it was originally now. i can't get into any os now and am on my live cd. i tried all my options. nothing. figured boot might do something good but said i needed to load kernel first or something. plz help quickly

---

### Post by Jack of Fables on 2006-12-07
please someone help, im stuck using my live cd because i reinstalled gnome and now i can't get through it. i have 3 partitions that have os's installed on them, i was stuck on windows. someone said to reinstall gnome to switch between them at boot, but i can't get through gnome!

---

### Post by drphilngood on 2006-12-07
> **Jack of Fables said:**
> please someone help, im stuck using my live cd because i reinstalled gnome and now i can't get through it. i have 3 partitions that have os's installed on them, i was stuck on windows. someone said to reinstall gnome to switch between them at boot, but i can't get through gnome!

How does this problem relate to this thread?

> **Jack of Fables said:**
> thats was a while ago, i need to move a ext3 partition and a ntfs partition and my problems will be gone, sorda.

[increase partition size]("http://www.ubuntuforums.org/showthread.php?p=1855388#post1855388")

We can´t help you if you don´t tell us all that is happening...

---

### Post by Jack of Fables on 2006-12-07
I made this thread and am still havng problems with switching between my partitions. they said reinstall gnome, i did. now i can't get through it. that enough for ya?
o, and the problem is i can't figure out how to get through gnome, it was originaly automatic, then i installed windows and that got rid of gnome. i couldn't switch between my partitions. some one said reinstall gnome, i did. now it is like a terminal or something. i looked at the commands, none look like anything that will help me get to my partitions. i tried boot, but it said something about loading the kernel fisrt or something.

---

### Post by bulldog on 2006-12-07
Yes for now.
I didn't advice you to reinstall Gnome but GRUB,which is your bootloader.

If you did,and you have one disk connected give us the outcome of```
sudo fdisk -l (l as in like)
```
Than we can have a peek at your partitions.

And while your working hard at the fdisk command,I have another one coming.

---

### Post by Hendrixski on 2006-12-07
> **Jack of Fables said:**
> please someone help, im stuck using my live cd because i reinstalled gnome and now i can't get through it. i have 3 partitions that have os's installed on them, i was stuck on windows. someone said to reinstall gnome to switch between them at boot, but i can't get through gnome!

I don't think that re-installing GNOME is what they meant, it sounds like you re-installed windows on one of your partitions so it took out the GRUB bootlader.  If you re-install grub (which you can do from the live CD) it should fix it.  If grub doesn't detect the 3 operating systems then edit /boot/grub/menu.list and put them in there.

:)

---

### Post by Jack of Fables on 2006-12-07
sorry, dosed off while i was typeing, i meant grub and thats what counts right?

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4328    34764628+  83  Linux
/dev/sda2            4329       10855    52428127+   7  HPFS/NTFS
/dev/sda3   *       10856       11976     9004432+  83  Linux
/dev/sda4           11977       12161     1486012+   5  Extended
/dev/sda5           11977       12161     1485981   82  Linux swap / Solaris

i opened menu.list, but it says that it does not exist anynore?

---

### Post by bulldog on 2006-12-07
> **Jack of Fables said:**
> sorry, dosed off while i was typeing, i meant grub and thats what counts right?

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4328    34764628+  83  Linux
/dev/sda2            4329       10855    52428127+   7  HPFS/NTFS
/dev/sda3   *       10856       11976     9004432+  83  Linux
/dev/sda4           11977       12161     1486012+   5  Extended
/dev/sda5           11977       12161     1485981   82  Linux swap / Solaris

Okay.now we gonna mount your ubuntu to see your menu.lst.
```
sudo mkdir /mnt/rescue
```
```
sudo mount /dev/sda3 /mnt/rescue
```
```
sudo gedit /mnt/rescue/boot/grub/menu.lst
```
The output off the last command would be appreciated :D
I presume that sda3 **is** your ubuntu?

**EDIT:**
I've noticed that your windows is on your second partition.
In order to have it boot,you probably have to change your boot.ini with the right partition.
See here for a how to.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors)

---

### Post by Jack of Fables on 2006-12-07
ubuntu is sda1, sabayon is sda3. should i just replace sda3 with sda1 when i do it?
i copied and pasted everything exactly as typed and it opened menu.lst in a text editor

---

### Post by bulldog on 2006-12-07
Yes copy and paste it to the forum please,so we can enjoy it together :D

See my edit in my previous post

---

### Post by Jack of Fables on 2006-12-07
its empty
but it was sabayon, not ubuntu that was mounted

---

### Post by bulldog on 2006-12-07
Huh?
You have mounted sda1 I presume?
```
cat /mnt/rescue/boot/grub/menu.lst
```

Is this one empty too?
Make a new mountpoint```
sudo mkdir /mnt/ubuntu
```
```
sudo mount /dev/sda1 /mnt/ubuntu
```
```
sudo gedit /mnt/ubuntu/boot/grub/menu.lst
```
This one on the forum please.

---

### Post by Jack of Fables on 2006-12-07
windows was booting fine until i reinstalled grub, now it just won't boot anything
no, let me do it now

---

### Post by Jack of Fables on 2006-12-07
here it is on sda1

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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bulldog on 2006-12-07
You should be able to boot Ubuntu because this is set right in GRUB.
You have no entry for windows nor Sabayone.
To boot windows we can put an entry into GRUB,but I don't know if it will boot,because it's on the second partition.
See one of my previous post for explanation.
```
## END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify (hd0,1)
makeactive
savedefault
chainloader	+1


#on  /dev/sda1
title     Sabayone
root (hd0,2
kernel   this you have to fill in yourself,but I have not done this before so        I'm not dure if this is allright this way.
initrd
quiet
savedefault
boot
```

---

### Post by Jack of Fables on 2006-12-07
im confused, i can get rid of my sabayon partition, and windows booted fine before i installedd grub, so shouldn't it still work? and am i supposed to do soomething with this?

---

### Post by bulldog on 2006-12-07
Yes,at least the windows part you should copy to the bottom of your menu.lst,save the file and try to reboot from hard disk.

Pay attention at errors please.
```
## END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify (hd0,1)
makeactive
savedefault
chainloader	+1
```

---

### Post by Jack of Fables on 2006-12-07
copy and paste all of it to the bottom?
and windows is sda2, it says sda1

---

### Post by bulldog on 2006-12-07
Just copy what isn't there.
The ##END DEBIAN BLA BLA you shouldn't copy if it's already there.

And you're right of course it should be sda2 instead.
You can change that one

---

### Post by Jack of Fables on 2006-12-07
even though sda1 isn't windows, but ubuntu?

---

### Post by bulldog on 2006-12-07
> **Jack of Fables said:**
> even though sda1 isn't windows, but ubuntu?
Read previous post please

---

### Post by Jack of Fables on 2006-12-07
o, sorry, thanks for all the help!

---

### Post by strabes on 2006-12-07
Here's a howto for restoring grub: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Jack of Fables on 2006-12-07
i think i need some instructions to get through grub cause i still can't do it

---

### Post by bulldog on 2006-12-07
What do you need to know?

---

### Post by Jack of Fables on 2006-12-07
when i start my computer, i get a couple lines of text, then something about starting grub. followed by grub which is text based something or other, it looks like a terminal but says grub> or somethiing. i can't figure out how to get passed it. if you need more information, odds are i won't know and will need to restart my compter and wait for that to load up, then find out, then wait forever for my sabayon live cd to load. i can't get passed grub to get to my partitions or whatever it is i need to get to.

---

### Post by bulldog on 2006-12-07
It's possible you have to boot another time into the live cd :( 
You have to mount your ubuntu partition again,and have a look at your fstab.
It's very much possible it points to the wrong partitions.

Your fstab is in /etc/fstab and you can edit it with gedit.
Be sure that the lines points to the right partitions according to what is in menu.lst.

---

### Post by Jack of Fables on 2006-12-07
that brought up the live cd's fstab, but i found the one one ubuntu.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

not sure what i need to do with it

---

### Post by bulldog on 2006-12-07
It points to the right partitions so you have nothing to do here.
Didn't think it should help,but you never know.

Well as I can see everything is set up as it should be,so don't know what to do anymore for now.

I will think it over and see if I can think of something else after a good night of sleep.

---

### Post by Jack of Fables on 2006-12-07
what should grub show at system startup?

---

### Post by Jack of Fables on 2006-12-07
now i'm getting an error message when grub tries to load, I think it's #72 or something. is there an alternate boot loader that is easier?

---

### Post by bulldog on 2006-12-08
You should pay attention to errors,and take a good look at them,they can help to come to a solution.
If you're guessing what the error is,you can't expect you get much help.

An easier boot loader?there's nothing wrong with GRUB,but if you go fiddling with partitions or what ever,you can have any boot loader but it will fail too.

It very easy to understand how it works.
Take a look at this site and you know all you ever need to know,

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Jack of Fables on 2006-12-08
that helped, it seems the problem i'm having is that it boots in to the comand line interface, when i need it to boot into the gui. and i bet the problem i'm having with the error is that i uninstalled sabayon because i didn't need it (just takein space). i'll reinstall grub just to be sure, then tell you if it boots into cli or gui.

---

### Post by Jack of Fables on 2006-12-08
great news, it works!
i reinstalled grub, then i rebooted (sent me to ubuntu).
pressed esc while grub was loading and got hte menu to chose what to boot into. thanks

---

### Post by Ravana on 2006-12-11
[QUOTE=Jack of Fables;1856918]here it is on sda1



## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu



Snipped a bit here...
You need to edit the above lines a bit for the GRUB screen to appear:
Set the timeout to 10 and put one of those # thingies in front of hiddenmenu in the last line.

---

