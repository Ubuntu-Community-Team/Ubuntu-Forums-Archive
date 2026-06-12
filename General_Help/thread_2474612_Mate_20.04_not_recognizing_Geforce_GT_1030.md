---
title: "Mate 20.04 not recognizing Geforce GT 1030"
date: 2022-05-03
forum: General Help
---

### Post by SciGuy1872 on 2022-05-03
Hi.  I have a Dell Latitude e5420 and have used an eGPU to connect a Geforce GT 1030--the fan on the card is running, so I think the card is getting power.  I have the eGPU (Beast Dock V8.0) attached to my computer by an HDMI cable.  But the computer doesn't recognize that the card is attached--if I run ```
lshw -c display
```, then I get ```
 *-display                 
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:e1c00000-e1ffffff memory:d0000000-dfffffff ioport:7000(size=64) memory:c0000-dffff

```   

What do I need to do to get the computer to recognize that the card is attached--I have downloaded the driver from Nvidia and tried to install it; I am told that no Nvidia cards are recognized and that I need to disable X.  I think the process is to recognize the card, install the driver, then blacklist Noveau.  What do  I need to do?

---

### Post by Frogs Hair on 2022-05-04
Before installing any driver from the internet, open software sources - additional drivers and check for drivers there.

---

### Post by SciGuy1872 on 2022-05-04
The only driver listed there is the wifi.  The computer doesn't detect the graphics card at all--doesn't list there or when I run the lshw command.  Maybe it's the connections with the GDC v8--the two ports are connected with their proper pin number counterpart, the fan on the GPU is running, and a green light is on in the internals of the eGPU.  I think I remember reading about switches along the port for the graphics card--am I right?  Do these need to be changed?

---

### Post by SciGuy1872 on 2022-05-04
Ok.  Cleared the mistake I made by trying to use the HDMI port to the computers HDMI port -- I thought the HDMI was a newer technology than an old expresscard interface and would be a better transfer rate  The os had to be running,  then i connected the GDC by expresscard, and then the computer saw the gt 1030 and i was able to go to Additional Drivers.

---

