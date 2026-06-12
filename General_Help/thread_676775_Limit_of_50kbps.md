---
title: "Limit of 50kbps"
date: 2008-01-24
forum: General Help
---

### Post by fumbles on 2008-01-24
Hello, 

I cannot seem to download anything faster then 50kBps. My internet connection is 1.5Mbps ADSL so I should be getting 160kBps. If I have two things download simultaneously I can get a max of 90-100kBps. This goes for updating, downloading with firefox, wget etc. 

I'm new to Ubuntu, I just installed 7.10 about five minutes ago. I do not have this problem with Windows Vista and Windows XP (the other two OSs I run). Previously I was running Arch Linux x64, which had the same problem. I'm hoping its not a hardware issue as Windows is untouched. However this hasn't always been a problem. 

Motherboard: Asus A8N SLi Premium 
NIC1: Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
NIC2: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13) [NOT IN USE]
Kernel: 2.6.22-14-generic 
Arch: x86_64
Ver: 7.10

Thanks.

---

### Post by peabody on 2008-01-24
Have you tried running online bandwidth tests in Windows and Linux?

[http://www.dslreports.com/stest](http://www.dslreports.com/stest)

Would give us more believable benchmarks to compare.

---

### Post by fumbles on 2008-01-24
> **peabody said:**
> Have you tried running online bandwidth tests in Windows and Linux?

[http://www.dslreports.com/stest](http://www.dslreports.com/stest)

Would give us more believable benchmarks to compare.



Your line speed is 337 kbps (0.34 Mbps).
Your download speed is 42 KB/s (0.04 MB/s).

Windows is 160kBps, which is what its meant to be...

---

### Post by peabody on 2008-01-24
Just so we're on the right page here...

334 Kbps vs 160 kBps, that is windows is getting around 1.28Mbps correct?

That's quite a disparity.  Do you have a usb wifi stick you could try with the machine to see if you could get better thoroughput through a different network interface?  It might be a driver issue...

---

### Post by c0met on 2008-01-24
I have a 1.5 Mbps internet connection and regularly get 160 KBps (or better) on Ubuntu 7.10. I don't know if this helps, but under System >> Adminstration >> Network, I have "Roaming Mode" enabled.

---

### Post by fumbles on 2008-01-24
> **peabody said:**
> Just so we're on the right page here...

334 Kbps vs 160 kBps, that is windows is getting around 1.28Mbps correct?

That's quite a disparity.  Do you have a usb wifi stick you could try with the machine to see if you could get better thoroughput through a different network interface?  It might be a driver issue...

Yeah about 1.28Mbps with Windows, and not even half that in Linux. 
Unfortunately I don't have any wireless usb/pci interfaces, but I do have to onboard NICs. The bad part is the other one is stuffed, for some reason it cannot get an IP address, Windows Linux or whatever. It always ends up with one of those rubbish ones: 169.254.x.x. 
I'd hope this problem would go away when I switch distro to Ubuntu. A driver issue sounds like it could be the case. Maybe try an old kernel or something?
 
> **c0met said:**
> I have a 1.5 Mbps internet connection and regularly get 160 KBps (or better) on Ubuntu 7.10. I don't know if this helps, but under System >> Adminstration >> Network, I have "Roaming Mode" enabled.

Yes roaming mode is enabled, I've only just installed it so everything is at its defaults. Thanks for the idea though, I'm not sure what 'Roaming mode' means.

---

