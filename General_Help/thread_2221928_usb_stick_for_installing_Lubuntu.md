---
title: "usb stick for installing Lubuntu"
date: 2014-05-04
forum: General Help
---

### Post by Robbyx on 2014-05-04
I have followed the instructions at 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

and put lubuntu onto a usb stick.

I ensured that the boot order included the USB stick in the bios for the Dell GX620.

I created the bootable USB stick on my ubuntu machine and then took the usb stick over to another machine expecting it to boot from the stick so that I can install a new copy of lubuntu on that machine. 

Does anyone know why it fails  to boot from the usb drive and goes on to the HD to boot?

---

### Post by TheFu on 2014-05-04
Not all USB ports are created equal.
Not all flash drives are created equal.
Sometimes the combination of specific usb-port and specific usb-flash drive just doesn't work.

So ... I've had less luck with unetbootin - ended up switching to YUMI (Windows-only) to build multi-boot flash drives. Even then, sometimes a specific flash drive just does not work on a specific computer. Older computers and older flash drives tend to have more issues, but some new flash drives have problems with some computers too.

It doesn't help, but perhaps trying a different flash drive will work?

---

### Post by pfeiffep on 2014-05-04
Not meant to answer, but rather to help TS

Does the stick boot on the machine that created it?
Does the 'other' machine recognize the stick after booting from hdd?
Does the other machine boot to _**any**_ stick?

---

### Post by LastDino on 2014-05-04
Try that with Lili to make bootable USB (I use frigging Micro SD card and cardreader which cost me $ 2 around 3 years ago), is Stick booting in some other machine? I've also found out over the period of time that some machines do better with USB's mounted directly on board rather than the ones which are connected to front panel. So, try different USB ports as well. Also, check if BIOS has actually saved the settings or not, sometimes it doesn't if battery is running low.

---

### Post by stalkingwolf on 2014-05-04
try also using the boot menu.  you should see something when you first start to boot for which key will bring it up.

---

### Post by d.mayfair on 2014-05-04
On one of my computers you can set the boot order in the bios AND bring up a boot order separately. F12 for the boot order and DEL to enter bios

You say you included the usb drive in the boot order.You need to set it 1st,before the hard drive.In some (rare) cases you have to disable the hard drive completely.

---

### Post by Rex Bouwense on 2014-05-04
This may not be the problem, however it will only take a minute or so to check.  Some computers recognize a flash drive as another hard drive so when you insert a bootable flash drive/pen drive/whatever you want to call it into a USB port, it thinks that it is just another hard drive.  Go to the BIOS prior to boot and check if there is a + sign next to your hard drive.  If there is, open it up.  If you see your flash drive, move it to the top, save, exit, and continue with the boot.  No guarantee because I do not know what you are using.

---

### Post by Robbyx on 2014-05-04
I ran the boot menu and found that the USB stick was not showing as an option. I tried the HD diags, rebooted and the USB drive showed up in the boot menu. Ran the option to install and had an error " kernel panic - not syncing VFS: unable to mount  root fs on unknown block (2.0) and when I rebooted the USB would again not be showing.  (I had the same error from trying to run Ub without installing.) 

If I boot in via the HD not the USB stick would I be able to reformat and install Ubuntu from the USB? It will be seen as a drive (although not a boot drive). 

This is  getting difficult because the usb cd gives a fault error and can not read my Ubuntu live CD so i am forced to try the USB stick approach. 

in essence if I can download the ubuntu live CD where can I put it so that i can run it and create  a new installation wiping out the existing one? I propose to reformat the HD but not  before  I know I will not irrecoverably cripple the system.

PS: I have just run the gparted live cd and it has loaded properly.  I am going to try to burn another DVD for the system update and see if it was a fault on the cd instead of the drive. I will post back my findings.

---

### Post by Robbyx on 2014-05-04
The new cd goes wrong half way through the install and stops. It refers to the same error message: 

When I put in the USB stick it is only sometimes recognised. To me it feels like there is no boot area on the stick. Should I have done anything else than install the os via unetbootin? I assumed that it put on its own boot tracks.

