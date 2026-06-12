---
title: "[SOLVED] Wireless Freezing Laptop"
date: 2008-03-16
forum: General Help
---

### Post by ultraloveninja on 2008-03-16
So, I've been digging around trying to find some resolution to this issue, but I am coming up empty handed.

I have a realtek wireless card in my Gateway laptop and I've v7.10 installed.  When try to connect to a wireless network, the laptop locks up completely and I have to reboot.

Tried to do a manual config as well, and that doesn't even connect to the network at all.

Not too sure what the issue is.  I've tried to look up some answers, but coming up with some dead ends.

Also, why is it I cannot choose WPA either?

I even tried to install the latest release of the linux drivers from realtek and i am not sure that it did anything either.

Any help would be awesome.
Thanks!

---

### Post by penguinpi.com on 2008-03-17
open the terminal and type lscpi and post what it outputs.

---

### Post by ultraloveninja on 2008-03-17
bash: lscpi: command not found

---

### Post by penguinpi.com on 2008-03-18
Sorry, my bad the command is lspci  duh!

---

### Post by ultraloveninja on 2008-03-18
It's kuhl...
Here ya go:
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

---

### Post by lswest on 2008-03-18
can you post the output of ```
lshw -C network
``` please? it will tell us what drivers are being used for the card at the moment.

---

### Post by penguinpi.com on 2008-03-18
Is it in your restricted drivers manager? and if so is it enabled?

---

### Post by ultraloveninja on 2008-03-18
here is the output:
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:03:25:42:5e:47
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.0.65 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:08:09.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:d3:f2:d7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g

and no, it is not listed in the restricted drivers manager.

---

### Post by penguinpi.com on 2008-03-18
See if this helps

[http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page)

---

### Post by ultraloveninja on 2008-03-18
i did see that, but i was just wondering if there was any way to install the drivers with out having to install the svn-tortise stuff.  but if that's what gots to do in order for it to work, then i guess i have to.

---

### Post by alan34 on 2008-03-18
Have a look at my post on the thread. It worked when I did on my pc but no feed back on this thread. 
Wish people would say (moan).

[http://ubuntuforums.org/showthread.php?t=726188](http://ubuntuforums.org/showthread.php?t=726188)

Good luck

---

### Post by ultraloveninja on 2008-03-18
kuhl.

Thanks for all the help/resources everyone.

I am gonna give that a try and see what happens.

---

### Post by ultraloveninja on 2008-03-21
Wellm everything was going good till I got to this part:

sudo ndiswrapper -l

Which gave me this:

net8185 : invalid driver!


So...yeah.
I got nada.

---

### Post by ultraloveninja on 2008-03-22
anyone???

---

### Post by ultraloveninja on 2008-03-22
ok...i figured it out and i got it to work.

here is what i did. much is similar to the blacklist method, but with a little twist:

i got the WINXP drivers from realtek's site downloaded them to the desktop for the time being.

i then went to the synaptic package manager and installed the ndiswrapper.

i also made sure that i was able to un-package the RAR file.  You might have to download that from the Add/Remove programs in order get to the WINXP folder that was in the folder that you downloaded from the realtek website.

if you go through all the steps and get an error like i did telling you that its already installed then you have to remove it from not only your username prompt but from your root level as well. 

so, i removed it while i was still in WINXP folder which was on my desktop in both my username and then in  root (sudo su - [ENTER], it will ask for your password then).

so, i removed it while i was still in WINXP folder which was on my desktop in my username:

```

nsidwrapper -r net8185

```

I checked to be sure it was gone:

```

ndiswrapper -l

```

and got nothing there.

Then I repeated the same process as "root" just to be sure the driver was completely uninstalled..

after i did that, i moved the WINXP folder from the desktop to the tmp folder directory.  while i was still in root i changed into the directory:

```

cd /tmp/WINXP

```

type ndiswrapper -i net8185.inf in the folder where you extracted the driver files hit enter. next ndiswrapper -l shows net8185.  it should then show that the driver is installed along with the alternate driver of the r8180, which is prolly the reason why it kept crashing when i tried to conncet to anything via the wireless. so then it should look like this:

```

device (10EC:8185) present (alternate driver: r8180)

```

after that you can proceed to add the ndiswrapper on boot and blacklist the old r8180 driver so that it doesn't use it anymore.  i closed out my current terminal of when i was in root and went back to my username.

to load the driver when you boot:

```

sudo gedit /etc/modules

```

----------You should see something like this add ndiswrapper at the end of the file--------

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

```


blacklist the linux driver:


```

sudo gedit /etc/modprobe.d/blacklist

```


---------------At the end of the file add------



```

# wireless network card driver
blacklist r8180

```

Reboot and see if it worked.

Overall, you gotta make sure that if you are having issues trying to install the Realtek 8185 drivers is to make sure that it's completely removed in both your username and in root, and to just install it via root.

---

