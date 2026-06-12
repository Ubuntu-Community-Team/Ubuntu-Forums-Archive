---
title: "How to format usb stick?"
date: 2016-12-14
forum: General Help
---

### Post by 1ritesh on 2016-12-14
Hello,
i have made boot from usb stick it is now showing ~3.89Mb but it real size is 4/8gb two pen drive sony and hp 
please how to get it real 8/4gb??

---

### Post by TheFu on 2016-12-14
Not certain I understand the question. "4/8gb" means?   and "8/4gb" means exactly what?

I can make some guesses to the meaning.
a) There are many counterfeit flash drives in the world. The packages say xyzGB and the true size is less. Could that be the situation? The only way to validate is to actually write specifically sized data to the storage.  It mostly happens with name-brand storage of 32G or larger, so the first thing I do after getting any new flash drive is to try and store data just a little smaller than the advertised amount.  Bad devices have been found everywhere - online, sketchy places and a high-end retail and online stores that would never risk their reputation over a $25 device. No good way to know based on purchase location, that's the point.
b) Storage vendors and software people disagree on the meaning of 1KB and 1 KiB. This difference becomes larger and larger as more storage is involved.  Storage people say 1K is 1000Bytes.  Software people say 1K is 1024Bytes.  OSes report what software people say, so 3.89 x 1024 is 3983.36B (very close to 4G), then we subtract the storage used for "formatting" and it all makes sense.  Most people don't need to be exact with their size statements and assume the software people version is correct (based on 1024B in 1 KB).

Or I've completely missed the question.

