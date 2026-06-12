---
title: "Internet Not Working"
date: 2007-10-18
forum: General Help
---

### Post by condawg on 2007-10-18
Hi there.
I just installed Ubuntu 7.04 on my other computer and am having a problem...
I run wireless internet (the wireless starts down on the first floor, I'm on the third floor), and since Ubuntu's awesome I didn't have to install drivers of any kind.
BUT, if I try to connect to one of the networks, it doesn't work.
Any help?

EDIT : Forgot to Mention -- The wireless adapter worked on the machine when I had Windows XP on it... Just doesn't work now. :S

---

### Post by condawg on 2007-10-18
Anybody? Please?

---

### Post by nickpaton on 2007-10-18
Further information please....

Could you post the outputs from the following:

```
sudo lshw -C network
```

and 

```
iwconfig
```

---

### Post by condawg on 2007-10-18
> **nickpaton said:**
> Further information please....

Could you post the outputs from the following:

```
sudo lshw -C network
```

and 

```
iwconfig
```

Surely.
(sorry for the late response... I was helping my brother with his homework)


Sud lshw -C network --
```

*-network:0
Description: Wireless Interface
product: RT2500 802.11g Cardbus/mini-PCI
vendor: RaLink
physical id: a
bus info: pci@02:0a.0
logical name: ra0
version: 01
serial: 00:12:17:9a:7d:ea
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 latency=32 link=yes multicast=yes wireless=RT2500 Wireless
Resources: iomemory:df004000-df005fff irq:21

*-network:1
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: c
bus info: pci@02:0c.0
logical name: eth0
version: 10
serial: 00:10:dc:5e:df:7c
size: 10MB/s
capacity: 100MB/s
width:32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
resources: ioport:c400-c4ff iomemory:df007000-df0070ff irq:19

```



iwconfig --

```

lo      no wireless extensions.


eth0     no wireless extensions.


ra0    RT2500 Wireless ESSID:""
mode:managed frequency:2.412 GHz Bit Rate:48 Mb/s Tx-Power:0 dBm
RTS thr:off Fragment thr: off
Link quality=64/100 signal level=-57 dBm noise level:-192 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag: 0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```



Jesus, that took like, 10 minutes to type.

---

### Post by nickpaton on 2007-10-18
Thanks for that and sorry for the typing LOL.  
The easiest way of copying the contents of the Terminal is to simply place your mouse at the top of the bit to be copied and sweep down to the end of the copy section.  
Then right mouse click and do a copy.  Back to the reply box (here), click on # above, and paste the selected Terminal contents between the ##'s.
Bet you wish you'd known that earlier!!

Right.. Have a look at this [HOWTO]("http://ubuntuforums.org/showthread.php?t=241565")

and 

[this one]("http://ubuntuforums.org/showthread.php?t=27134") 

There are new Serial Monkey drivers, but I cannot off hand find too much information on them.  I have just used them for a related chipset and they work reliably on 7.04.
Do a further forum search on RT2500 and Serial monkey and that should give further useful results.
I'll try and dig out the information for you tomorrow.

I don't recommend using the Windows .ini file and Ndiswrapper method since it's now been superceded by the above procedures.

Good luck and hope your brother gets good marks in his homework!

Nick

---

### Post by condawg on 2007-10-18
Thanks much! I'll check out the links.
And I couldn't copy/paste it becausae I'm on my Windows machine right now, the internet's not working on the Ubuntu, so I had to type the commands in Ubuntu then look at that screen while typing over here :P
Thanks though.
*clickeh*

---

### Post by nickpaton on 2007-10-18
Been digging around for the SerialMonkey stuff.  [Here's]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page") the official site

What they recommend is using the GUI [RutilT]("http://ubuntuforums.org/showthread.php?t=554089") which is great for detecting and setting up your wireless connection.

I'll have to look into how to link RutilT to installing the RT2500 driver tomorrow for ya.

Cheers M8

---

### Post by condawg on 2007-10-18
Awesome! Thank you

---

### Post by condawg on 2007-10-18
Okay, I downloaded the driver from that site and got it onto my Ubuntu machine, but how do I install it?
Sorry, new to Linux.

---

### Post by condawg on 2007-10-18
Also, will installing Gutsy Gibbon fix this problem? Does that have an automatic fix for this?
Because I'm downloading that now.

---

### Post by nickpaton on 2007-10-19
> **condawg said:**
> Also, will installing Gutsy Gibbon fix this problem? Does that have an automatic fix for this?
Because I'm downloading that now.

Post 51 on [this thread]("http://ubuntuforums.org/showthread.php?t=563547&page=6") seems to indicate that the driver is fixed in Gutsy.

See how it goes.  I'm not going to available for a week or so from the W/E so apologies if you're waiting for a reply from me next week.

---

### Post by condawg on 2007-10-19
Thanks :D
And not a problem :)
Hopefully Gutsy will make it work... My Windows XP crashed last night (on my mom's laptop right now while XP reinstalls), so the GG download didn't finish, but I'll try and get it finished, installed, and running later :)

---

### Post by nickpaton on 2007-10-19
I've just had another look over the whole thread.

From your iwconfig, you already have the RT2500 chipset driver for your WLAN card installed, however I didn't spot this properly and subsequently gave you some duff information.  
My stupid & apologies to you - I was very tired at the time.

What is needed is a suitable Interface to set up the device.  

When using a device with a similar chipset (RT73) it's been reported that it will not work with the preinstalled Network Manager, and to use the neat manager RutilT instead.


Follow the steps in [http://ubuntuforums.org/showthread.php?t=554089](http://ubuntuforums.org/showthread.php?t=554089)  (thanks to the excellent HOWTO by Sulligogs for this)

You will need to make a few changes:

In step 5:

[LIST]
[*]Change '# RT61' to '# RT2500'.
[/LIST]

[LIST]
[*]Even though you will be running the wireless NIC as DCHP, do add an IP address etc etc as described.  To find your your IP address etc do ifconfig; 'Inet address' in ifconfig is 'Address'; 'mask' is the 'Netmask'; and you will need to find out the IP address of your router (probably 1 below Inet address if only your PC is on in the whole system).
[/LIST]

In step 8:

[LIST]
[*]Carry out the steps to make sure that RutilT is loaded each time, but also refer to post #3. I would suggest running as DHCP, so enter rutilt -dp .
[/LIST]

It should now work, but I needed (in Fiesty) to go into System > Administration> Network and click the Wireless Connection Properties, untick Enable roaming mode, put in your SSID name and set configuration  to Automatic configuration (DHCP).  Even though you may be adding encryption, do it in RutilT not here.
You may not need to do this, but I put it in to assist.

---