I tried again to make the stick the boot device but although it is recognised in the boot menu,  there is no sign of booting which makes me think that there is no boot tracks. is that possible?

---

### Post by radwanski-michal-a on 2014-05-04
If you got Ubuntu (or any quite recent Linux or Unix) you may want to create the Live USB in the easiest way:
```
sudo dd bs=4M if=path/to/ubuntu.iso of=/dev/sd{X} && sync
```
where {X} is your USB key's letter.

---

### Post by Robbyx on 2014-05-05
Radwanski:
Is it possible something is missing from your command line. When I ran it I had a load of input/ output errors and the file names on the stick seem to have control characters in them:


[IMG]http://i.imgur.com/ClOrGVU.jpg[/IMG]

---

### Post by TheFu on 2014-05-05
> **radwanski-michal-a said:**
> If you got Ubuntu (or any quite recent Linux or Unix) you may want to create the Live USB in the easiest way:
```
sudo dd bs=4M if=path/to/ubuntu.iso of=/dev/sd{X} && sync
```
where {X} is your USB key's letter.

This has worked recently for me with 13.10 and 14.04 before.  Just confirming.  Also - DO NOT COPY/PASTE THIS unchanged. The USB device needs to be specific to your system and validated every time the USB drive is plugged in. It can change.

So ... ```
sudo dd bs=4M if=/path/to/ubuntu.iso of=/dev/sdf
``` is what I needed, but unlikely to work for many other people since the USB device will be different. Use **dmesg** to check that.

@Robbyx - please post the EXACT command you tried.

---

### Post by Robbyx on 2014-05-05
dmesg shows:

> [ 7370.912800] usb 1-1: New USB device found, idVendor=abcd, idProduct=1234
[ 7370.912803] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7370.912807] usb 1-1: Product: UDisk           
[ 7370.912809] usb 1-1: Manufacturer: General 
[ 7370.912812] usb 1-1: SerialNumber: 0701080210071837109307
[ 7370.913247] scsi12 : usb-storage 1-1:1.0
[ 7371.912449] scsi 12:0:0:0: Direct-Access     General  UDisk            5.00 PQ: 0 ANSI: 2
[ 7371.913155] sd 12:0:0:0: Attached scsi generic sg2 type 0
[ 7371.916687] sd 12:0:0:0: [sdb] 1967680 512-byte logical blocks: (1.00 GB/960 MiB)
[ 7371.917306] sd 12:0:0:0: [sdb] Write Protect is off
[ 7371.917310] sd 12:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 7371.917930] sd 12:0:0:0: [sdb] No Caching mode page found
[ 7371.917934] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 7371.920558] sd 12:0:0:0: [sdb] No Caching mode page found
[ 7371.920562] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 7371.921320]  sdb: sdb1
[ 7371.924931] sd 12:0:0:0: [sdb] No Caching mode page found
[ 7371.924935] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 7371.924939] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[ 7599.810482] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7599.810487] FAT-fs (sdb1): Filesystem has been set read-only
[ 7601.966642] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7603.581238] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7604.216720] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7606.958920] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7608.706849] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7609.544750] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7610.103452] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7611.412771] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7612.677068] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7613.473700] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7614.112679] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7618.013408] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7620.488328] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7621.317119] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[ 7622.135959] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain 

---

### Post by TheFu on 2014-05-05
What command did you do with dd, exactly?

Should have been;```

sudo dd bs=4M if=/path/to/ubuntu.iso of=/dev/sdb
``` ... with the path to the ISO file modified for your system.

---

### Post by sudodus on 2014-05-05
There might be several causes for your problems. Maybe the following links will help you test various solutions to find something that works.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)
[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

-o-

Flashing an Ubuntu iso file into a USB pendrive with ***dd*** is likely to work, but it is risky. dd is nick-named 'disk destroyer' because it does what you tell it to do without questions, and if you get a single letter wrong you might overwrite a drive with valuable data. I made a shell-script ***mkusb*** to help making the operation safe (help selecting the correct target drive). See this link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

