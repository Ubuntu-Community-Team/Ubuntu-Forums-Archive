---
title: "Clear existing files from USB"
date: 2015-02-27
forum: General Help
---

### Post by jones5 on 2015-02-27
I  have been trying out Elementary OS on a pendrive USB.  I now wish to clean it off  and put an Ubuntu trial on the USB but am finding it impossible to clear the Elementary from the pen drive.

Tried the usual reformat drive E option in windows and HP Disk storage format tool.

Any siuggestions?

---

### Post by sffvba[e0rt on 2015-02-27
Depending on how you plan to write the new ISO file to the USB you don't need to first remove what ever is on the drive.  However you can use the steps[ in this tutorial]("http://www.passmark.com/forum/showthread.php?4508-Reclaim-disk-space-after-imaging-with-imageUSB") to get your USB reformatted to the correct size ready for you to use.

---

### Post by Elfy on 2015-02-27
*Thread moved to **General Help**.*

---

### Post by jones5 on 2015-02-27
Ok thanks for the quick reply. 

I used your tutorial to make sure the USB drive was reformatted and empty. I checked on properties and the whole USB drive was empty and FAT32. After loading up the ISO image with a persistent partition and all seemed to go as it should, on running the USb drive it still loads Elementary?? I just cannot understand how it is remaining on the USB?

 I am using the following technique to try and load up a persistent version of Ubuntu onto this USB drive (2GB). [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu). 

I have trial Ubuntu (not persistent) on another USB which I am running and using its disk creator to make the persistent version USB which keeps loading elementary OS.

What am I doing wrong?

---

### Post by jones5 on 2015-03-01
[FONT=Verdana]I have come across this thread [http://www.tomshardware.co.uk/answers/id-1916525/removing-write-protection-bootable-flash-drive.html#xtor=EPR-8809](http://www.tomshardware.co.uk/answers/id-1916525/removing-write-protection-bootable-flash-drive.html#xtor=EPR-8809) [/FONT][FONT=Verdana]that is relevant to the above problem about not being to be able to return a USB drive to its original state after loading a linux iso to try it out, in this case Elementary. The above article suggests it is common that USB drives are effectively stuck with the live linux os once it is loaded. Can anyone here confirm this? If true it should be made crytsal clear on Ubuntu and Elementary  instructions (and other Linux try out live ISO's to be used with USB drives). Otherwise I and others will be sacrificing relatively expensive USB drive sticks simply for the privilege of trying Linux. I cannot believe this was intended by the usually helpful Linux fraternity. There does seem to be silence over this? I can only assume the USb drives are really ruined if trying Linux. I hope not.[/FONT]

---

### Post by NM5TF on 2015-03-01
uhhhhhhh....no USB drive should ever be "ruined" by loading a *nix distro on it....

I have a SANDisk 16GB drive that I have loaded/erased 5-6 different Linux distros on it with
no problems.....and I just loaded it with some bash files & read them correctly....

[COLOR="#FF0000"]to erase a USB drive I use GParted to [COLOR="#0000FF"]format[/COLOR] the stick to FAT32 so it can load basically
any OS.....[/COLOR]

GParted should be available from your running live stick.....

never had any luck using the "disk creator" that is built-in....I have never had any problems
using [COLOR="#FF0000"]UNetbootin[/COLOR] to load the iso image & booting from that....

you might try formatting the USB stick first and then load the iso using UNetbootin...

good luck...

tommy

---

### Post by jones5 on 2015-03-04
First apologies to those who have read and contribued. I have figured out (doh) that I was reloading the elementary os onto my USB stick instead of the  ubuntu iso. They (both elementary and Uuntu ISO were in the same file but were not clearly identified. Therefore I jumped to the (wrong) conclusion that the elementary OS was not being wiped. I was accidentally reloading it and not the Ubuntu ISO. We all learn as we go on - I hope. I have kept the Ubuntu but also liked the Elementary. Ubuntu seems to have the edge. I now have a persistent version of Ubuntu  on a USB stick. Very neat and I can keep settings etc. Next I will try out the whole OS and may try to load Ubuntu onto the netbook hardrive along with Windows. I will open a new thread about whether this install will retain the settings I have made in the persistent mode?

---