This size difference is enough of an issue that storage people (I'm a software guy at heart) have made up a new unit of measure and wikipedia has articles explaining the differences: [https://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](https://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)
>  This discrepancy causes confusion, as a disk with an advertised capacity of, for example, 400 GB (meaning 400000000000 bytes) might be reported by the operating system as 372 GB, meaning 372 GiB.
Same thing?

---

### Post by PaulW2U on 2016-12-14
> **1ritesh said:**
> i have made boot from usb stick it is now showing ~3.89Mb but it real size is 4/8gb two pen drive sony and hp 
please how to get it real 8/4gb??
Hi 1ritesh, like TheFu I'm a little confused by what you have written but I think you're saying that you have two USB sticks, one 4GB and the other 8GB but they are both reporting just 3.89MB available. I've seen something similar when I have used different applications to write ISO images to USB sticks.

I can't offer a technical explanation as to why this happens but I think that **gnome-disk-utility**, which appears as **Disks** in Ubuntu menus, will format the USB device so that the full capacity becomes available. Of course there may be other solutions which use different applications that will solve your problem.

---

### Post by RobGoss on 2016-12-14
As PaulW2u stated, the **disk utility** will allow you to format that USB, just open up the disk utility in the upper right hand corner of the tool choose **format**, make sure you choose the correct drive to format you don't want to format the wrong drive

It should format the USB drive  to its original state

---

### Post by ajgreeny on 2016-12-14
Depending on what you used to create the installation or boot USB disk you may also have to create a new partition table before formatting the unallocated space that makes into a partition.

Gparted which you can install from the repos is probably the easiest way to do that, though the Disks application may also be able to; I have never used it so am unfamiliar with its abilities.

---

### Post by 1ritesh on 2016-12-15
> [COLOR=#000000]Hi 1ritesh, like TheFu I'm a little confused by what you have written but I think you're saying that you have two USB sticks, one 4GB and the other 8GB but they are both reporting just 3.89MB available. I've seen something similar when I have used different applications to write ISO images to USB sticks.[/COLOR]

[COLOR=#000000]I can't offer a technical explanation as to why this happens but I think that [/COLOR]gnome-disk-utility, which appears as Disks in Ubuntu menus, will format the USB device so that the full capacity becomes available. Of course there may be other solutions which use different applications that will solve your problem.

yes, i have two pendrive which was used as boot usb showing few mb size.
how to get in 8gb and 4gb size?
i want to know after format the the size is same in fewmb why?

---

### Post by QIII on 2016-12-15
Hold on for a moment, please.

First, let's clarify.  You say you have two devices.

One is a 4GB device that is reporting its size as 3.89GB.

The other is an 8GB device that is reporting its size as 3.89GB.

Is that correct?  This was asked earlier, but you did not answer directly.

---

### Post by 1ritesh on 2016-12-15
> [COLOR=#000000]Hold on for a moment, please.[/COLOR]

[COLOR=#000000]First, let's clarify. You say you have two devices.[/COLOR]

[COLOR=#000000]One is a 4GB device that is reporting its size as 3.89GB.[/COLOR]

[COLOR=#000000]The other is an 8GB device that is reporting its size as 3.89GB.[/COLOR]

[COLOR=#000000]Is that correct? This was asked earlier, but you did not answer directly.[/COLOR]

i have two usb stick one is 4gb another is 8gb
i used usb as bootable to install ubuntu i have writer iso file in usb after that moment both usb is showing ~2.9MB space it is not formatting under ntfs..

---

### Post by QIII on 2016-12-15
OK.

What tool or process did you use to get the bootable image on to each drive?

---

### Post by sudodus on 2016-12-15
I think there are some data near the head end of the drive, that is causing this confusion. You can use mkusb to wipe the first megabyte, or let it restore the drive to a standard storage device with an MSDOS partition table and a partition with the FAT32 file system (or some more advanced partitioning). See these links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by 1ritesh on 2016-12-15
> [COLOR=#000000]OK.[/COLOR]

[COLOR=#000000]What tool or process did you use to get the bootable image on to each drive?[/COLOR]
sir it was Win32dishImager .

---

### Post by sudodus on 2016-12-15
Win32DiskImager is a cloning tool. I think mkusb can help you restore it :-)

I have used it many times for that particular purpose.

---

### Post by 1ritesh on 2016-12-15
> [COLOR=#000000]I think there are some data near the head end of the drive, that is causing this confusion. You can use mkusb to wipe the first megabyte, or let it restore the drive to a standard storage device with an MSDOS partition table and a partition with the FAT32 file system. See these links,[/COLOR]

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe]("https://help.ubuntu.com/community/mkusb/wipe")

how to do download this software?

---

### Post by sudodus on 2016-12-15
It is described in the links, but here it is:

The fastest way to start making and repairing USB boot drives is to install the mkusb PPA, install and update the mkusb package like all the other program packages.

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu
```

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install **mkusb** mkusb-nox usb-pack-efi
```

---

### Post by 1ritesh on 2016-12-15
after this command will make usb will be fine?

---

### Post by sudodus on 2016-12-15
It works for me. The crucial step is to wipe the first megabyte. It can be done with other tools too, for example with ***dd***. But dd is dangerous. mkusb 'wraps a safety belt' around dd.

---

### Post by 1ritesh on 2016-12-15
how mkusb will work?

---

### Post by sudodus on 2016-12-15
Please read the information at the links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

and try it.

-o-

If you only trust software, that is part of the official Ubuntu release, you can use ***Disks*** instead and wipe the whole drives (overwrite with zeros). It will also work, but slower. (It is usually enough to wipe the first megabyte, which is an option with mkusb.)

And you should be very cautious. Check and double check, that you will wipe the pendrives, and not an internal drive or an external drive with all the family pictures.

---

### Post by 1ritesh on 2016-12-15
i have used the comand it say unable to find.

how to solve problem?

---

### Post by lisati on 2016-12-15
> **1ritesh said:**
> i have used the comand it say unable to find.

Which command?

---

### Post by sudodus on 2016-12-15
> **1ritesh said:**
> i have used the comand it say unable to find.

Which command?

1. Did you try to use Disks? It can be started from Unity's Dash or from the menu of for example Lubuntu. The command to use from a terminal window is

```
gnome-disks
```

2. Or did you use the commands to install mkusb? The command lines should be run in a terminal window. In that case what happened? Please describe the output after entering the commands.

3. Or did you install mkusb. In that case, which command did you use to run mkusb? It can be started from Unity's Dash or from the menu of for example Lubuntu. It can also be started with the following command line in a terminal window,

```
sudo -H mkusb
```

or to get directly to the wipe menu

```
sudo -H mkusb wipe
```

You must also enter the password (the usual password to log in to your user).

---

### Post by 1ritesh on 2016-12-16
It say mkusb command not found

what is hardisk temperature monitor?

---

### Post by sudodus on 2016-12-16
> **sudodus said:**
> It is described in the links, but here it is:

The fastest way to start making and repairing USB boot drives is to install the mkusb PPA, install and update the mkusb package like all the other program packages.

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu
```

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install **mkusb** mkusb-nox usb-pack-efi
```

> **1ritesh said:**
> It say mkusb command not found

If you are running Ubuntu or an Ubuntu family flavour, please try again to install mkusb according to the instructions above. You can copy and paste the command lines from here to a terminal window. That way you can avoid typing errors.

---

### Post by C.S.Cameron on 2016-12-16
If the Live drive was created with an ISO9660 partition and a FAT32 partition, Windows would only see the FAT partition.
The ISO9660 partitions are a little hard to get rid of, they don't want to unmount with gparted, (except in Puppy or gparted Live).
The easiest way I have found to delete them is to create a new partition table with gparted.
The OP probably needs a msdos table with FAT32 file system.

Sorry to interrupt, on second thought mkusb is the easiest method.

---

### Post by 1ritesh on 2016-12-17
[ATTACH=CONFIG]272737[/ATTACH]how to delete this??

---

### Post by sudodus on 2016-12-17
Install *mkusb* and use it to wipe the first megabyte. It is easier than to use Disks. After that you will be able to use any partitioning tool, for example *gparted* in linux or the built-in 'formatting' tool in Windows.

Or let *mkusb* do the whole job and restore the drive to a standard storage device with an MSDOS table with FAT32 file system as suggested by *C.S.Cameron*.

-o-

It is also possible to use *Disks* - search the available options (click on the buttons), and you will find out how to use it.

Warning: Be careful so that you do the actions on the correct drive.

---

### Post by RobGoss on 2016-12-17
It seems to me that the OP is at the right option all you need to do is click on the **menu **in the** top right hand **corner of the **Disk tool **and choose format, it should do it's thing

---

### Post by C.S.Cameron on 2016-12-17
It is an ISO9660 partition, hard to unmount in Ubuntu,
I'm not sure Files can see it in Ubuntu.

Edit:

If the OP wants to keep partition 2 then perhaps wiping the partition table may not be the best idea.

Either Puppy Linux or the gparted Live CD/USB should be able to format the ISO9660 partition and leave everything else as is.

---

