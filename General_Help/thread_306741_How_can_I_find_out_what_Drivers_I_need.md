---
title: "How can I find out what Drivers I need?"
date: 2006-11-25
forum: General Help
---

### Post by thenetduck on 2006-11-25
HI, 
  I am running a computer that I am trying to get set up for my parents. I was wondering how I would find the drivers for my graphics card. The card is on the motherboard. Thanks,
 
 The Net Duck

---

### Post by taurus on 2006-11-25
Applications -> Accessories -> Terminal
```
lspci
lsmod
```[/code]

---

### Post by thenetduck on 2006-11-25
Ok lspci gives me this

```

00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:0e.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)


```


 Does anyone know what dirvers I now need to install? and how I would find a how to to install the drivers?? Thanks, 
 
The Net Duck

---

### Post by taurus on 2006-11-25
Your onboard graphic card is "Intel Corporation 82810 CGC [Chipset Graphics Controller]" and I believe you can use "815resolution" (or even "915resolution")driver for it.  It's available in the repos after you enable both universe & multiverse in /etc/apt/sources.list...

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by thenetduck on 2006-11-25
Ok so I just do something like sudo apt-get install 815resolution .... ?
 I couldn't find any information about getting or installing the drivers, however I did enable the repositories successfully. 

 Thanks, 

 The Net Duck

---

### Post by taurus on 2006-11-25
You need to edit your /etc/apt/sources.list and remove the # in front of the lines that have universe & multiverse in them...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude install 815resolution
```

---

### Post by theparoxysm on 2008-03-02
I have an older laptop, an 02' IBM Thinkpad, G40.

It recognized the in-keyboard joystick style mouse, but not some usb ports, and wifi/etc other things.  Is there a good way to search for everything that needs drivers or can have better drivers?

Also, it says I have no connectivity, so unless this forum is locatedly natively I believe that is wrong.

Anyway to see what's going on there too?

---

