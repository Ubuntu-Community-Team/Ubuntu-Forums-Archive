---
title: "[SOLVED] I think I am Ready to Go ALL OUT with Ubuntu"
date: 2007-08-03
forum: General Help
---

### Post by Xomphos on 2007-08-03
Hi,

I have been messing with Linux and various distros for around three years. I am an avid XP user and have come to like Ubuntu. However, with both my desktop and laptop computer, it always seems to come down to the wireless card which makes me revert back to Windows. I think I want Ubuntu to be my main OS on my old laptop computer now. I really like it, but it is my wireless card that doesn't work. It is a Microsoft MN-720 wireless notebook adapter and I got it to work with ndiswrapper, but then I would reboot and after trying many things it wouldn't work ever again until I reinstalled Ubuntu. I think I want to go and buy a wireless card that works "plug and play" but I don't know which one to get. Can someone please tell me a wireless card for my laptop that is readily available in retail stores and that works off the bat without having to screw around getting it to work?

For the record, here are my specs:
-Manufacturer: Dell
-Model: Inspiron 4150
-30GB HDD
-1.60 gHz Intel Pentium 4 M Processor
-256mb ram
-ATI Radion 7500 M with 16mb Video Ram (can't get this to work with 3D -example: Tremulous doesn't load-any advice?)
-OS: Ubuntu 7.04 with available updates

So, what is a good wireless card that is affordable, readily available and that will work with no hassle? And as a side note, can I do anything about my graphics card?

Thanks! :D

_____________________

Edit:

Anyways, just incase someone knows what is wrong with my wireless card so I don't have to buy a new one, this is what I am getting in terminal:

michael@michaellaptop:~$ ndiswrapper -l
mn720-ankh : driver installed
        device (14E4:4325) present (alternate driver: bcm43xx)
michael@michaellaptop:~$ sudo depmod -a
michael@michaellaptop:~$ sudo modprobe ndiswrapper
michael@michaellaptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

michael@michaellaptop:~$ ndiswrapper -l
mn720-ankh : driver installed
        device (14E4:4325) present (alternate driver: bcm43xx)
michael@michaellaptop:~$ 

Any suggestions? Thanks! :D
________________________________

This was just posted:

> **dougfractal said:**
> **wifi**
did you blacklist the broadcom driver?
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
for more about ndiswrapper
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

**3D**
but from
[http://ubuntuforums.org/archive/index.php/t-32015.html](http://ubuntuforums.org/archive/index.php/t-32015.html)

Wow, thanks, I did that with my wireless card unplugged and then restarted and plugged it in and it still wouldn't work. The end of the blacklist file says:

> # buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
blacklist bcm43xx

It still doesn't work though. It still gives the same thing when I gave the ndiswrapper -l command. Additionally, under the Windows Network Drivers ndiswrapper gui, it shows a network logo WHEN I have my card plugged in, but says:

Hardware Present: No

I feel really close to getting this to work. Like I said, the first time until I rebooted, it worked great. Thanks for your help on this. :D

Also with the graphics card I don't get what you mean by changing those options and restarting the x server. I have been messing around with Linux for around three years, but I am sadly not as knowledgable as I wish I could be, mainly because I haven't gotten my wireless to work.

Thanks! :D

---

### Post by Swarms on 2007-08-03
With no clue what is good, though I looked at my card which works on Ubuntu 100%

Manufactorer: Planet *Networking and Communication*
Model No.: WL-3560

Then you can do the rest. :)

---

### Post by Xomphos on 2007-08-03
Thanks, but I have never heard of that card before. If I find it, I'll know it works. Thanks though!

Anyways, just incase someone knows what is wrong with my wireless card so I don't have to buy a new one, this is what I am getting in terminal:

michael@michaellaptop:~$ ndiswrapper -l
mn720-ankh : driver installed
        device (14E4:4325) present (alternate driver: bcm43xx)
michael@michaellaptop:~$ sudo depmod -a
michael@michaellaptop:~$ sudo modprobe ndiswrapper
michael@michaellaptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

michael@michaellaptop:~$ ndiswrapper -l
mn720-ankh : driver installed
        device (14E4:4325) present (alternate driver: bcm43xx)
