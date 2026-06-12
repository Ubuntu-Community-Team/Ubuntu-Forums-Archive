---
title: "Is Linux eSATA friendly?"
date: 2015-06-07
forum: General Help
---

### Post by gr8 on 2015-06-07
I'm planning on buying an eSATA docking station, plunking some huge hard drive on top of it, then running an eSATA cable from the docking station to my motherboard through a hole I drilled in my case (it looks nice, trust me).

Will this work or am I going to get some Linux driver issue or some other weird BIOS this or that.

---

### Post by Bucky Ball on 2015-06-08
You don't have eSATA connection on the back of the case? If it is a desktop, you should have. You run a cable from the SATA connection on the motherboard to the connector pins. I can't see why you're plan won't work and yes, Ubuntu is eSATA friendly. Just plug it in.

Just remember, though, that the plug on the motherboard is not eSATA, it is SATA. Don't get the two confused. The plugs are slightly different. You are going to need a cable with eSATA connector on one end and SATA connector on the other. Read [this]("https://en.wikipedia.org/wiki/Serial_ATA#Cables.2C_connectors.2C_and_ports"). I guess you can get SATA> eSATA cables. Never tried myself. ;)

---

### Post by sudodus on 2015-06-08
Yes, linux is eSATA friendly. I even boot from an SSD in an external USB 3 and eSATA box :-)

In a desktop you can get an adapter like this (cheap and simple and reliable)

[http://www.startech.com/Cables/Drive/eSATA/2-port-SATA-to-ESATA-Slot-Plate-MF~ESATAPLATE2](http://www.startech.com/Cables/Drive/eSATA/2-port-SATA-to-ESATA-Slot-Plate-MF~ESATAPLATE2)

---

### Post by Bucky Ball on 2015-06-08
> **sudodus said:**
> 

[http://www.startech.com/Cables/Drive/eSATA/2-port-SATA-to-ESATA-Slot-Plate-MF~ESATAPLATE2](http://www.startech.com/Cables/Drive/eSATA/2-port-SATA-to-ESATA-Slot-Plate-MF~ESATAPLATE2)

Yep, just the ticket. ;)

Mount in the back of your motherboard case, plug the device into one or two SATA ports on the mother board then use the eSATA cable to attach your external drives to it. This is same setup my motherboard came with 'off the shelf'. The adapter is built in with a couple of eSATA ports on the back of the case, so no need for installing a third-party adapter.

---

