---
title: "Attempting to run 16.04 from USB stick ... can not change settings"
date: 2016-10-04
forum: General Help
---

### Post by oldsoundguy on 2016-10-04
I have made a USB stick with 16.04 on it and run Ubuntu on my Windows 7 laptop.  
It will boot to the system just fine and I can navigate through it.  Make changes such as accessing my home network and add things such as a printer.
The issue is that those changes disappear if I shut down and re-boot. 
I really do NOT want to set up a dual boot.
Is this a normal thing? Or is there a way to add or change (or even UPDATE)?

---

### Post by colmax on 2016-10-04
You may need to redo the liveusb and add Persistance when you do it
Persistance allows space to write changes to the liveusb
Maybe 2GB would do
Cheers

---

### Post by oldsoundguy on 2016-10-04
I have a stick that was created using Rufus.  Can I just ADD Persistance?

---

### Post by ian-weisser on 2016-10-04
Not easily. Persistence requires a separate partition on the USB stick. Repartitioning may or may not destroy the existing Ubuntu image.
You might be able to, if you are skilled with partitioning tools.

If not, remake the stick with persistence. Faster and easier than learning how to safely edit partitions using Windows tools.

Also, persistence is a limited trick. When the persistence space fills up, you won't be able to make changes anymore.
Ubuntu images are limited snapshots intended for you to test on your hardware. They are not designed for everyday use, and cannot be usefully upgraded.

---

### Post by oldsoundguy on 2016-10-04
I have a 16GB stick so there is plenty of room.  I am willing to go to point A and start all over again.  Have the ISO (did not erase it). also still have Rufus .. so starting over is not a problem.  Can create more than a single partition if need be .. so how should I go about this?  (BTW, thanks for the answers thus far .. you are pointing me in the right directions, but seem to be missing a step or two.  Most of the "help" I have seen on the forums seems to be assuming that I am doing this on a Linux box .. no .. this is on a Win 7 laptop.)

---

### Post by C.S.Cameron on 2016-10-04
You can use mkusb to make a 16.04 usb stick with a persistent partition, (casper-rw).
Unetbootin will make a USB stick with persistent file, but is limited to 4GB.
I do not see "persistence" mentioned on the Rufus page.
With Ubuntu 16.04 64 bit you might be able to insert a blank casper-rw file on the root of the drive and edit syslinux.cfg, txt.cfg, text.cfg or grub.cfg to add the word persistence, (after "-- ").

---

### Post by oldsoundguy on 2016-10-04
Guess I am missing something here.  Went to my Ubuntu desktop and installed mkusb, downloaded 16.04 64bit ISO.
Then ran mkusb and it created a bootable disk. The thing boots, but when I go to make a change .. and re-boot .. NOTHING.  It does not remember the change (using my home net as the test.)

---