michael@michaellaptop:~$ 

Any suggestions? Thanks! :D

---

### Post by dougfractal on 2007-08-03
**wifi**
did you blacklist the broadcom driver?
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
for more about ndiswrapper
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

**3D**
but from
[http://ubuntuforums.org/archive/index.php/t-32015.html](http://ubuntuforums.org/archive/index.php/t-32015.html)
> Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
Driver "radeon"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "True"
Option "UseInternalAGPGART" "no"
Option "backingstore" "true"
Option "AllowGLXWithComposite" "true"
EndSection

I restarted the X server by pressing Ctl+Alt+Backspace, and then when it restarted, I now have 1300+ FPS in glxgears

---

### Post by ReaderRat on 2007-08-03
[**[COLOR="Red"]Wifi Cards Supported[/COLOR]**](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by maniacmusician on 2007-08-03
> **dougfractal said:**
> **wifi**
did you blacklist the broadcom driver?
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
]

This should do it. I always have to do this with my broadcom cards.

---

### Post by TravMan63 on 2007-08-03
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320105](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320105)

I have that card with ubuntu 7.04, and I purchased it there (it's a great store - I've purchased 'lots')

check out the other user reviews as well - Gentoo, Ubuntu, PCLinux OS, Puppy...

plug it in ....

maybe edit 
/etc/network/interfaces
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto ra0
iface ra0 inet dhcp
wireless-essid name here if needed
wireless-key your key here

iface eth0 inet dhcp

auto eth0
```

Dell C-840 Latitude
2GHz, 1GB, 80GB, Nvidia4 Go 440

---

### Post by Xomphos on 2007-08-03
> **dougfractal said:**
> **wifi**
did you blacklist the broadcom driver?
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
for more about ndiswrapper
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

**3D**
but from
[http://ubuntuforums.org/archive/index.php/t-32015.html](http://ubuntuforums.org/archive/index.php/t-32015.html)

Wow, thanks, I did that with my wireless card unplugged and then restarted and plugged it in and it still wouldn't work. The end of the blacklist file says:

> # buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
blacklist bcm43xx

It still doesn't work though. It still gives the same thing when I gave the ndiswrapper -l command. Additionally, under the Windows Network Drivers ndiswrapper gui, it shows a network logo WHEN I have my card plugged in, but says:

Hardware Present: No

I feel really close to getting this to work. Like I said, the first time until I rebooted, it worked great. Thanks for your help on this. :D

Also with the graphics card I don't get what you mean by changing those options and restarting the x server. I have been messing around with Linux for around three years, but I am sadly not as knowledgable as I wish I could be, mainly because I haven't gotten my wireless to work.

Thanks! :D

---

### Post by Xomphos on 2007-08-03
bump

---

### Post by HermanAB on 2007-08-04
In my experience, always keep the original WiFi adaptor Windoze driver handy for use with ndiswrapper.  There are many WiFi devices that work with Linux, but they don't seem to be in any of the shops where I live...

---

### Post by Xomphos on 2007-08-04
> **HermanAB said:**
> In my experience, always keep the original WiFi adaptor Windoze driver handy for use with ndiswrapper.  There are many WiFi devices that work with Linux, but they don't seem to be in any of the shops where I live...

Yeah, I orignally used the windows drivers in an old installation, but in this one used custom ones from ndiswrappers site and they work.

Thanks! :D

---

### Post by ugm6hr on 2007-08-04
If you want a new wifi card - it will be sleeker to get an internal one.  This is how to replace it:

[http://support.dell.com/support/edocs/systems/ins4150/en/sm_en/upgrades.htm#1084976](http://support.dell.com/support/edocs/systems/ins4150/en/sm_en/upgrades.htm#1084976)

Just look for a mini-PCI wifi card with a spported chipset (most, but not all Atheros & Intel).

Here's a UK example:
[http://www.ebuyer.com/UK/product/110375](http://www.ebuyer.com/UK/product/110375)

If you want to find a Broadcom solution - let us know exactly which BCM card you have:```
lspci -nn
```

---

### Post by dougfractal on 2007-08-04
> but in this one used custom ones from ndiswrappers site and they work.
Thanks! Xomphos

So is wifi sorted?

> graphics card I don't get what you mean by changing those options and restarting the x server

from [http://ubuntuforums.org/archive/index.php/t-32015.html](http://ubuntuforums.org/archive/index.php/t-32015.html)

backup
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
```

