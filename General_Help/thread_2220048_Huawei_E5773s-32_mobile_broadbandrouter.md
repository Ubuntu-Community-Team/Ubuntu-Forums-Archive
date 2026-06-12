---
title: "Huawei E5773s-32 mobile broadband/router"
date: 2014-04-26
forum: General Help
---

### Post by anssi2 on 2014-04-26
Hiya all. 

I am a very very new user to ubuntus so, most likely what im asking is something pretty easy. :D

I have a Huawei E5773s-32 mobile broadband/router which i am using directly through usb (since im using it on old desktop). Im running it on Lubuntu 14.04. Why doesnt this work? :/
[B]
lsusb shows:
[/B]```
Bus 001 Device 003: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM
Modem/Networkcard
```
This also shows a bunch of root hubs, which are most likely non-important. Also, to me it seems that my Huawei is recognized as a moden, rather than usb memory.

Network Connections, through which i think one should connect to the interwebs :D also doesnt seem to show any connection and no matter the setting (DNS etc) also ones made by me dont work.

Thanks a bunch :D

---

### Post by anssi2 on 2014-04-27
So, i think i have made atleast a tiny bit of progress. Even though i dont have a clue what to do with my new found information.
[B]
sudo lshw -C network shows:[/B]
```
*-network DISABLED
description: Ethernet interface
```
So, that is what i find interesting. Why does it say Ethernet interface? Im definately not using ethernet. How can that be changed?...

---

### Post by varunendra on 2014-04-27
Welcome to the forums anssi2!

Please try this -

Open "Disk Utility" program from Unity dash or Applications menu (if using a Desktop Environment other than Unity) and see if the modem appears as a mounted cd drive. If yes, eject it from the application and see if Network Manager prompts you for a "New Mobile Broadband Connection..".

(alternative way to open "Disk Utility" : Press "Alt-F2" > type "palimpsest" > press Enter)

If you don't see a mounted cd there, or the trick doesn't work, please disconnect the modem > wait 10 seconds > reconnect > wait about 30 seconds > open a terminal (Ctrl-Alt-T) and post back the full outputs of -
```
lsusb
dmesg | tail -40
```

---

### Post by anssi2 on 2014-04-27
Thank you varunendra. :)

So, i tried what you said. It did appear as cd-drive, yet ejecting it did nothing.

[B]lsusb shows:
[/B]```
Bus 001 Device 004: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Aaaaand
[B]
dmesg | tail - 40[/B]
```
[  104.414701] usb-storage 1-6:1.2: USB Mass Storage device detected
[  104.421697] scsi4 : usb-storage 1-6:1.2
[  104.421990] usb-storage 1-6:1.3: USB Mass Storage device detected
[  104.422254] scsi5 : usb-storage 1-6:1.3
[  105.453575] scsi 4:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  105.453817] scsi 5:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[  105.626765] sr1: scsi-1 drive
[  105.632129] sr 4:0:0:0: Attached scsi CD-ROM sr1
[  105.632757] sr 4:0:0:0: Attached scsi generic sg2 type 5
[  105.633100] sd 5:0:0:0: Attached scsi generic sg3 type 0
[  105.925510] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  108.305510] ISO 9660 Extensions: Microsoft Joliet Level 1
[  108.329412] ISOFS: changing to secondary root
[  342.682288] usb 1-6: USB disconnect, device number 3
[  342.682581] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  342.682612] option 1-6:1.0: device disconnected
[  342.682707] huawei_cdc_ncm 1-6:1.1 wwan0: unregister 'huawei_cdc_ncm' usb-0000:00:10.4-6, Huawei CDC NCM device
[  362.792028] usb 1-6: new high-speed USB device number 4 using ehci-pci
[  362.929845] usb 1-6: New USB device found, idVendor=12d1, idProduct=1506
[  362.929854] usb 1-6: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[  362.929858] usb 1-6: Product: HUAWEI Mobile
[  362.929861] usb 1-6: Manufacturer: HUAWEI Technology
[  362.938239] option 1-6:1.0: GSM modem (1-port) converter detected
[  362.938414] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[  362.942975] huawei_cdc_ncm 1-6:1.1: MAC-Address: 0c:5b:8f:27:9a:64
[  362.943124] huawei_cdc_ncm 1-6:1.1: cdc-wdm0: USB WDM device
[  362.943681] huawei_cdc_ncm 1-6:1.1 wwan0: register 'huawei_cdc_ncm' at usb-0000:00:10.4-6, Huawei CDC NCM device, 0c:5b:8f:27:9a:64
[  362.944050] usb-storage 1-6:1.2: USB Mass Storage device detected
[  362.950597] scsi6 : usb-storage 1-6:1.2
[  362.950883] usb-storage 1-6:1.3: USB Mass Storage device detected
[  362.951174] scsi7 : usb-storage 1-6:1.3
[  363.949246] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  363.953089] scsi 7:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[  364.076713] sr1: scsi-1 drive
[  364.077005] sr 6:0:0:0: Attached scsi CD-ROM sr1
[  364.077234] sr 6:0:0:0: Attached scsi generic sg2 type 5
[  364.077607] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  364.317702] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  366.212122] ISO 9660 Extensions: Microsoft Joliet Level 1
[  366.213120] ISOFS: changing to secondary root

```

Something helpful? :)

---

### Post by varunendra on 2014-04-28
I'm afraid I know next to nothing about these "cdc_device" things. I would have loved to figure it out (I'm sure there are good reference threads about it here, please try searching yourself), but I don't have much time these days to dig and discover new treasures of knowledge.

For now, please post back the outputs of -
```
usb-devices
ifconfig -a
sudo lshw -C network
nm-tool
```
..with the modem plugged in, and "lsusb" showing its device ID as "12d1:1506".

And since I may not be able to help further without getting some help myself, please try to find reference threads to your particular device ("Huawei E5773s" or "12d1:1506"), and/or keywords "cdc_wdm" and "cdc_ncm". Please post back if you find anything that looks helpful, I'd be glad to work with substantial hints.

Posts by forum user "bmork" may be particularly helpful.

---