### Post by yancek on 2016-10-04
If you are using mkusb, I would suggest you read over in detail the information at it's site below.  Scrolling down toward the bottom of the page you will see an explanation of how to get persistence.

 [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by sudodus on 2016-10-05
See this link for more details,

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by oldsoundguy on 2016-10-05
Think I got it ... does not boot direct, you have to select the persistent from a pop up screen ...  they sure buried that option on the instructions .. I had to search a bunch .. and several times do a complete re-format .. At least I can get it to boot into persistent now!  So MANY thanks to all that jumped in! .. Have not had to go under the hood of Ubuntu for a couple of years, so had to dredge up some old skills ... and they were covered with cobwebs!

---

### Post by sudodus on 2016-10-05
I'm glad it works for you. Congratulations :KS

Please tell us more about the details: which method and tool did you use? And which instructions 'buried' the details about persistence? If you tell us, we have a chance to improve the instructions.

---

### Post by oldsoundguy on 2016-10-05
Well there, folks.  Got a valid install, but the laptop gacks and gags and just does not like working on the HP.  I DID notice there were two different choices as to "type" ... one of them general for large drives and another for "some" HP's.  I chose the general... may re-do and try the HP .. takes time as FORMATTING takes forever and you have to combine the partitions FIRST and re-make it into a single disk!!  The quest continues!!

And the gacking and gagging contiue .. managed to get another drive setup this time using the one for "some HP's".  Both the mouse and the touchpad freeze as far as CLICKING.

Think I am flogging a dead horse!  Wishful thinking that just does not work

BUT .. as to creating a drive .. it just takes a lot of CLOSE and SLOW reading of the gazillion pop up screens. (and a tad of "translating of intent!!"

---

### Post by T2uiYKb7 on 2016-10-05
If it's a fast USB stick I'd boot a second live USB and do a normal install **to** the USB. Get's rid of any possible weirdness and will run like a normal full install **but off your USB.**

---

### Post by oldsoundguy on 2016-10-06
Now, I never thought of trying that!  Will give that a shot .. will need to clear the two 16gb Lexar drives AGAIN!!  Busy schedule tomorrow, so make take a couple of days ..  (as they say .. watch this space........)

---

### Post by sudodus on 2016-10-06
[mkusb makes persistent live drives with an MSDOS partition table for HP computers:](https://help.ubuntu.com/community/mkusb/persistent#Partitions)
> In a separate menu window you can choose between a GUID partition table, GPT, and an old style MSDOS partition table. Normally GPT is recommended (and it works with huge drives (greater than 2 TB), but many HP computers need an MSDOS partition table to boot directly from USB. 


If you want an installed system in your Lexar pendrive, you can try according to the following link,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by oldsoundguy on 2016-10-06
I had the live drive with the MSDOS option on the drive.  It was really dodgy and "little things" like Enter button or mouse click would not work at times .. When I get the time later today (maybe that is IF I get the time) will see if I can get a bootable pen drive with the OS and get it to work.

This is NOT a life changing thing, just that I would like to be able to run Ubuntu on that laptop when I am not using it for Windows.  I need Windows as I have to have .NET to run some programs that I use to refurbish GPS units (a money making hobby ....) and some photography editing programs that have no counterpart in Linux.

AND.... I really DO APPRECIATE all the of the help and suggestions .. as I said earlier, been quite a while since I got under the hood and did something other than just point and click.

---

### Post by sudodus on 2016-10-06
Maybe you have problems with a driver for graphics or wifi in that computer. Please specify the chips for graphics and wifi, and we might be able to help. 

If you need a proprietary driver, you had better use an installed system. Also, only installed systems can upgrade the kernel, so it might be a better alternative than a persistent live system, that is not working properly.

Finally, please remember that you might have problems to boot from USB unless you have an MSDOS partition table in (in some but not all HP computers).

---

### Post by oldsoundguy on 2016-10-06
Well, Well, Well!
I went and got the "pen drive" setup ... IT WORKS and I can modify the OS and THE BUTTONS WORK!!
Have some artifacts on the screen, but I can live with that! but there are some issues!! (not MAJOR .. it WORKS at least without crashing and locking up!

BTW  graphics= NVIDA GeForce 7150M / nForce 630M
WiFi= Atheros AR5007 802.11 b/g
Laptop= HP Pavilion dv9700 Notebook PC Rev1

Ubuntu 16.04 (latest as of today) 64 bit
And set the ram up to 4mb (Windows 7 can only use 3mb, but Ubuntu can use that 4mb)

Added an external BlueTooth receiver as there was no BlueTooth on board  (it works in Windows so should work in Ubuntu.)

I get some time, and I will start to customize Ubuntu

ADDENDUM:  Looks like 16.04 is NOT going to be stable.  Could be a bug or two! May go back and re-do and go for 14.04. PLUS--got a disk warning saying that the system is running out of space.  (on a 16mb drive?)  
But having fun and a lot of old skills are still there .. dormant, but there!

---

### Post by sudodus on 2016-10-06
I have a computer with the ASUS motherboard M2N-VM DVI. It has an onboard graphics chip with a similar model number (I think slightly older than yours),

GeForce 7050 PV / nForce 630a

and all current Ubuntu versions work with it. But I prefer Lubuntu or Xubuntu in that computer in order to get it fast enough. It works with and without a proprietary nvidia driver. I think, but I am not sure, that it should work with your graphics chip too.

I don't know about your wifi chip, but I hope that someone can chip in and help you (no pun intended).

-o-

I'm sure you will find a good configuration - but you might have to play around with different versions and flavours of Ubuntu and tweak the system until you are satisfied. Good luck :-)

---

### Post by oldsoundguy on 2016-11-08
This has been dormant for a while, but need to re-open as STILL having problems getting the USB to work.  Every time I boot from the USB I get the Install or TRY screen.  and little things like MY HOME NETWORK will not install .. have tried three different methods of installing and NOTHING seems to work like the USB is an actual WORKING drive like a hard drive.  I really think I am missing something IMPORTANT in the general "how-to" pages I have tried to utilize.

---

### Post by sudodus on 2016-11-08
When you get the Install or TRY screen, it indicates that it is a live or persistent live system (in contrast to an installed system). If this is not what you want, you should ***install*** the system (like installing to an internal drive but to a USB drive).

-o-

I suggest that you create a ***new thread*** in the [Networking & Wireless forum](https://ubuntuforums.org/forumdisplay.php?f=336) dedicated to the problem with networking.

---

### Post by C.S.Cameron on 2016-11-08
I agree, 16GB is large enough for a Full install.
However if you do want to remove Try/Install on a sylinux boot, (SDC, Unetbootin):

Plug drive into running Linux computer, go to the root folder of your Live or Persistent USB
    Enter the syslinux directory for a SDC install, (or for UNetbootin install the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz.efi
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

For 32bit systems omit ".efi"

My HP EliteBook in not very good at running Ubuntu from pendrive either.
My 120GB USB3 stick boots faster and runs better when stuck into USB2 slot than into USB3 slot on that machine.

---