so ```
sudo gedit /etc/X11/xorg.conf
```
change the Section "Device" 
```
Section "Device"
Identifier "Radeon Mobility 7500"
Boardname "ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
VendorName "ATI Technologies"
Driver "radeon"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "True"
Option "UseInternalAGPGART" "no"
Option "backingstore" "true"
Option "AllowGLXWithComposite" "true"
EndSection
```

in Section "Screen"
change Device "Radeon Mobility 7500"


Do only if you need to

you may need to also add DRI and Composite section
```
Section "DRI"
        Group        0
        Mode         0666
EndSection
```

in Section "Module"
```
load "dri"
```

```
Section "Extensions"
Option "Composite" "0"
EndSection
```

---

### Post by Xomphos on 2007-08-04
> **dougfractal said:**
> Xomphos

So is wifi sorted?



from [http://ubuntuforums.org/archive/index.php/t-32015.html](http://ubuntuforums.org/archive/index.php/t-32015.html)

backup
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
```

so ```
sudo gedit /etc/X11/xorg.conf
```
change the Section "Device" 
```
Section "Device"
Identifier "Radeon Mobility 7500"
Boardname "ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
Vendor "ATI Technologies"
Driver "radeon"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "True"
Option "UseInternalAGPGART" "no"
Option "backingstore" "true"
Option "AllowGLXWithComposite" "true"
EndSection
```

in Section "Screen"
change Device "Radeon Mobility 7500"


Do only if you need to

you may need to also add DRI and Composite section
```
Section "DRI"
        Group        0
        Mode         0666
EndSection
```

in Section "Module"
```
load "dri"
```

```
Section "Extensions"
Option "Composite" "0"
EndSection
```

Thanks, but what do you mean by my wifi is sorted? I just got this custom driver:

[http://ankhcraft.com/drivers/mn720-ankh.zip](http://ankhcraft.com/drivers/mn720-ankh.zip)

from this page:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

Now, I tried the graphics thing and I couldn't back it up because there was no directory it said, so instead I just created a copy and placed it in a folder in my home folder. Then, I went ahead and changed settings up to changing the device in screen. Then I restarted the X Server by pressing ctrl-alt-backspace and I lost my graphics/desktop and got a weird BSOD style of error. The biggest thing I noticed was that it said Vendor wasn't an appropriate variable or something. Additionally, when I restart, I am now in command-line only!

Is it possible to fix both these problems without re-installing now?

Thanks! :D

---

### Post by ugm6hr on 2007-08-04
> **Xomphos said:**
> Thanks, but what do you mean by my wifi is sorted? I just got this custom driver:

[http://ankhcraft.com/drivers/mn720-ankh.zip](http://ankhcraft.com/drivers/mn720-ankh.zip)

from this page:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

Now, I tried the graphics thing and I couldn't back it up because there was no directory it said, so instead I just created a copy and placed it in a folder in my home folder. Then, I went ahead and changed settings up to changing the device in screen. Then I restarted the X Server by pressing ctrl-alt-backspace and I lost my graphics/desktop and got a weird BSOD style of error. The biggest thing I noticed was that it said Vendor wasn't an appropriate variable or something. Additionally, when I restart, I am now in command-line only!


He was asking **if** wifi was sorted... Clearly not.  Maybe try to fix one thing at a time, eh?

As for returning your desktop to prior status - that's what the backup is for.  You will need to know the full path and name of the backup file though (and insert it into the command below).

```
sudo rm /etc/X11/xorg.conf
sudo cp /home/*user/backup-filename.whatever* /etc/X11/xorg.conf
sudo poweroff
```

This should turn it all off - and when you reboot, it should work (hopefully).

---

### Post by Xomphos on 2007-08-04
> **ugm6hr said:**
> He was asking **if** wifi was sorted... Clearly not.  Maybe try to fix one thing at a time, eh?

As for returning your desktop to prior status - that's what the backup is for.  You will need to know the full path and name of the backup file though (and insert it into the command below).

```
sudo rm /etc/X11/xorg.conf
sudo cp /home/*user/backup-filename.whatever* /etc/X11/xorg.conf
sudo poweroff
```

This should turn it all off - and when you reboot, it should work (hopefully).

Awesome, it worked! Thanks! :D 

Anyways, for wifi, I honestly don't know what the term, "sorted" means. Any suggestions?

Also, with the graphics, any idea what could have caused my problem?

Thanks! :D

---

### Post by ugm6hr on 2007-08-04
> **Xomphos said:**
> Awesome, it worked! Thanks! :D 

Anyways, for wifi, I honestly don't know what the term, "sorted" means. Any suggestions?

Also, with the graphics, any idea what could have caused my problem?

Thanks! :D

Ah - language barrier.  For *sorted* read *resolved/fixed*.  So the answer is no.

I have no idea about the graphics card, I'm afraid.

I am a bit of a beginner myself - and have only really had experience with my own setups (2 laptops so far).

I will try and help with wifi though:

As I stated earlier - if you want to just get a new internal mini-PCI card (which is what you initially suggested) - then try the Intel one I linked to earlier.  Dells are compatible with any generic mini-PCI - so there should be no issue with it, and the Intel 3945 is pretty well supported in Ubuntu (although uninterrupted WPA sometimes needs Wicd instead of Network Manager).

From your earlier post - I gather your current card is listed as pciid 14e4:4325 and Chipset: Broadcom 43xG when you enter:
```
lspci -nn
```
Have to say, I'm a bit surprised that Dell have used a Microsoft branded card in their laptop...  But if that's true - it looks like you *might* get it to work - but it doesn't look straightforward.  Just follow one of the multitude of ndiswrapper how-tos in the Ubuntu wiki.  If *lspci* lists something else - just post it here for further advice.

EDIT: I have jusr re-read your original post - and realised that the wifi card is external - and not a Dell original - which makes sense now.  The wiki dougfractal pointed you to should sort it out if you have had it working before, and to make sure it works each time you reboot: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de)

---

### Post by dougfractal on 2007-08-04
> Anyways, for wifi, I honestly don't know what the term, "sorted" means. Any suggestions?
slang for installed and working?
> 
Also, with the graphics, any idea what could have caused my problem?
Sorry about the BSOD.  I should have warned you better. Well done for finding the backup.

Tips
```
sudo poweroff   
sudo reboot
sudo /etc/init.d/gdm restart     # just restart X

sudo nano /etc/X11/xorg.conf   # text edit xorg.conf
```

If you have edited this file but would like it to be automatically updated again, run the following command:
  ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

The answer for 3D for you is by using the code from the above post.
also read a guide, although being a surviver of having no X, means that you know how to get X back.

check this it could  the be  log file of  xorg
```
cat /var/log/Xorg.0.log.old | grep "(EE)"
```

It's likely that the Identifier names didn't match.

post your xorg.conf and the log (to the broken X) Then I can take a look  .
from BSOD ```
cp /var/log/Xorg.0.log ~/Xorg.0.log.broken
```

---

### Post by Xomphos on 2007-08-04
> **ugm6hr said:**
> Ah - language barrier.  For *sorted* read *resolved/fixed*.  So the answer is no.

I have no idea about the graphics card, I'm afraid.

I am a bit of a beginner myself - and have only really had experience with my own setups (2 laptops so far).

I will try and help with wifi though:

As I stated earlier - if you want to just get a new internal mini-PCI card (which is what you initially suggested) - then try the Intel one I linked to earlier.  Dells are compatible with any generic mini-PCI - so there should be no issue with it, and the Intel 3945 is pretty well supported in Ubuntu (although uninterrupted WPA sometimes needs Wicd instead of Network Manager).

From your earlier post - I gather your current card is listed as pciid 14e4:4325 and Chipset: Broadcom 43xG when you enter:
```
lspci -nn
```
Have to say, I'm a bit surprised that Dell have used a Microsoft branded card in their laptop...  But if that's true - it looks like you *might* get it to work - but it doesn't look straightforward.  Just follow one of the multitude of ndiswrapper how-tos in the Ubuntu wiki.  If *lspci* lists something else - just post it here for further advice.

The Intel 3945 looks like a great purchase for me, however, I can't seem to find a reliable US retailer. 

Also, here s what got spit out when I entered that code:

> michael@michaellaptop:~$ lspci -nm
00:00.0 "0600" "8086" "1a30" -r04 "" ""
00:01.0 "0604" "8086" "1a31" -r04 "" ""
00:1d.0 "0c03" "8086" "2482" -r02 "8086" "4541"
00:1e.0 "0604" "8086" "2448" -r42 "" ""
00:1f.0 "0601" "8086" "248c" -r02 "" ""
00:1f.1 "0101" "8086" "248a" -r02 -p8a "8086" "4541"
00:1f.5 "0401" "8086" "2485" -r02 "1013" "5959"
00:1f.6 "0703" "8086" "2486" -r02 "14f1" "5421"
01:00.0 "0300" "1002" "4c57" "1028" "012b"
02:00.0 "0200" "10b7" "9200" -r78 "1028" "012a"
02:01.0 "0607" "104c" "ac51" "1028" "012b"
02:01.1 "0607" "104c" "ac51" "1028" "012b"
07:00.0 "0280" "14e4" "4325" -r02 "1414" "0003"

I really don't know what I can do. I mean, that internal card looks nice (it'll free up a card slot for USB 2.0 :)), but the thing is, my external card did WORK the first time I plugged it in. Knowing that, I know it can work, because it did. Suggestions?

Edit: 

I'm sorry, I accidently entered the wrong command, here is the correct one:

> michael@michaellaptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #1) [8086:2482] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
02:01.1 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
07:00.0 Network controller [0280]: Broadcom Corporation BCM43xG 802.11b/g [14e4:4325] (rev 02)
michael@michaellaptop:~$ 



Thanks! :D

---

### Post by Xomphos on 2007-08-04
> **dougfractal said:**
> slang for installed and working?

Sorry about the BSOD.  I should have warned you better. Well done for finding the backup.

Tips
```
sudo poweroff   
sudo reboot
sudo /etc/init.d/gdm restart     # just restart X

sudo nano /etc/X11/xorg.conf   # text edit xorg.conf
```

If you have edited this file but would like it to be automatically updated again, run the following command:
  ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

The answer for 3D for you is by using the code from the above post.
also read a guide, although being a surviver of having no X, means that you know how to get X back.

check this it could  the be  log file of  xorg
```
cat /var/log/Xorg.0.log.old | grep "(EE)"
```

It's likely that the monitor's names didn't match.

post your xorg.conf and the log (to the broken X) Then I can take a look  .
from BSOD ```
cp /var/log/Xorg.0.log ~/Xorg.0.log.broken
```

First, yeah, from my other recent post, the wireless still isn't working. Suggestions?

Also, here is what I got:

> michael@michaellaptop:~$ cat /var/log/Xorg.O.log.old | grep "(EE)"
cat: /var/log/Xorg.O.log.old: No such file or directory
michael@michaellaptop:~$ cat /var/log/Xorg.0.log.old | grep "(EE)"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 17325 kB of video memory needed at this resolution and depth.
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
michael@michaellaptop:~$ cp /var/log/Xorg.O.log -/Xorg.O.log.broken
cp: invalid option -- /
Try `cp --help' for more information.
michael@michaellaptop:~$ 

And the .conf file:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


Suggestions?

Thanks! :D

---

### Post by dougfractal on 2007-08-04
> (EE) RADEON(0): Static buffer allocation failed. Disabling DRI.
(EE) RADEON(0): At least 17325 kB of video memory needed at this resolution and depth.
(EE) AIGLX: Screen 0 is not DRI capable

meaning not enough memory to run 3D.

so change in the Section "Screen"  > DefaultDepth 16

---

### Post by Xomphos on 2007-08-04
> **dougfractal said:**
> meaning not enough memory to run 3D.

so change in the Section "Screen"

Thanks, so before I proceed, this should pretty much be the EXACT changes I need to make to the conf. file?

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Radeon Mobility 7500"
Boardname "ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
Vendor "ATI Technologies"
Driver "radeon"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "True"
Option "UseInternalAGPGART" "no"
Option "backingstore" "true"
Option "AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Radeon Mobility 7500"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1400x1050"
EndSubSection
SubSection "Display"
Depth 4
Modes "1400x1050"
EndSubSection
SubSection "Display"
Depth 8
Modes "1400x1050"
EndSubSection
SubSection "Display"
Depth 15
Modes "1400x1050"
EndSubSection
SubSection "Display"
Depth 16
Modes "1400x1050"
EndSubSection
SubSection "Display"
Depth 24
Modes "1400x1050"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

Also, anything on wifi?

Thanks! :D

---

### Post by dougfractal on 2007-08-04
xorg.conf looks good. I wish you luck

Hold this space for wifi .....

These thread may help
[http://ubuntuforums.org/showthread.php?t=234053](http://ubuntuforums.org/showthread.php?t=234053)
bcm43xx-fwcutter isnt working??

try this howto thread
[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

---

### Post by ugm6hr on 2007-08-04
For your wifi - you may not need ndiswrapper at all:
[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices) lists your card as supported by fwcutter.

If you want to give it a try - it is *supposed* to be very easy:
*Unblacklist* bcm43xx by putting a "#" (without the "") in front of the relevant line at the bottom:
```
gksudo gedit /etc/modprobe.d/blacklist
```

Then follow this: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) (basically - download, extract, double-click).

That should just get it working with no further trouble (in theory).

---

### Post by Xomphos on 2007-08-04
> **ugm6hr said:**
> For your wifi - you may not need ndiswrapper at all:
[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices) lists your card as supported by fwcutter.

If you want to give it a try - it is *supposed* to be very easy:
*Unblacklist* bcm43xx by putting a "#" (without the "") in front of the relevant line at the bottom:
```
gksudo gedit /etc/modprobe.d/blacklist
```

Then follow this: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) (basically - download, extract, double-click).

That should just get it working with no further trouble (in theory).

WOW. THAT WORKED! :D :D :D :D :D 

Thank-you so much. Right now, I have wireless finally working and am typing from my laptop! Thanks for your help and everyone else who helped! :D

-------------------------------------------------------

Also, with the graphics card, I changed the .conf file again to what I posted, and again, got that BSOD thing and again had to copy back the old .conf file. The BSOD thing keeps saying that 'Vendor' isn't an appropriate variable or something. Suggestions?

Thanks! :D

---

### Post by dougfractal on 2007-08-04
Sorry my mistake.

"Vendor"  should have read "VendorName"


```
Section "Device"
Identifier "Radeon Mobility 7500"
Boardname "ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
VendorName "ATI Technologies"
Driver "radeon"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "True"
Option "UseInternalAGPGART" "no"
Option "backingstore" "true"
Option "AllowGLXWithComposite" "true"
EndSection
```


Almost there ;-)

---

### Post by ugm6hr on 2007-08-04
> **Xomphos said:**
> WOW. THAT WORKED! :D :D :D :D :D 

Thank-you so much. Right now, I have wireless finally working and am typing from my laptop! Thanks for your help and everyone else who helped! :D


Glad that's sorted :guitar:

Perhaps when you've fixed xorg.conf - uou might like to post it on my thread linked from my signature below?

---

### Post by Xomphos on 2007-08-04
> **dougfractal said:**
> Sorry my mistake.

"Vendor"  should have read "VendorName"


```
Section "Device"
Identifier "Radeon Mobility 7500"
Boardname "ATI Technologies, Inc. Radeon Mobility 7500 (M7 LW)"
VendorName "ATI Technologies"
Driver "radeon"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "True"
Option "UseInternalAGPGART" "no"
Option "backingstore" "true"
Option "AllowGLXWithComposite" "true"
EndSection
```


Almost there ;-)

WOW. That worked too! I'm now getting like 1400fps in glxgears! Thank you to you and everyone who persisted with helping me fix these problems. I am pretty certain I will now be staying with Ubuntu for more than a few days now. Thank you so much for helping. I really appreciate it! :D

---

