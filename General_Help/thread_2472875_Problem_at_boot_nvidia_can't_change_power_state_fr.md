---
title: "Problem at boot: nvidia can't change power state from d3cold to d0 (config space inac"
date: 2022-03-15
forum: General Help
---

### Post by bobthesob on 2022-03-15
Hi!

At start booting sometimes halts and I get the error message "Nvidia 0000:01:00.0: can't change power state from d3cold to d0 (config space inaccessible)" and then the booting just halts. Sometimes it boots but when I enter the password at the log on screen it freezes again. If I reboot one or two times everything works fine but it's very annoying. Anyone have any suggestions?

Specs
Ubuntu 21:10
ASUS TUF Gaming FX506LI-HN012T
NVIDIA® GeForce® GTX 1650 Ti
                                                                                                                                                                                                                                                                                                              i5-10300H                                                                                                                                                   

Intel Core i5                                                                                                                                                   

                                         

Thanks in advance

---

### Post by Autodave on 2022-03-15
What driver for nVidia are you using?  Where did you get that driver?

---

### Post by bobthesob on 2022-03-15
They should be the native ones if I haven't played around with it when I tried to fix the issue a while back (was a couple of months ago and my meory sucks) but the issue has been there since I installed ubuntu on this computer.

"sudo lshw -c video" gives:

*-display                 
       description: VGA compatible controller
       product: CometLake-H GT2 [UHD Graphics]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: driver=i915 latency=0

---

### Post by bobthesob on 2022-03-29
Reinstalled once more an made sure I use the X.org X Server. Works like a charm.

---

