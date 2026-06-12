---
title: "[SOLVED] fstab"
date: 2007-09-04
forum: General Help
---

### Post by Ripfox on 2007-09-04
How do I add my usb mp3 player to fstab on my gfs lappy? Sorry, I haven't tackled this configuration file as of yet :)

---

### Post by strabes on 2007-09-04
Are they not mounted automatically when you plug them in? If not, you can run ```
blkid
``` to find the uuid of your mp3 player's partition when it is plugged in. Using this uuid, you can add a line into your /etc/fstab file that looks similar to this:```
UUID=3bdb46de-2464-458b-b93e-243c9a1b3ff8 /media/MYMP3PLAYER vfat defaults 0 2
```

I'm not 100% sure on that line, hopefully someone more knowledgeable will correct me if I'm wrong.

You'll need to create the directory that you specified, using the following command:```
sudo mkdir /media/MYMP3PLAYER
```

---

### Post by Ripfox on 2007-09-04
oh wow...ok so i'm trying it now ill be right back.

---

### Post by Ripfox on 2007-09-07
Ok so blkid only shows my hdd, not the mp3 player :(

blkid:

/dev/sda1: UUID="22a62687-35b6-4a3f-891e-f7f939ea7f54" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="3a450987-ef98-4551-b08d-98a714d11cae" TYPE="swap" 

lsusb shows: 

Bus 005 Device 003: ID 10d6:2200 Actions Semiconductor Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000

---

### Post by yabbadabbadont on 2007-09-07
What does this output?
```
dmesg | grep -i usb
```

---

### Post by Ripfox on 2007-09-08
dmesg | grep -i usb
[    3.696000] usbcore: registered new interface driver usbfs
[    3.696000] usbcore: registered new interface driver hub
[    3.696000] usbcore: registered new device driver usb
[    3.724000] USB Universal Host Controller Interface driver v3.0
[    3.724000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.724000] usb usb1: configuration #1 chosen from 1 choice
[    3.724000] hub 1-0:1.0: USB hub found
[    3.828000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.828000] usb usb2: configuration #1 chosen from 1 choice
[    3.828000] hub 2-0:1.0: USB hub found
[    3.932000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.932000] usb usb3: configuration #1 chosen from 1 choice
[    3.932000] hub 3-0:1.0: USB hub found
[    4.036000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.036000] usb usb4: configuration #1 chosen from 1 choice
[    4.036000] hub 4-0:1.0: USB hub found
[    7.092000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    7.096000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.096000] usb usb5: configuration #1 chosen from 1 choice
[    7.096000] hub 5-0:1.0: USB hub found
[   24.592000] usbcore: registered new interface driver ndiswrapper
[ 9154.912000] usb 5-2: new high speed USB device using ehci_hcd and address 2
[ 9155.048000] usb 5-2: config 1 interface 0 altsetting 0 endpoint 0x83 has an invalid bInterval 200, changing to 9
[ 9155.048000] usb 5-2: configuration #1 chosen from 1 choice
[ 9155.260000] usbcore: registered new interface driver libusual

---

### Post by Ripfox on 2007-09-08
bump

---

### Post by Jose Catre-Vandis on 2007-09-08
Doesn't look like your mp3 player is being spotted by Ubuntu (normally you should get a nautilus window open up when you plug it in), unless it is the "Actions Semiconductor". Do you have any other usb devices connected? Have you tried connecting the mp3 player to all/any of your usb ports? Is the mp3 player switched on? Have you tried connecting when laptop is on, and before booting up? Are your usb ports all activated (looks like it)?

---

### Post by Ripfox on 2007-09-09
It is in fact the "actions semiconductor". Yes to all the previous questions. Thanks for looking at my thread, I REALLY want to make this el-cheapo mp3 player work with my Ubuntu.

---

### Post by Ripfox on 2007-09-09
Side note: this mp3 player DID show up on my desktop that has 6.06 installed (Xubuntu)
so this seems to be a Feisty problem. Does not show up under Gutsy either.

---

### Post by Jose Catre-Vandis on 2007-09-09
What does:
```
sudo fdisk -l
```
and
```
df -T -h
```
report?

---

### Post by Ripfox on 2007-09-09
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris


and

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    108G  2.3G  100G   3% /
varrun       tmpfs    502M  108K  501M   1% /var/run
varlock      tmpfs    502M     0  502M   0% /var/lock
procbususb   usbfs    502M  100K  501M   1% /proc/bus/usb
udev         tmpfs    502M  100K  501M   1% /dev
devshm       tmpfs    502M     0  502M   0% /dev/shm
lrm          tmpfs    502M   33M  469M   7% /lib/modules/2.6.20-15-generic/volatile


(thanks for the reply)

---

### Post by Ripfox on 2007-09-09
Ok...this is weird. I did a reinstall of Feisty, and after I did the updates, there was a "disk" icon on the desktop, and it was my mp3 player showing up. I opened it up and there was the music. So, I unmounted it, waited, plugged it back in, and NOTHING! What the hell is goin' on here! :confused:

---

### Post by Ripfox on 2007-09-09
bump

---

### Post by Ripfox on 2007-09-09
Ok...I feel like a dumbass now. :)

If anyone buys one of these or similar product:
[http://kinwei.manufacturer.globalsources.com/si/6008818364500/pdtl/Flash-MP3/1002078605/Flash-MP3-Player.htm](http://kinwei.manufacturer.globalsources.com/si/6008818364500/pdtl/Flash-MP3/1002078605/Flash-MP3-Player.htm)

There is an option in the actual menu on the player which says "online mode" and in there is an option to make it act as a usb drive or a "media player". I switched it to usb and viola, it worked.
This seems redundant to me, but what do I know!

---

### Post by Jose Catre-Vandis on 2007-09-11
Good to get it sorted, ripfox, I've been "there" too :)

---

