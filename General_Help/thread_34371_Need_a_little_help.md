---
title: "Need a little help"
date: 2005-05-14
forum: General Help
---

### Post by blu.gecko on 2005-05-14
Ok,

I am new to linux, I downloaded Ubuntu 5.0.4 and installed it without any issues on a new Compaq Presario 2210US, I got Ndiswarpper up and running, I would like to Install Vmware so I can continue to run Netstumbler, or if there is a equiv. application, I tried Kismet, lets just say I got some server errors I dont understand, and I would like to be able to scan all bands B/A/G, I use wifi Radar to connect, all I know how to do is dpkg at this point. I like vmware, or what I have seen of it so far, I found this posting 

[http://software.newsforge.com/software/05/04/27/186203.shtml?tid=130](http://software.newsforge.com/software/05/04/27/186203.shtml?tid=130)

[http://www.newsforge.com/blob.pl?id=abc4ed2754e01a01ef177b85d4e75dd9](http://www.newsforge.com/blob.pl?id=abc4ed2754e01a01ef177b85d4e75dd9)

---

### Post by monchichi on 2005-05-14
Installing VMWare just to run netstumbler is overkill! VMWare emulates system hardware so that you can run an entire operating system inside of another one. If you just have to run a windows program, run it with Wine, but I doubt it would work very well with wireless hardware. ([http://winehq.com)](http://winehq.com)), installation:```
sudo apt-get install wine
```I don't know of any linux wireless programs with better functionality than Kismet.

---

### Post by bruizer on 2005-05-15
Did you run from term? What were the errors?

---

### Post by bruizer on 2005-05-15
I've been trying to install also, and after installing through Synaptic, I get this when trying to run:
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (ciscosource): Enabling monitor mode for cisco source interface eth0...
FATAL: Unable to open cisco control file '/proc/driver/aironet/eth0/Config' 2:No such file or directory

I opened the kismet.conf file and was looking at the sources directive, and then went to Kismet site and found this in the README:

    Chipsets known to NOT WORK:
     Broadcom           - No linux drivers, only useable with ndiswrapper or
                          linuxant wrappers around windows drivers.
     Airport Extreme    - Really a Broadcom, with no rfmon in the OSX drivers.
     Atmel              - There is a hack for pseudo-monitor in USB.  There is
                          currently no equivalent hack for PCMCIA.
     HermesII           - Proxim successor to the Orinoco/HermesI.  No support
                          yet in the drivers, may be available in the future.
     ipw2200            - Intel 2200 802.11g/Centrino-G cards.  Similar to the
                          ipw2100s, but the drivers currently do NOT support
                          monitor mode.  Once they do, support will be added.

I am currently using a Dell TrueMobile 1400 (Broadcom... so it won't work). It looks like you are using Windoze drivers also, you may want to read up on you chipset through the Kismet site:
[http://www.kismetwireless.net/documentation.shtml#readme](http://www.kismetwireless.net/documentation.shtml#readme)


Anyone have some insight on how to get this working?

---

### Post by Staesys on 2005-05-15
NetStumbler does indeed run with WINE, but at least in my case, it can't find the network adaptor.

---

### Post by blu.gecko on 2005-05-15
I like Netstumbler, It gives me all the details I want like "fake" router type and info, Kismet gives me ? it scans for B only. I use Wifi-Radar and my wireless wont connect to weak signals like my Windozs will, its becoming to be my big debate....

---

### Post by monchichi on 2005-05-18
Kismet can scan B, A, and G.

If you want to connect to weak or barely-existent signals, try using the command line tools "iwlist" "iwspy" "iwconfig"

---

### Post by bruizer on 2005-05-18
Kismet is still not playing nicely with me. I also seem to be having the same problem with Airsnort.... I gues it just doesn't like the Broadcom chipsets

---

### Post by aldenhg on 2007-08-10
In my experience, Kismet straight up won't work with ndiswrapper - or at least not with Broadcom chips.

---

