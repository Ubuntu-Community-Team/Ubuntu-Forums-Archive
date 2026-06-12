---
title: "help request"
date: 2008-02-20
forum: General Help
---

### Post by pagiatis on 2008-02-20
Hi. I am a newbie to linux and I am running the Gutsy Gibbon distribution, and I really like it, but I have some problems. First of all, when I insert a removable media like a cd or dvd,  
 I get a message that says that it cannot be mounted. It doesn't happen with all types of removable media though. Data dvds and cds work almost always fine, but video dvds and rewritable dvds don't. My laptop's dvd drive used to do weird things even when I had windows, but it worked at the beginning ( I have tried many times with an external drive, and it failed too). Also, I tried to access a memory stick by using a card reader and it recognized the card reader, but it couldn't recognize the card (I tried many types of cards too), and agaiin, it used to work some time ago. Also, when I try to waitch a video file with the default movie player(and others like Mplayer and vlc), I have no color. I have partly solved this by uninstalling the movie player, it's codecs, and the forbidden gnome essentials. Now I use Mplayer, but I really liked the other program for the playback of mp3s. And finally, the shutdown and restart buttons have disappeared from the shutdown menu, and I have to turn off the pc by using the laptop's button (5 second hold). And something more. I can't use my computer's wifi because I can't get the drivers working. I have downloaded a program that says that it can install windows drivers, but it didn't work correctly. So, these are the problems that I have. I would appreciate any help since i really like the OS, and I don't want to change it because of some minor problems. Thank you in advance, and sorry for the long post...

---

### Post by Kingsley on 2008-02-20
Which wireless card does your computer use?

---

### Post by Yellow Pasque on 2008-02-20
Can you run this for me so I  can see how your CD drive is set to mount things?
```
cat /etc/fstab | grep cd
```

I would also like to see what kind of wireless chip you have. Please run:
```
sudo update-pciids; sudo lshw -C network
```

When you need to turn off your computer, press Ctrl+Alt+F1 and enter this command in the terminal:
```
sudo init 0
```
This will bring the system down properly and makes sure you don't lose data.

---

### Post by pagiatis on 2008-02-20
First of all, thanks for your help. 
```
john665@sonyvaio665fu:~$ cat /etc/fstab | grep cd
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
john665@sonyvaio665fu:~$ sudo update-pciids; sudo lshw -C network
[sudo] password for john665:
--02:28:02--  http://pciids.sourceforge.net/v2.2/pci.ids.bz2
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 131,000 (128K) [text/plain]

100%[====================================>] 131,000       22.30K/s    ETA 00:00

02:28:11 (22.28 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [131000/131000]

Done.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:27:7c:b9
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:db:14:46
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.3 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```
This is what it says. Also, don't mind the username that I have at the pc. The pc is an acer.

---

### Post by Yellow Pasque on 2008-02-20
It looks like the wireless device has the driver loaded, so let's try these commands:
```
cat /etc/network/interfaces
iwconfig
```

---

### Post by pagiatis on 2008-02-20
```
john665@sonyvaio665fu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

john665@sonyvaio665fu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Yellow Pasque on 2008-02-20
Great! Now all you have to do is add the interface to the interfaces file:
```
sudo gedit /etc/network/interfaces
```
Add this:
```
auto eth1
iface eth1 inet dhcp
```
Save and reboot. Your connection should work.

---

