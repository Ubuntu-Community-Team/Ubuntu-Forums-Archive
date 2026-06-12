---
title: "How to use wireless"
date: 2008-05-04
forum: General Help
---

### Post by timboellis on 2008-05-04
I just got a new laptop with an Atheros wireless card hardware sees it as a hardware however how do i see and connect to networks?

---

### Post by timboellis on 2008-05-04
Lookijng at the other posts i see this if it helps at all

tim@tim-laptop:~$ lspci | grep -i net
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
tim@tim-laptop:~$

---

### Post by ghost_ryder35 on 2008-05-04
left click on network manager in the upper right hand corner
 
 If you cannot connect after doing that post the results of these commands on the forum
 
```

iwlist

```
```

ifconfig

```
```

lspci

```

---

### Post by ghost_ryder35 on 2008-05-04
> **timboellis said:**
> Lookijng at the other posts i see this if it helps at all
 
tim@tim-laptop:~$ lspci | grep -i net
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
tim@tim-laptop:~$
go to system, administration, software sources, and put a tick next to universal repositories, then click on the third party tab, and put a tick next to both of them. it will ask you to reload. Do it.
then go to terminal and do
```

**sudo apt-get install linux-restricted-modules-`uname -r`**

```
 
Then reboot, if the wireless still is not active
Then click system, administration, hardware drivers and put a tick next to the atheros drivers (hope they are there)

---

### Post by timboellis on 2008-05-04
IWLIST
[PHP]Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation [/PHP]

ifconfig
[PHP]eth0      Link encap:Ethernet  HWaddr 00:1e:68:3f:cc:01  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe3f:cc01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:941049 (918.9 KB)  TX bytes:193923 (189.3 KB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10800 (10.5 KB)  TX bytes:10800 (10.5 KB)
[/PHP]
lsci
[PHP]tim@tim-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
[/PHP]

---

### Post by twright on 2008-05-04
try /system/administration/hardware drivers

---

### Post by timboellis on 2008-05-04
yes it is in there and enabled as atheros hardware access layer (HAl)

---

### Post by timboellis on 2008-05-04
ALSO GOT SUPPORT for atheros 802.11 wireless lan cards

---

### Post by ghost_ryder35 on 2008-05-04
> **timboellis said:**
> ALSO GOT SUPPORT for atheros 802.11 wireless lan cards
so did that make it work?

---

### Post by timboellis on 2008-05-04
no thats been there from the begining

---

### Post by timboellis on 2008-05-06
does anyone have any sugestions before i format the ubuntu partition?

---

### Post by twright on 2008-05-06
it won't take long to get it working. 1st thing's first, find a windows driver for your card. you can use that with ubuntu

---

### Post by timboellis on 2008-05-06
Well i have tried the NDIS wrapper with a windows driver ubuntu sees it but do not know how to connect

i tried t download 2 wireless lan managers from the repos add/remove they both see the wireless as disabled.#


i have turned the wireless on and off with the switch on the laptop but still it cannot see it .

---

### Post by twright on 2008-05-06
if you post the output of ndiswrapper -l i will be able to help

i had to go through the ndiswrapper procedure when i 1st tried ubuntu but i eventually got it working (and it does it automatically for me now) and i have never looked back

---

### Post by timboellis on 2008-05-06
tim@tim-laptop:~$ ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
tim@tim-laptop:~$

---

### Post by twright on 2008-05-06
ok, can you try this in terminal
```
sudo su
echo ath_pci >> /etc/modprobe.d/blacklist
```then restart and see if that helps

the command "sudo iwlist scanning" will tell you if any networks have been found

---

### Post by timboellis on 2008-05-06
Well now I have the connect to wireless network and all i get is a poop up asking for the network name , peap etc.  I tried to put in my SSID no just to goes and thinks then drops off again.

I also ran kwifi and click scan for network and get nothing and the wifi is crossed out and tried wireless assistant and get Unknown encoding of: file:///usr/share/applications/kde/wlassistant.desktop

---

### Post by timboellis on 2008-05-06
Also I get 
root@tim-laptop:/home/tim# sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by timboellis on 2008-06-02
any help on this at all?

---

### Post by twright on 2008-06-02
try first removing ndiswrapper (sudo aptitude purge ndiswrapper) the use gksu gedit /etc/modprobe.d/blacklist and remove the las line from the file

now this tuturial should do the trick:
[http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)

---

### Post by timboellis on 2008-06-02
Thanks a lot finaly I am back to Ubuntu no more vista :-)

