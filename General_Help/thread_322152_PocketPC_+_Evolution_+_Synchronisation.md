---
title: "PocketPC + Evolution + Synchronisation"
date: 2006-12-20
forum: General Help
---

### Post by MegaHz on 2006-12-20
Hi,
has anybody managed to synchronise the windows pocket pc with evolution?

thanks

---

### Post by andreh on 2007-03-09
Hello, I tried to connect a Mitac Mio P550 to Ubuntu 06.06 Dapper Drake but also I was not able to do this. Did anybody succeed in connnecting a Mitac Mio P350, an Asus N632 or an Qtek g100 to Ubunut and was able to exchange files ?
I think it already goes wrong with the driver which is NOT present. It seems it is only possible for HP IPAQ and for Palm PDA's.
Am I right ?
If I read the book Hack 23 Sync with your PDA
[b]


Ubuntu Hacks
By Bill Childers, Jonathan Oxer, Kyle Rankin
...............................................
Publisher: O'Reilly
Pub Date: June 2006
Print ISBN-10: 0-596-52720-9
Print ISBN-13: 978-0-59-652720-4
Pages: 447
[/b]
they tell me this: ** dmesg**

 1738.233238] usb 1-1: new full speed USB device using ohci_hcd and address 2 [ 1738.796279] ipaq 1-1:1.0: PocketPC PDA converter detected 
[ 1738.803167] **usb 1-1: PocketPC PDA converter now attached to ttyUSB0**

[i]
Unfortunately, this probably won't work with a Pocket PC that's too new. At the time of this writing, SynCE did not yet support the most recent Pocket PC operating system, Windows Mobile 5.0. 
The next thing you'll need to do is install some packages, but before you do so, make sure you've enabled the universe repository in /etc/apt/sources.list. Then, run sudo apt-get update to get the latest packages and install synce, dccm, and some supporting tools: [/i]
USER@ubuntu:~$ sudo apt-get install synce-dccm synce-serial librra0-tools 
            





> 
Hoi, 
Volgens mij wil mijn PocketPC 5 Mip P550 niet praten met ubuntu 06.06.
* Hoe kan ik zien hoe het device heet en waar het zit ? *

als ik dmesg in tik krijg ik
   [quote][4294926.344000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4295546.535000] usb 1-1: USB disconnect, address 3
[4295550.957000] usb 1-1: new full speed USB device using uhci_hcd and address 4
maar dan had toch ook al het device genoemd moeten worden ? dus iets als
   > 'usb 4-2: PocketPC PDA converter now attached to ttyUSB0'
In 
"cat /proc/bus/usb/devices"
staat
   > T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ef(unk. ) Sub=01 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=3340 ProdID=a0a1 Rev= 0.00
S:  Manufacturer=Mitac Corporation
S:  Product=Mio DigiWalker USB Sync
S:  SerialNumber=e61dd285-1d1d-0604-0108-00022ac1fc92
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ef(unk. ) Sub=01 Prot=01 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
waarbij 
   > Driver=(none)
me wat ongerust maakt.

Daarna dit commando uitgevoerd:
   > sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial
met o.a. dit als resultaat:
   > synce-multisync-plugin is already the newest version.
synce-serial is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 72 not upgraded.
en nu denk ik dat het hier is mis gegaan:
   > /dev/ttyUSB0
local address: 192.168.131.102
remote address: 192.168.131.201
no dns entry needed
die /dev/ttyUSB0 zie ik nergens, dus niet bij dmesg en ook niet in /dev met :

USER@ubuntu:~$ ls -rtl /dev/*SB*
ls: /dev/*SB*: No such file or directory


ls -rtl /dev/*sd*
[b]
Mijn vraag is dus:
Moet ik dit commando 
  sudo synce-serial-config ttyUSB0
wel geven ?
[/b]
Die ttUSB0 is toch niet goed ?


[http://www.ubuntuforums.org/showthread.php?t=136257&page=2](http://www.ubuntuforums.org/showthread.php?t=136257&page=2)
[http://www.ubuntuforums.org/showthread.php?t=136257&page=5](http://www.ubuntuforums.org/showthread.php?t=136257&page=5)
[http://ubuntuforums.org/showthread.php?t=30936&page=9](http://ubuntuforums.org/showthread.php?t=30936&page=9)


> rs@ubuntu:~$ multisync
[plugin_init:915] here
plugin_API_version
short_name
long_name
plugin_init
[sync_connect:48] ----->
[synce_info_from_file:51] unable to open file: /home/USER/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[synce_connect:291] Failed to initialize RAPI
[sync_connect:62] <-----
[sync_connect:48] ----->
[synce_info_from_file:51] unable to open file: /home/USER/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[synce_connect:291] Failed to initialize RAPI
[sync_connect:62] <-----
[sync_disconnect:73] ----->
[synce_join_thread:260] synce_join_thread called when no thread is running
[sync_disconnect:79] <-----
[sync_disconnect:73] ----->
[synce_join_thread:260] synce_join_thread called when no thread is running
[sync_disconnect:79] <-----
[http://www.sjoerdmulder.nl/wordpress/?p=4](http://www.sjoerdmulder.nl/wordpress/?p=4)
[/quote]

---

### Post by andreh on 2007-03-13
Building SynCE with Windows Mobile 2005 support from Subversion
[http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion](http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion)

[http://www.opensync.org/wiki/DeviceCompatibilityList](http://www.opensync.org/wiki/DeviceCompatibilityList)

> LDAP Plugin
Moto Plugin
Opie Plugin
Palm Plugin
Python Plugin
Sunbird Plugin
Synce Plugin ¶
How could i sync my WM5 device?
[b]
The libopensync-plugin-synce in OpenSync is currently not able to sync with WM5 devices.
There exist a in project for syncing OpenSync with WM5 Devices. 
SyncML[/b]

[http://www.opensync.org/wiki/syncml-guide](http://www.opensync.org/wiki/syncml-guide) 
I got Error XYZ ... what does it mean?

[[http://libsyncml.opensync.org/wiki/ErrorCodes]](http://libsyncml.opensync.org/wiki/ErrorCodes])
[http://www.opensync.org/wiki/DeviceCompatibilityList](http://www.opensync.org/wiki/DeviceCompatibilityList)

Building SynCE with Windows Mobile 2005 support from Subversion
[http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion](http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion)

HOWTO is based on syncing my Dell Axim X3i with Evolution, but it should carry over to IPAQs and other Pocket PCs
[http://www.ubuntuforums.org/archive/index.php/t-30936.html](http://www.ubuntuforums.org/archive/index.php/t-30936.html)

---

### Post by jacksonz123z on 2007-03-17
Yes, under Fiesty I can sync my HP Ipaq1930 with Evolution, the contacts and calendar are perfect .  The Howto worked first time with out problems.

---

### Post by Paulo Wageck on 2007-03-18
i could sync an eten m600 and a linux box using a vmware virtual machine to sync files and emails (w/ the virtual machine running windows).

---

