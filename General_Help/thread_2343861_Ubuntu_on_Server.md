---
title: "Ubuntu on Server"
date: 2016-11-20
forum: General Help
---

### Post by dshah on 2016-11-20
Hi

I would like to know which edition should I install on my server which will host 10 thin clients? Server version or Desktop version?

I need GUI on server and also this setup is for office envoirment, we will use thin clients for office softwares, internet and development pruposes.


Thanks for any input

---

### Post by deadflowr on 2016-11-20
Use server version.
You can install a basic desktop when you also install the server functions you need for the thin clients.
That way when you restart into it, all will be at the ready.

The Desktop version will have unwanted/unneeded junk, and also not have needed/wanted junk.
And because of that, you'll have to do some extra work post-install to set everything up.

---

### Post by HermanAB on 2016-11-20
Concur with above.  Use server version, then install xfce desktop if you want.

---

### Post by dshah on 2016-11-20
Thanks...... I download server version image, burned on a CD and now when I try to boot from CD I get below error:

**EDD: Error 0100 reading sector 70030**
**no default or ui configuration directive found **

---

### Post by dshah on 2016-11-20
I will try with USB

Also another question, I noticed there is an enterprise version for HP? HP Moonshot 14.04 LTS?
Should I use that one for HP servers or normal 16.04 LTSs server version?

I have 32 GB DDR4 Ram, Intel Xeon E3-1225v5

My Server Specification:
> 
HPE PROLIANT ML10 SERVER 838124-425 &#8226; Model:HPE ProLiant ML10 Generation9 (Gen9)&#8226; CPU: Intel Xeon E3-1225v5 (3.3GHz/4-core/80W)Processor Kit&#8226; &#924;emory: 4 x HPE 8GB Single Rank x8 PC4-17000P-E(DDR-2133) Unbuffered CAS-15 Standard Memory Kit&#8226; HDD: 2x HP 1TB 6G 7.2k rpm SATA (3.5in) Non-HotPlug MDL HDD 1yr Warranty (up to 4 NHP LFF SATA)&#8226; Power supply: 1 x HPE 300W Multi-Output PowerSupply Kit&#8226; Optical Drives: HP 9.5mm SATA DVD-RW JackBlackGen9 Optical Drive&#8226; LAN: Intel Ethernet Connection I219-LM&#8226; Interfaces: 2x display port, 1 Network RJ-45, 4x USB3.0, 3x USB 2.0&#8226; Storage Controller: Intel RST controller (RAID0/1/1+0/5) SATA Only

---

### Post by dshah on 2016-11-20
I burned Ubuntu Server 16.04 LTS version to USB and this error comes up when trying to boot from USB:

**no default or ui configuration directive found**

---

### Post by dshah on 2016-11-22
I was able to install it via USB.

---

