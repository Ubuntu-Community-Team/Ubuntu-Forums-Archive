---
title: "Can't see memory chip from camera with USB adapter"
date: 2015-05-20
forum: General Help
---

### Post by RogerDavis on 2015-05-20
I have two Fuji Camera memory chips (actually common PNY or eFilm chips), inserted into several different adapters that are not mounted or opened when I connect the adapters.

    The chip seems to be found by the system. See Below :
    Disk /dev/sdd: 15.8 GB, 15819866112 bytes
    83 heads, 15 sectors/track, 24817 cylinders, total 30898176 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000

    But I can't see or work with the chips unless they are inserted into the camera, and the camera is connected by its USB cable.

    How do I fix this, make it auto mount, etc, just like a common USB thumb drive?

---

### Post by SeijiSensei on 2015-05-20
Can you mount /dev/sdd1?  /dev/sdd refers to the entire device; filesystems reside within the partitions like /dev/sdd1.  Try
```
sudo mount /dev/sdd1 /mnt
```
What happens?  Can you see your files with "ls /mnt"?

---

### Post by RogerDavis on 2015-05-20
No luck here.  The only way I can see the files is by putting the card into the camera, then connecting the camera with it's USB cable to the computer.


roger@roger-desktop:~$ sudo mount /dev/sdd1 /mnt
[sudo] password for roger: 
mount: special device /dev/sdd1 does not exist
roger@roger-desktop:~$ ls /mnt
roger@roger-desktop:~$

---

### Post by SeijiSensei on 2015-05-20
Most off-the-shelf memory cards are formatted with FAT32.  Is that the case with yours, or did the camera format the card?  Perhaps it uses a proprietary file system.

If you insert the card into a Windows machine, can it read it?

---

### Post by RogerDavis on 2015-05-20
This machine is dual OS, on separate drives, essentially two different machines.  Neither one can see the card unless it's in the camera, and even that is a try, try again kind of thing.

At least one of the cards was used as purchased.  The other I'm not sure about.  BUT both have now been camera formatted, and the same problem exists.

---

### Post by SeijiSensei on 2015-05-21
If Windows can't read the card either, I'd guess it's using a proprietary filesystem of some kind.

Some printers have a card reader slot.  If you have one of those, you could give it a try there.

Have you tried formatting the card from Linux or Windows before putting it in the camera?  On Linux, you can use
```
sudo mkfs -t vfat /dev/sdd1
```
assuming the device has a partition already.  If not, you can use "sudo fdisk /dev/sdd" to create one, or format it from Windows as FAT32.

---

### Post by RogerDavis on 2015-05-21
I tried:
roger@roger-desktop:~$ sudo fdisk /dev/sdd
[sudo] password for roger: 
fdisk: unable to open /dev/sdd: No such file or directory
roger@roger-desktop:~$ 
roger@roger-desktop:~$ 
roger@roger-desktop:~$ sudo mkfs -t vfat /dev/sdd1
mkfs.fat 3.0.26 (2014-03-07)
/dev/sdd1: No such file or directory
roger@roger-desktop:~$ 

Also, I tried Windoze, it won't format it because it can't see it.

I don't think I can format it from either OS through (not with) the camera, but I'm afraid to try as it might toast the camera?

Printer doesn't have a card slot.  However, the router has a USB plug.  I tried the adapter/card into there, router quit working until I restarted it.

---

### Post by Bucky Ball on 2015-05-21
This is how you should be able to format the card, from [here]("http://smallbusiness.chron.com/format-fuji-sd-memory-card-digital-camera-49466.html"):

> PC Card Reader
Step 1

Insert the SD card fully into your computer's memory card reader. If you are using an external card reader, connect the card reader to your computer before inserting the memory card.
Step 2

Open the Start menu and click "Computer." You should see the SD card displayed with a label such as "SD/MMC" and a letter assignment such as "F:".
Step 3

Right-click the icon for the memory card and select "Format" on the context menu.
Step 4

Type a label for the SD card in the "Volume Label" field. To maintain compatibility with your digital camera, do not change the default settings for the card's file system or allocation unit size.
Step 5

Click the "Start" button to format the SD card.


If you can't do it this way (particularly step 2, and you see nothing of the card at that point) I'd say there is something very odd going on with the way your camera has formatted the card.

I have been popping into this thread on and off and, as suggested by SeijiSensei, a proprietary filesystem on the cards is a possibility I've been thinking about since first viewing. The above quote throws no light on this and neither have you to this point. Perhaps put the card in the camera and see if you can determined the filesystem the card is formatted in or check the manual. Make moving forward a lot easier as we're doing a bit of grasping at straws without that information. ;)

