---
title: "mp3 player not recognized"
date: 2023-05-07
forum: General Help
---

### Post by jonfisher on 2023-05-07
Ubuntu 22.x  lts

My mp3 player doesn't show up in Ubuntu/task bar.

It use to in previous versions of Ubuntu

?

---

### Post by jonfisher on 2023-05-09
Since no one helped out since I made this post, I have gotten this far on another site:  [https://www.linuxquestions.org/questions/linux-hardware-18/mp3-player-not-recognized-4175724847/](https://www.linuxquestions.org/questions/linux-hardware-18/mp3-player-not-recognized-4175724847/)

I will keep checking this thread for help, as I still can't get the Sandisk mp3 player to work.

---

### Post by Dennis N on 2023-05-09
If the device doesn't show on the Ubuntu Dock when inserted, check Settings > Ubuntu Desktop > Dock > Configure Dock Behavior
Check to be sure "Show Volumes and Devices" is ON.

Even if not on the Dock, it should also be in the Files (Nautilus) side pane if mounted on insertion.

I checked an old San Disk mp3 player I have (20 years old!) and it does show up in Ubuntu 23.04 (screenshot).

---

### Post by jonfisher on 2023-05-09
> **Dennis N said:**
> If the device doesn't show on the Ubuntu Dock when inserted, check Settings > Ubuntu Desktop > Dock > Configure Dock Behavior
Check to be sure "Show Volumes and Devices" is ON.

Even if not on the Dock, it should also be in the Files (Nautilus) side pane if mounted on insertion.

I checked an old San Disk mp3 player I have (20 years old!) and it does show up in Ubuntu 23.04 (screenshot).



I don't seem to be having any luck.  See 2 screenshots below when Sandisk clip mp3 player is plugged in - nothing.  Nothing pops up on left dock either.  ???

---

### Post by Dennis N on 2023-05-09
It seems it is not being detected at all by the OS. Maybe it's not making a good connection. Are other USB devices being detected on the same USB port? Try another USB port to see if you get a connection. Try the device on another computer.

From the terminal, the command [FONT=Courier New]lsusb[/FONT] will show you connected devices. Does the player show up?

---

### Post by jonfisher on 2023-05-09
> **Dennis N said:**
> It seems it is not being detected at all by the OS. Maybe it's not making a good connection. Are other USB devices being detected on the same USB port? Try another USB port to see if you get a connection. Try the device on another computer.

From the terminal, the command [FONT=Courier New]lsusb[/FONT] will show you connected devices. Does the player show up?

I tried EVERYTHING you said.  I tried it on my laptop that is also 100% Ubuntu 22.x LTS   and  nothing!

It's an Ubuntu 22.x lts problem!

It's the Sandisk clip mp3 player....

> 
michael@michael-HP-EliteDesk-800-G1-SFF:~$ lsusb 
Bus 002 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c216 Logitech, Inc. F310 Gamepad [DirectInput Mode]
Bus 003 Device 003: ID 0781:b6b7 SanDisk Corp. SDDR-99 V4 ImageMate 5-in-1 Reader
Bus 003 Device 006: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 03f0:322a HP, Inc HP LaserJet Pro MFP M127fn
Bus 003 Device 002: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
michael@michael-HP-EliteDesk-800-G1-SFF:~$ 


above, I think the Sandisk it's seeing is my Sandisk card reader for my camera.

---

### Post by Dennis N on 2023-05-10
If it fails to be detected or mount on two different computers, I would have to suspect the player itself. Maybe a bad or dirty contact in the connector that goes into the USB port, rather than the port itself. That's all I can think of since you did all those tests. Sorry I don't have a better idea.

My San Disk Cruzer (see screenshot) has a USB stick that detaches from the player, then plugs into the USB port. The picture of post #3 is from Ubuntu 23.04, but it does connect and mount in Ubuntu 22.04 as well, shown below. 

```
dmn@Kayleigh:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0781:7114 [COLOR="#FF0000"]SanDisk Corp. Cruzer Mini[/COLOR]
Bus 001 Device 002: ID 0627:0001 Adomax Technology Co., Ltd QEMU USB Tablet
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jonfisher on 2023-05-10
ok, if anyone else can help, please do

---

### Post by jonfisher on 2023-05-11
What, no more help?

---

### Post by ActionParsnip on 2023-05-11
Reboot with the device unplugged and log in as normal. Let the OS settle and run:
```

sudo fdisk -l; lsusb

```
plug in the device, wait a few seconds, then run:
```

sudo fdisk -l; lsusb; dmesg | tail

```
What is the full output please?

Also, when you last unplugged the device, did you use the safe remove feature in the OS before physically unplugging it?

---

### Post by jonfisher on 2023-05-11
output is:

> 
michael@michael-HP-EliteDesk-800-G1-SFF:~$ sudo fdisk -l; lsusb
[sudo] password for michael: 
Disk /dev/loop0: 187.9 MiB, 197029888 bytes, 384824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 187.9 MiB, 197029888 bytes, 384824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 154.25 MiB, 161746944 bytes, 315912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 154.25 MiB, 161738752 bytes, 315896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 149 MiB, 156241920 bytes, 305160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 150.23 MiB, 157532160 bytes, 307680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 116.79 MiB, 122458112 bytes, 239176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Samsung SSD 870 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8FB7D54A-C82B-4B16-96AA-37640511E023

Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624 1953523711 1952473088  931G Linux filesystem


Disk /dev/sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000NM0033-9ZM
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D46CF724-B6A7-4363-8BFD-90A0B4D144B8

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048 1937139711 1937137664 923.7G Linux filesystem
/dev/sdb2  1937139712 1953523711   16384000   7.8G Linux swap


Disk /dev/loop8: 116.76 MiB, 122433536 bytes, 239128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 55.61 MiB, 58314752 bytes, 113896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 55.64 MiB, 58339328 bytes, 113944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 63.32 MiB, 66392064 bytes, 129672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 63.34 MiB, 66412544 bytes, 129712 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 72.99 MiB, 76537856 bytes, 149488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 72.99 MiB, 76537856 bytes, 149488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 55.1 MiB, 57778176 bytes, 112848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 55.03 MiB, 57704448 bytes, 112704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 22.16 MiB, 23232512 bytes, 45376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 241.9 MiB, 253648896 bytes, 495408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 241.49 MiB, 253222912 bytes, 494576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 391.27 MiB, 410279936 bytes, 801328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 521.44 MiB, 546766848 bytes, 1067904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop22: 164.82 MiB, 172830720 bytes, 337560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop23: 164.82 MiB, 172830720 bytes, 337560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop24: 349.69 MiB, 366673920 bytes, 716160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop25: 349.69 MiB, 366678016 bytes, 716168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop26: 460.56 MiB, 482930688 bytes, 943224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop27: 460.56 MiB, 482930688 bytes, 943224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop28: 140 KiB, 143360 bytes, 280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop29: 81.26 MiB, 85209088 bytes, 166424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop30: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop31: 52.36 MiB, 54898688 bytes, 107224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop32: 52.36 MiB, 54902784 bytes, 107232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop33: 37.09 MiB, 38891520 bytes, 75960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop34: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop35: 4.2 MiB, 4403200 bytes, 8600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop36: 102.5 MiB, 107474944 bytes, 209912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop37: 102.84 MiB, 107835392 bytes, 210616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop38: 157.76 MiB, 165425152 bytes, 323096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop39: 260.71 MiB, 273375232 bytes, 533936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop40: 289.78 MiB, 303853568 bytes, 593464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop41: 101.47 MiB, 106397696 bytes, 207808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop42: 213.2 MiB, 223559680 bytes, 436640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop43: 51.66 MiB, 54173696 bytes, 105808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop44: 51.66 MiB, 54173696 bytes, 105808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop45: 45.93 MiB, 48160768 bytes, 94064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop46: 45.93 MiB, 48156672 bytes, 94056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop47: 53.24 MiB, 55824384 bytes, 109032 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop48: 53.24 MiB, 55824384 bytes, 109032 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop49: 428 KiB, 438272 bytes, 856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop50: 452 KiB, 462848 bytes, 904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop51: 295.71 MiB, 310079488 bytes, 605624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop52: 320.44 MiB, 336003072 bytes, 656256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Bus 002 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 007: ID 046d:c216 Logitech, Inc. F310 Gamepad [DirectInput Mode]
Bus 003 Device 003: ID 0781:b6b7 SanDisk Corp. SDDR-99 V4 ImageMate 5-in-1 Reader
Bus 003 Device 006: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 03f0:322a HP, Inc HP LaserJet Pro MFP M127fn
Bus 003 Device 002: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
michael@michael-HP-EliteDesk-800-G1-SFF:~$ sudo fdisk -l; lsusb; dmesg | tail
Disk /dev/loop0: 187.9 MiB, 197029888 bytes, 384824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 187.9 MiB, 197029888 bytes, 384824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 154.25 MiB, 161746944 bytes, 315912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 154.25 MiB, 161738752 bytes, 315896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 149 MiB, 156241920 bytes, 305160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 150.23 MiB, 157532160 bytes, 307680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 116.79 MiB, 122458112 bytes, 239176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Samsung SSD 870 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8FB7D54A-C82B-4B16-96AA-37640511E023

Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624 1953523711 1952473088  931G Linux filesystem


Disk /dev/sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000NM0033-9ZM
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D46CF724-B6A7-4363-8BFD-90A0B4D144B8

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048 1937139711 1937137664 923.7G Linux filesystem
/dev/sdb2  1937139712 1953523711   16384000   7.8G Linux swap


Disk /dev/loop8: 116.76 MiB, 122433536 bytes, 239128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 55.61 MiB, 58314752 bytes, 113896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 55.64 MiB, 58339328 bytes, 113944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 63.32 MiB, 66392064 bytes, 129672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 63.34 MiB, 66412544 bytes, 129712 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 72.99 MiB, 76537856 bytes, 149488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 72.99 MiB, 76537856 bytes, 149488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 55.1 MiB, 57778176 bytes, 112848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 55.03 MiB, 57704448 bytes, 112704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 22.16 MiB, 23232512 bytes, 45376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 241.9 MiB, 253648896 bytes, 495408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 241.49 MiB, 253222912 bytes, 494576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 391.27 MiB, 410279936 bytes, 801328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 521.44 MiB, 546766848 bytes, 1067904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop22: 164.82 MiB, 172830720 bytes, 337560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop23: 164.82 MiB, 172830720 bytes, 337560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop24: 349.69 MiB, 366673920 bytes, 716160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop25: 349.69 MiB, 366678016 bytes, 716168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop26: 460.56 MiB, 482930688 bytes, 943224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop27: 460.56 MiB, 482930688 bytes, 943224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop28: 140 KiB, 143360 bytes, 280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop29: 81.26 MiB, 85209088 bytes, 166424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop30: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop31: 52.36 MiB, 54898688 bytes, 107224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop32: 52.36 MiB, 54902784 bytes, 107232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop33: 37.09 MiB, 38891520 bytes, 75960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop34: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop35: 4.2 MiB, 4403200 bytes, 8600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop36: 102.5 MiB, 107474944 bytes, 209912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop37: 102.84 MiB, 107835392 bytes, 210616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop38: 157.76 MiB, 165425152 bytes, 323096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop39: 260.71 MiB, 273375232 bytes, 533936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop40: 289.78 MiB, 303853568 bytes, 593464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop41: 101.47 MiB, 106397696 bytes, 207808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop42: 213.2 MiB, 223559680 bytes, 436640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop43: 51.66 MiB, 54173696 bytes, 105808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop44: 51.66 MiB, 54173696 bytes, 105808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop45: 45.93 MiB, 48160768 bytes, 94064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop46: 45.93 MiB, 48156672 bytes, 94056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop47: 53.24 MiB, 55824384 bytes, 109032 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop48: 53.24 MiB, 55824384 bytes, 109032 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop49: 428 KiB, 438272 bytes, 856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop50: 452 KiB, 462848 bytes, 904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop51: 295.71 MiB, 310079488 bytes, 605624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop52: 320.44 MiB, 336003072 bytes, 656256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Bus 002 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 007: ID 046d:c216 Logitech, Inc. F310 Gamepad [DirectInput Mode]
Bus 003 Device 003: ID 0781:b6b7 SanDisk Corp. SDDR-99 V4 ImageMate 5-in-1 Reader
Bus 003 Device 006: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 03f0:322a HP, Inc HP LaserJet Pro MFP M127fn
Bus 003 Device 002: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dmesg: read kernel buffer failed: Operation not permitted
michael@michael-HP-EliteDesk-800-G1-SFF:~$ 


---

### Post by speartip on 2023-05-11
I know that this doesn't help your issue, but my Sandisk Sansa Clip mp3 player, opens and transfers files perfectly on my 22.04 LTS system, so it's likely not the OS that's at fault. What model Sansa Clip do you have? and how old is it?

---

### Post by jonfisher on 2023-05-11
> **speartip said:**
> I know that this doesn't help your issue, but my Sandisk Sansa Clip mp3 player, opens and transfers files perfectly on my 22.04 LTS system, so it's likely not the OS that's at fault. What model Sansa Clip do you have? and how old is it?

i just know it looks like this and yes, it too use to work easily like yours
the usb charges it fine, i have lots of songs on it, so i'll just keep using it without the option to add more mp3s to it

[IMG]https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Fwww.picstop.co.uk%2Fuser%2Fproducts%2Flarge%2Fsandisk-sansa-clip-jam-blk.jpg&f=1&nofb=1&ipt=bd76d2f2a03c2f107b0b3c933465eafcc56f9f21a0239887b9505b72391cd5c7&ipo=images[/IMG]

---

### Post by ActionParsnip on 2023-05-11
When you last unplugged it, did you use the safe remove feature in the OS before physically unplugging it?

---

### Post by jimmyrus on 2023-08-17
Man, still?  [https://www.linuxquestions.org/questions/linux-hardware-18/sandisk-mp3-player-no-longer-pops-up-on-screen-4175709549/](https://www.linuxquestions.org/questions/linux-hardware-18/sandisk-mp3-player-no-longer-pops-up-on-screen-4175709549/), [https://www.linuxquestions.org/questions/linux-hardware-18/mp3-player-not-recognized-4175724847/page2.html#post6429877](https://www.linuxquestions.org/questions/linux-hardware-18/mp3-player-not-recognized-4175724847/page2.html#post6429877), [https://www.linuxquestions.org/questions/linux-hardware-18/sandisk-mp3-player-no-longer-pops-up-on-screen-4175709549/](https://www.linuxquestions.org/questions/linux-hardware-18/sandisk-mp3-player-no-longer-pops-up-on-screen-4175709549/)

Gotta be baby fed after having ubuntu since 2015?

---

