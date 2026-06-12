---
title: "Wireless and sound have gone."
date: 2008-05-11
forum: General Help
---

### Post by cometa2k7 on 2008-05-11
I have Ubuntu Hardy on my computer, but after a couple of updates, my wireless has stopped working, along wih my sound.

I can get a wired connection to work, but it's a pain having a cable running all of the way up the stairs.

I have tried downgrading everything that was upgraded using synaptic, but it still doesn't work.

Also, my sound has stopped working, it just says that> No volume control GStreamer plugins and/or devices found.

I need help.

---

### Post by ghost_ryder35 on 2008-05-11
need to know what type of hardware your running, please post ouputs of
```

ifconfig
iwlist
lspci

```

---

### Post by cometa2k7 on 2008-05-11
The top part of this is my wired connection which I have runnin temporarily.

> nathan@nathan-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0b:db:8d:8f:90  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe8d:8f90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:22871 (22.3 KB)  TX bytes:20844 (20.3 KB)
          Base address:0xdf40 Memory:feae0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1960 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98000 (95.7 KB)  TX bytes:98000 (95.7 KB)


iwlist just gave a list of usages.

> nathan@nathan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
nathan@nathan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)


---

### Post by ghost_ryder35 on 2008-05-11
what type of wireless card do you have?  if its wireless
```

lsusb

```

---

### Post by cometa2k7 on 2008-05-11
It's a Belkin Wireless G USB Network Adapter

It works in Ubuntu, and on the other OS's I've tried. I had it working last night, and it has been installed and working for quite a while.

> nathan@nathan-desktop:~$ lsusb
Bus 005 Device 003: ID 050d:705c Belkin Components 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


---

### Post by james_vanb on 2008-05-11
I've always had to use ndiswrapper to get my Belkin USB to work.  Not sure why an update would take it out, but if you have the install cd, you might want to try reinstalling the driver.  I do the following:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules (or gedit if using ubuntu)

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

This also worked for a Zonet ZEW 1502, without blacklisting anything.

Good luck.

---

### Post by cometa2k7 on 2008-05-11
Nope, doesn't work for me. And I've always managed to use the zd1211rw drivers to run my wireless. I used ndiswrapper a little on PCLinuxOS2007, but with Ubuntu, it just worked. Then just stopped.

However, my sound is working again, after booting to the "generic" kernel, and not the "386" one. I hadn't realised that I'd installed the "386" one, but uninstalling it made the sound work. Not the wireless though.

---

### Post by james_vanb on 2008-05-11
Just saw this Thread on the zd1211rw.  Seems you are not the only one having some issues.  Maybe a solution is here?

[http://ubuntuforums.org/showthread.php?t=774774&highlight=belkin+usb](http://ubuntuforums.org/showthread.php?t=774774&highlight=belkin+usb)

---

### Post by cometa2k7 on 2008-05-15
> **james_vanb said:**
> Just saw this Thread on the zd1211rw.  Seems you are not the only one having some issues.  Maybe a solution is here?

[http://ubuntuforums.org/showthread.php?t=774774&highlight=belkin+usb](http://ubuntuforums.org/showthread.php?t=774774&highlight=belkin+usb)

Thanks for the info, but my problem is slightly different to this. My card worked fine in Hardy to start with, it just stopped, and has messed up. I might find a fix in there, so I'll keep checking it.

---

