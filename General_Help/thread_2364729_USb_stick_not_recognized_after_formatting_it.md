---
title: "USb stick not recognized after formatting it"
date: 2017-06-27
forum: General Help
---

### Post by swenray on 2017-06-27
Hello, i'm swenray, 

yesterday I tried to copy on my Lacie usb stick (not external HD ) a bunch of video files, as it didn't work I tried to compress those files and to be sure I had enough space I formated it. 

Unsuccessfully my USB wasn't recognized on screen anymore.Therefore I post here my first thread, hoping not to disturb any of you,  and of course hoping twice so hard that I'll have a little answer to  start my investigation why it doesn't work.

SO I knew ONE thing ! this code to run as for knowing what is connected to my laptop , there it goes : 

```
sudo lsusb
```

and gives me this 

```
bronz@Swen-rage:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 011: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102/2.0 / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 007: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

As : bus 001 device 11 (toshiba) is the usb stick. 

 [ logitech is my wireless mouse ; terminus technology is a usb hub (4 ports available) because I only have one left on my laptop... don't know for the other ones ]

AND SO : 

I went to see this other thread : 
[https://ubuntuforums.org/showthread.php?t=2271595]("http://https://ubuntuforums.org/showthread.php?t=2271595")

 that have been closed and they told to run : 

```
sudo fdisk -l
```

it gives me : 
```

bronz@Swen-rage:~$ sudo fdisk -l
[sudo] Mot de passe de bronz : 
Disque /dev/sda : 111,8 GiB, 120034123776 octets, 234441648 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x918388d7

Périphérique Amorçage     Start       Fin  Secteurs   Size Id Type
/dev/sda1    *             2048 230389759 230387712 109,9G 83 Linux
/dev/sda2             230391806 234440703   4048898     2G  5 Étendue
/dev/sda5             230391808 234440703   4048896     2G 82 partition d'échang




Disque /dev/sdb : 14,6 GiB, 15610576896 octets, 30489408 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc3072e18

Périphérique Amorçage Start      Fin Secteurs  Size Id Type
/dev/sdb1    *         8064 30489407 30481344 14,5G  7 HPFS/NTFS/exFAT
```

As where my usb is disque /dev/sdb ...


So I hope this helps you to understand my problem, and maybe you guys have an idea about it...

Best regards, and have a nice day ! ! 

M-sr

---

### Post by ajgreeny on 2017-06-27
Assuming the USB disk is seen in gparted, which you can either install to any of the *ubuntu family or use from one of the *ubuntu live OSs, try using **Device ->Create partition table** to make a new filesystem on the USB, then once you have that you can format the now unallocated space to fat32 or whatever filesystem type you wish to use.

Don't forget that as the files you want to put on it are videos, there is a relatively small file size maximum that fat32 can write, which I believe is 4GB, so if you have some huge files you may need to consider ntfs if the files need to be read by Windows machines, or ext# if only Linux is to use them.

---

### Post by swenray on 2017-07-01
Hooo, well. Sorry for the long no responds ajgreeny . 

So I tryied, and it wooorked !! So much thanks to you. Only thing that isn't quite my problem, but the fact is I used the USB to transfer the files on a MAC.

 I formated the files to NTFS, which is "readonly" for Mac, because HFS+ wasn't available...  [https://www.howtogeek.com/73178/what-file-system-should-i-use-for-my-usb-drive/](https://www.howtogeek.com/73178/what-file-system-should-i-use-for-my-usb-drive/) 

Again : THANK YOU AJGREENY :guitar: and a nice day to you

---

### Post by HermanAB on 2017-07-01
NTFS RW support is available on a Mac, but you got to mount it manually:
[http://www.aeronetworks.ca/2014/11/apple-mac-ntfs-readwrite-support.html](http://www.aeronetworks.ca/2014/11/apple-mac-ntfs-readwrite-support.html)

---