PS: [Here's]("http://www.fujifilm.com/support/digital_cameras/compatibility/card/s/") a list of compatible cards. Is yours there?

---

### Post by sudodus on 2015-05-21
Can your card reader read other cards/chips?

I also think that they are special cards/chips, maybe formatted in a different way by the camera.

Maybe they are configured differently at a very low level, which can explain that they are not even recognized as devices. Maybe they look like common PNY or eFilm chips, but they are really something else.

---

### Post by RogerDavis on 2015-05-23
1) I have only SD chips here (8 and 16 GB), but the readers have worked before.

2) I just buy the SD cards "over the counter", not in any special place or way.

From the manual:

Memory Cards
Pictures can be stored in the camera&#8217;s internal memory or on optional SD and SDHC memory cards. In this
manual, SD memory cards are referred to as &#8220;memory cards.&#8221; For more information, see page 10.

Compatible Memory Cards
SanDisk SD and SDHC memory cards have been approved for use in the camera. A complete list of ap-
proved memory cards is available at [http://www.fujifilm.com/products/digital_cameras/index.html](http://www.fujifilm.com/products/digital_cameras/index.html). Op-
eration is not guaranteed with other cards. The camera can not be used with MultiMediaCard (MMC)
or xD-Picture Cards.

---

### Post by RogerDavis on 2015-05-23
From Places, Computer, the card isn't directly seen. 

If I try to format from "Disks", which identifies it as " /dev/sdc1, 8.0GB unknown, W95 FAT32" I get   "Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)"

What I'm actually trying to do is not format, but read these cards without the camera.  The format was just another way to try to get it seen.

---

### Post by sudodus on 2015-05-24
I must admit that I do not understand the problem with these cards, I can only guess.

Maybe there is something special with the format created by the camera, which is OK, as long as the camera itself is reading it. Maybe another card adapter might read it too, maybe not.

Since you are prepared to format the cards, you might also try to wipe them (write zeros so overwriting also the partition table at the head of the available memory space). This method can sometimes revive USB pendrives. See this link

[https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)

See also [this link where some of the text (but not all of it) might be applicable to your case]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297"). The cards are obviously not 'gridlocked', they are possible to read with your camera, but they are somehow impossible to read with your card reader. So maybe it would help to wipe the first megabyte.

But maybe you have to format them in your camera in order to use them in your camera, and you will be back where you are now.

---

### Post by RogerDavis on 2015-05-24
I have a hunch that these cards might be different from earlier cards I had.  These are SDHC class 6 chips.  

I'm now trying to research what affect the cards may have.  I found one chip that is unmarked, but it doesn't work either.  I suspect is is the original in the camera.

---

### Post by sudodus on 2015-05-24
It is possible that your card reader does not work with SDHC cards.

---

### Post by RogerDavis on 2015-06-12
Somehow, BOTH reader adapters had become damaged.  I took the chip to a different location, had another of the same reader there, it works. 

I received a new reader adapter I ordered, it works on USB 3.0, but not on the 2.0 ports on the top front!?!  The light flashes for a while, then goes solid, but nothing works no matter how long I wait.

I have a Card Reader Writer that won't display the SD card, but if I plug the reader adapter into it's 2.0 USB port, that works.

So:
- Card readers were bad (maybe damaged by my compter top front USB ports
- Why only those ports, and how to fix?

---

### Post by sudodus on 2015-06-12
Have you tried with a USB extension cable (or hub with cable) from the rear USB ports?

---

### Post by RogerDavis on 2015-06-12
That is the 3.0 connection I mentioned that does work.  The 3.0 is on an extension cable.  The USB 2.0 on the card reader also works.

Both of the 2.0's on the computer front panel do not work.  I suspect that they may have damaged my other two readers so that they don't work on ANY ports, and started all this.  So I'm concerned about how to fix these two 2.0 ports.

---

### Post by sudodus on 2015-06-13
Let us hope that someone who knows more about hardware will read this and help you. Otherwise maybe there is some small local repair shop for computers. You could ask there if it can be repaired for a reasonable cost, of if is better to use the working USB connections via an external hub.

---

### Post by RogerDavis on 2015-06-17
I took the original two readers to another place, and they didn't work there either.

I bought two more dirt cheap readers on Ebay, they worked on all ports...

Now I'm stuck with trying to find out how both of the originals got junked...

---

