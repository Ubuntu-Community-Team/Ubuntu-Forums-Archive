---
title: "Wan WiFi Question"
date: 2007-08-13
forum: General Help
---

### Post by cssutto on 2007-08-13
A dumb question, but I know not how to use either.

I bought a Kyocera Router.  I can use it with the Ethernet cable and by going through the KR1 web page to turn it on, but I can not figure out how to use wan or WiFi to talk to the router.

In fact, I don't even understand the difference between WAN and WiFi.

I know that I have the WAN hardware because it is in my order spec sheet for the computer when purchased and is confirmed by Lenovo.

So how do I turn on WAN so as to do away with the Ethernet cable?

CSSJR

---

### Post by aldenhg on 2007-08-14
WAN = **W**ide **A**rea **N**etwork. This more or less refers to the internet. 
WiFi  = **Wi**reless **Fi**delity. This is kind of a dumb industry term in my opinion and in fact refers to a WLAN.
WLAN = **W**ireless **L**ocal **A**rea **N**etwork. A small wireless network, not to be confused with the wide area wireless networks provided by some cellular carriers. A WLAN (WiFi) is generally used in conjunction with a boradband connection of some sort, such as cable or DSL. The way that a WLAN is created is by pluging in a wireless router and configuring it. These are then connected to by a wireless adapter.

I hope I didn't talk down to you at all there. If you're looking to turn on the wireless capabilities of your router, the first thing to do would be to confirm that you do indeed have a wireless router. Post the model number here and I can give you specific instructions.

---

### Post by cssutto on 2007-08-14
Thanks for the reply.

The router is a Kyocera KR1.

CSSJR

---

### Post by cssutto on 2007-08-14
I should have mentioned that I am running 6.06 and that I tried the wireless assistant, which said there was no usable wireless equipment found.

I guess I will have to boot up XP, which I hate hate hate hate to see if I do have what I think I have in my laptop.


CSSJR

---

### Post by aldenhg on 2007-08-14
It seems like you'd be best off with a link to the manual. It has all the steps to configuring your wireless network.
[http://www.kyocera-wireless.com/kr1-router/pdf/kr1_router_userguide_english.pdf](http://www.kyocera-wireless.com/kr1-router/pdf/kr1_router_userguide_english.pdf)
If you have any questions, feel free to ask.

---

### Post by cssutto on 2007-08-14
I have the CD.

The problem is not with the KR1.  

The problem is that I can not turn on WiFi on my laptop.

In the meantime I booted XP and it confirmed that I have WiFi and it connected.

I could not get anywhere with Explorer though because it was not set up correctly.

So what I need is a means of activating the WiFi feature in my machine.
CSSJR

---

### Post by aldenhg on 2007-08-14
Ohhhhhhh ok. Well, do you know what kind of wireless card you have? If not, post the output of lspci when you run it in a terminal.

---

### Post by cssutto on 2007-08-14
claude69694@claude69694:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03 )
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev  03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  3 (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  4 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Co ntroller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridg e (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controlle r (rev 02)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Stora ge Controllers cc=AHCI (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev  02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71d 4
0000:02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Cont roller
0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controlle r
claude69694@claude69694:~$

---

### Post by aldenhg on 2007-08-14
0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
That's the important part right there. That's your wireless adapter. It looks like the drivers should be in the Restricted Drivers manager. If you haven't already, try starting up said manager From the System -> Administration menu. Select the drivers and you should be good to go after a reboot.
If not, type uname -r into the terminal. I've heard that the driver is missing from the 2.6.20-16 kernels, so jumping back to the -15 might help. It should be available from the grub menu (hit escape during boot when prompted to).

---

### Post by cssutto on 2007-08-14
I don't have a drivers manager in systems.administration.

CSSJR

---

### Post by aldenhg on 2007-08-14
Are you running KDE or Gnome? If it's KDE, I don't quite know where the Restricted Drivers manager is. If not, make sure that you're going to the menu at the top of your screen.
If you still can't get it running, you're probably going to have to use ndiswrapper. Ndiswrapper uses the Windows drivers with a compatability layer to make them work with Linux. check out this link for some instructions.
[http://ubuntuforums.org/showthread.php?t=429537](http://ubuntuforums.org/showthread.php?t=429537)

---

### Post by cssutto on 2007-08-14
I am running Gnome.

CSSJR

---