---

### Post by abuzakour on 2008-06-21
Hi Guys, 

sorry i am facing the same problem and i am a newbie in ubuntu.. 
i have removed the last lane from /etc/modprobe.d/blacklist
and i've gone to [http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)

there they are talking about Atheros AR5007EG and Not AR242x!! what do i have to do? i have disabled the download the driver of AR5007EG from the same link? Do i have to get the driver of AR242x? from where?? 

execuse my ignorance :-s

---

### Post by twright on 2008-06-21
> **abuzakour said:**
> Hi Guys, 

sorry i am facing the same problem and i am a newbie in ubuntu.. 
i have removed the last lane from /etc/modprobe.d/blacklist
and i've gone to [http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)

there they are talking about Atheros AR5007EG and Not AR242x!! what do i have to do? i have disabled the download the driver of AR5007EG from the same link? Do i have to get the driver of AR242x? from where?? 

execuse my ignorance :-s
you probably shouldn't have removed the last line (i had previously told him to put it there first :))

try one of these threads:
[http://ubuntuforums.org/tags.php?tag=ar242x](http://ubuntuforums.org/tags.php?tag=ar242x)

---

### Post by timboellis on 2008-07-29
As said previous I got it working with :

[PHP]1. Go to System -> Administration -> Hardware Drivers
2. UNCHECK Atheros Hardware Abstraction Layer (HAL)
3. Leave Support for Atheros 802.11 wireless LAN cards. CHECKED
For 64bits systems please follow the link below:
Quote:
http://www.ubuntugeek.com/atheros-ar...rdy-heron.html
I found this great link:
Quote:
http://madwifi.org/ticket/1679
Go to the bottom of the page and you'll find a link containing an already patched madwifi to support AR5007EG.

Here's the download link:
Quote:
http://snapshots.madwifi.org/special...+ar5007.tar.gz
The following are simple steps to compile and install the driver:
Quote:
1. Remove any ath_pci driver from the RESTRICTED DRIVERS MANAGER
2. Make sure that you have build-essential package installed, if not, fire up a terminal and type in sudo apt-get install build-essential
3. Navigate your way in Terminal to the directory where you downloaded the archive for the driver
4. Type these to decompress the archive tar xfz madwifi-ng-r2756+ar5007.tar.gz and cd madwifi-ng-r2756+ar5007
5. Type make to compile
6. Type sudo make install to install the driver
7. Type sudo modprobe ath_pci to insert the driver as a kernel module
8. Restart by typing sudo reboot
9. If all goes well, after you restarted, you will find wireless networks in your Network Manager [/PHP]

What has happened it when updates have been installed the wireless dissapeared but all I done as re installed the drivers not a big problem until now as it will not come back at all any suggestions

---

### Post by VyReN on 2008-07-29
This may be completely useless information, but I've had issues with my AR5007.  God only knows how I actually got the MadWiFi drivers installed and whatnot but for my wireless to work this is the process I had to do after the driver install:

Under Hardware Drivers I have UNCHECKED the "Atheros Hardware Access Layer (HAL)" and "Support for Atheros 802.11 wireless LAN cards".  I know this goes against the instructions, but ... it works for me.

Under System->Admin->Network you SHOULD have your "Wireless Connection" listed.  Change the properties...  I have DISABLED roaming mode, under "Network Name" you SHOULD have your wireless network listed.  Select it, click OK.

Pop open a terminal and sudo /etc/init.d/networking restart

That, for me, made everything work all pretty like.  Every time I switch networks I do need to select the new network and restart networking again, but it works. :)

I did notice with the Atheros drivers "enabled" my router logs showed a null MAC address when the machine attempted to connect.  I disabled those drivers and all was well.

Just my $0.02, for what its worth.

---

### Post by timboellis on 2008-07-29
Spot on all working now

---

