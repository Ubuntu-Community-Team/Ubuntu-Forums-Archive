---
title: "ubuntu 12.04.04 Desktio 64bit"
date: 2014-02-26
forum: General Help
---

### Post by Rakesh_vijayan on 2014-02-26
Hi friends when I installed ubuntu 12.04.04 Desktio 64bit the new LTS . package installation get slow . I tested if these cause of internet connection with deluge I got 1mbps downlaod speed  . how can i resolve this issue is this version

---

### Post by mastablasta on 2014-02-26
you could try and change the repository server (in software ceter) to another one. if that is what you mean?

I once updated and got really slow connection. i then moved to another mirror and it was all fast again.

---

### Post by Rakesh_vijayan on 2014-02-26
> **mastablasta said:**
> you could try and change the repository server (in software ceter) to another one. if that is what you mean?

I once updated and got really slow connection. i then moved to another mirror and it was all fast again.
I tried what you said but installation speed have no change .... what will be the problem for this version I have never meet like this in my ubuntu experiance . This make real frustrating

---

### Post by Rakesh_vijayan on 2014-02-27
why nobody replay for this post is this problem only cuase for me  or  entire world what heppen in 12.04 64 bit . package installation get slow  . I tried both 12.04 .3,4 both are same preformance .Only problem presist for install packages and upgrading ubuntu . Downloading (wget  [http://download.virtualbox.org/virtualbox/4.3.8/virtualbox-4.3_4.3.8-92456~Ubuntu~precise_amd64.deb](http://download.virtualbox.org/virtualbox/4.3.8/virtualbox-4.3_4.3.8-92456~Ubuntu~precise_amd64.deb)) which gives me 1mps speed .The problem may happen in server bandwidth problem

---

### Post by deadflowr on 2014-02-27
No, doesn''t happen to me, at least.
What is the speed you would expect?

Have you been running other versions of Ubuntu?
What speeds do they get?

Can you provide any info on your network adapters/cards?

---

### Post by Rakesh_vijayan on 2014-03-07
> **deadflowr said:**
> No, doesn''t happen to me, at least.
What is the speed you would expect?

Have you been running other versions of Ubuntu?
What speeds do they get?

Can you provide any info on your network adapters/cards?


I expect atleast more than 500 kb because 32 bit ubuntu12.04 povides me more than 700kbps .I change this to 64bit for use proxmox appliction 

Below is my card Information 

```
root@ns:/home/nadeen# sudo lshw -class network
SCSI                      
  *-network        
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 00:26:6c:dd:72:a1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=10.2.2.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:c0500000-c053ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:de:2b:45:e2:63
       width: 64 bits
       clock: 33MHz


```

---

### Post by 3rdalbum on 2014-03-07
Rakesh: I assume from your name that you live in India?

The Indian mirrors for Ubuntu are slow at times, and tend to be more unreliable than other mirrors hosted in other countries.

Go into Ubuntu Software Centre. Go to the menubar at the top of the screen and go to the Edit menu, then come down to Software Sources.

Where it says "Download from: " click on the popup menu and choose Main Server. Click Close and then click Reload in the box that pops up. You should have good package installation speed now.

---

### Post by Rakesh_vijayan on 2014-03-15
> **3rdalbum said:**
> Rakesh: I assume from your name that you live in India?

The Indian mirrors for Ubuntu are slow at times, and tend to be more unreliable than other mirrors hosted in other countries.

Go into Ubuntu Software Centre. Go to the menubar at the top of the screen and go to the Edit menu, then come down to Software Sources.

Where it says "Download from: " click on the popup menu and choose Main Server. Click Close and then click Reload in the box that pops up. You should have good package installation speed now.

Thanks for your replay yes "I am leaving in India" . when I Install a new ubuntu this step I usualy follow since when I using ubuntu , Is there any alternative  way to get speed for installing packages

---

### Post by deadflowr on 2014-03-15
[apt-fast]("http://www.webupd8.org/2012/10/speed-up-apt-get-downloads-with-apt.html"), maybe?

But that's all about downloading the packages.
If the issue is actual installation of packages, then that depends on the strength of the machine.

---

### Post by Rakesh_vijayan on 2014-03-19
I think the problem is on my lan card driver , when I tried with wifi I get full speed , like my past 32 bit os ,How can I verify my lan card problem

---

