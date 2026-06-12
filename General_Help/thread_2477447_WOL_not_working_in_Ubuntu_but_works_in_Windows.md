---
title: "WOL not working in Ubuntu but works in Windows"
date: 2022-07-25
forum: General Help
---

### Post by zkab on 2022-07-25
I have problems with a Dell XPS (Ubuntu 20.04 LTS preinstalled) and dock Dell WD19TB.
I have also another Dell XPS (Windows 11 preinstalled) and WOL in BIOS enabled attached to another WD19TB ... WOL works for the 'Windows XPS'.

WOL has been enabled in BIOS for the 'Ubuntu-XPS':

```
sudo ethtool <interface> | grep Wake-on
Supports Wake-on: pumbg
Wake-on: g

```
But when i give command:

```
wakeonlan -i 192.168.1.3 XX:XX:XX:XX:XX:XX
```

where 192.168.1.3 / XX:XX:XX:XX:XX:XX is the IP / MAC-address for Dell XPS (Ubuntu) ... nothing happends.


What I did for testing was replacing the 'Windows-dock' with 'Ubuntu-dock' and suddenly WOL works ... pure magic.
Don't understand why WOL works in a Windows environment but not in Ubuntu environment with identical docks.
Here are some information about the 'Ubuntu-dock':
```
   
oden@rk-dell:~$ fwupdmgr get-devices

&#9500;&#9472;WD19TB:
&#9474; &#9474;   Device ID:          570867f4ddda9915445da59bd85cd0e0e507270e
&#9474; &#9474;   Summary:            High performance dock
&#9474; &#9474;   Current version:    01.01.00.03
&#9474; &#9474;   Vendor:             Dell Inc. (USB:0x413C)
&#9474; &#9474;   Install Duration:   1 minute
&#9474; &#9474;   GUID:               cd357cf1-40b2-5d87-b8df-bb2dd82774aa
&#9474; &#9474;   Device Flags:       &#8226; Updatable
&#9474; &#9474;                       &#8226; Supported on remote server
&#9474; &#9474;                       &#8226; Device stages updates
&#9474; &#9474;                       &#8226; Device can recover flash failures
&#9474; &#9474;                       &#8226; Device is usable for the duration of the update
&#9474; &#9474; 
&#9474; &#9500;&#9472;Package level of Dell dock:
&#9474; &#9474;     Device ID:        073624c16dd99abe01ba1da223a70321e4f29beb
&#9474; &#9474;     Summary:          A representation of dock update status
&#9474; &#9474;     Current version:  01.00.25.01
&#9474; &#9474;     Vendor:           Dell Inc. (USB:0x413C)
&#9474; &#9474;     Install Duration: 5 seconds
&#9474; &#9474;     GUID:             8ceeeffd-51b6-580c-9b75-69143227aff8
&#9474; &#9474;     Device Flags:     &#8226; Updatable
&#9474; &#9474;                       &#8226; Supported on remote server
&#9474; &#9474;                       &#8226; Device can recover flash failures
&#9474; &#9474;                       &#8226; Device is usable for the duration of the update
&#9474; &#9474;   
&#9474; &#9500;&#9472;RTS5413 in Dell dock:
&#9474; &#9474;     Device ID:        0acceea54e71c4d8002593822afe0f4705616613
&#9474; &#9474;     Summary:          USB 3.1 Generation 1 Hub
&#9474; &#9474;     Current version:  01.21
&#9474; &#9474;     Vendor:           Dell Inc. (USB:0x413C)
&#9474; &#9474;     Install Duration: 14 seconds
&#9474; &#9474;     GUIDs:            86fb40c0-8bf5-5a8b-a4ad-3156cf6bfaf4
&#9474; &#9474;                       b27d25f1-019d-5718-b41a-02ddaefe5577
&#9474; &#9474;                       ac5b774c-b49d-566b-9255-85f0f7f8a4ed
&#9474; &#9474;     Device Flags:     &#8226; Updatable
&#9474; &#9474;                       &#8226; Supported on remote server
&#9474; &#9474;                       &#8226; Device stages updates
&#9474; &#9474;                       &#8226; Device is usable for the duration of the update
&#9474; &#9474;   
&#9474; &#9500;&#9472;RTS5487 in Dell dock:
&#9474; &#9474;     Device ID:        96969b82d977fdcbf607df084ef0dcf10119409b
&#9474; &#9474;     Summary:          USB 3.1 Generation 2 Hub
&#9474; &#9474;     Current version:  01.47
&#9474; &#9474;     Vendor:           Dell Inc. (USB:0x413C)
&#9474; &#9474;     Install Duration: 3 seconds
&#9474; &#9474;     GUIDs:            707c63d2-e597-5c40-84db-9b1bb4c48d96
&#9474; &#9474;                       acfcd89b-105d-55b9-b85b-08bf8508f38c
&#9474; &#9474;                       568ffa1e-a0db-5287-9ea3-872b60f7730b
&#9474; &#9474;     Device Flags:     &#8226; Updatable
&#9474; &#9474;                       &#8226; Supported on remote server
&#9474; &#9474;                       &#8226; Device stages updates
&#9474; &#9474;                       &#8226; Device is usable for the duration of the update
&#9474; &#9474;   
&#9474; &#9500;&#9472;VMM5331 in Dell dock:
&#9474; &#9474;     Device ID:        228ac6846b64d532dd1ea1b7e651e8f5f55fbc34
&#9474; &#9474;     Summary:          Multi Stream Transport controller
&#9474; &#9474;     Current version:  05.06.03
&#9474; &#9474;     Vendor:           Dell Inc. (USB:0x413C)
&#9474; &#9474;     Install Duration: 6 minutes
&#9474; &#9474;     GUID:             89fec0b6-6b76-5008-b82c-5e5c6c164007
&#9474; &#9474;     Device Flags:     &#8226; Updatable
&#9474; &#9474;                       &#8226; Supported on remote server
&#9474; &#9474;                       &#8226; Device stages updates
&#9474; &#9474;                       &#8226; Device is usable for the duration of the update
&#9474; &#9474;   
&#9474; &#9492;&#9472;Thunderbolt controller in Dell dock:
&#9474;       Device ID:        0833504c8c7accce52bb2216d78945dd41dd8bb1
&#9474;       Summary:          Thunderbolt controller
&#9474;       Current version:  60.00
&#9474;       Vendor:           Dell Inc. (THUNDERBOLT:0x00D4, TBT:0x00D4)
&#9474;       Install Duration: 22 seconds
&#9474;       GUIDs:            48711a14-0aaa-55b8-a17f-f7c494b318c6
&#9474;                         08a8c886-2818-544c-b1a3-588eb07ae487
&#9474;                         c94770ca-1773-592c-b20a-e87243bc7cd0
&#9474;                         017a6b19-1f84-5be6-89f5-14ebd10a52de
&#9474;       Device Flags:     &#8226; Updatable
&#9474;                         &#8226; System requires external power source
&#9474;                         &#8226; Supported on remote server
&#9474;                         &#8226; Install to parent device first
&#9474;                         &#8226; Device stages updates
&#9474;                         &#8226; Device is usable for the duration of the update

oden@rk-dell:~$ sudo fwupdmgr get-updates
Devices with no available firmware updates: 
 &#8226; VEN 04F3:00 04F3:31D1
 &#8226; TPM 2.0
 &#8226; UEFI Device Firmware
 &#8226; UEFI Device Firmware
 &#8226; UEFI dbx
 &#8226; USB4 Retimer
 &#8226; USB4 host controller
 &#8226; USB4 host controller
Devices with the latest available firmware version:
 &#8226; Package level of Dell dock
 &#8226; RTS5413 in Dell dock
 &#8226; RTS5487 in Dell dock
 &#8226; VMM5331 in Dell dock
 &#8226; WD19TB
 &#8226; PM9A1 NVMe Samsung 1024GB
 &#8226; System Firmware
 &#8226; Thunderbolt controller in Dell dock
No updates available for remaining devices

&#9474;     

```

I am lost ...

---

