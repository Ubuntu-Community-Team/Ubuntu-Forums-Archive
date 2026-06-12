---
title: "Cant connect wirelessly ubuntu 12.10"
date: 2013-02-07
forum: General Help
---

### Post by zouthe on 2013-02-07
Hey i just put ubuntu 12.10 as my new os and im still kind of new. When i try to connect to my wireless it keeps poping up asking me my network password and never actually making a connection. Im not sure if maybe i need a driver or something of that sort? i did sudo-apt get update and sudo apt-get upgrade both didnt help me with the wireless problem.

:confused:

---

### Post by grahammechanical on 2013-02-07
When you click the Network Manager icon do you get a drop down menu with a list of wireless access points that are in range? Yes? Then you do not need a driver.

Can you see your access point (wireless) in the list? What happens when you click on it? Are you asked to authenticate? Network Manager usually identifies the encryption method. So, all we need to do is authenticate the connection.

What password are you putting in? Is the wireless key? Also called WPA-PSK key or wireless passphrase. If it is the password that you put in when installing Ubuntu. then it is the wrong password.

Regards.

---

### Post by zouthe on 2013-02-07
Thanks for the quick reply, yes i can see my network on a drop down page.. i didnt set up my router when i had ubuntu on my computer but it does contain a password.. so do i just need to figure out what settings need to be turned on in the options tab on the wireless page? If so how do i figure out which ones need to be applied to secure a strong connection?

:popcorn:

---

### Post by zouthe on 2013-02-07
> **zouthe said:**
> Thanks for the quick reply, yes i can see my network on a drop down page.. i didnt set up my router when i had ubuntu on my computer but it does contain a password.. so do i just need to figure out what settings need to be turned on in the options tab on the wireless page? If so how do i figure out which ones need to be applied to secure a strong connection?

:popcorn:


Such as the Wireless IPV4 Settings the IPV6 Setting and wireless security settings in the options page.

---

### Post by zouthe on 2013-02-07
When i type  $ sudo lshw -C network

i get

 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 78:e3:b5:6f:d1:88
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.0.56 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: ra0
       version: 00
       serial: 08:ed:b9:54:9a:05
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN latency=0 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:f0300000-f030ffff
zouthe@zouthe-HP-Pavilion-g6-Notebook-PC:~$ sudo modprobe rt5390sta
zouthe@zouthe-HP-Pavilion-g6-Notebook-PC:~$ iwconfig
ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:-41 dBm  Noise level:-41 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

---

