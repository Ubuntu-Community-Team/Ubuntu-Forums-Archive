---
title: "Enabling NVIDIA driver causes freeze / lock up"
date: 2007-09-29
forum: General Help
---

### Post by samurijim on 2007-09-29
I recently downloaded the Ubuntu 7.04 Desktop and installed it on a 2.0Ghz Pentium 4 system that has 512MB Ram.

Everything seems to be running normally, that is until I enable the “NVIDIA accelerated graphics driver”. I have a GeForce4 MX 440 graphics card in the system. Once I enable it the desktop runs fine for maybe 10 seconds, but then freezes / locks up. I reboot and try again, same problem after a few seconds of using the system. I was finally able to turn off the driver (under Restricted Drivers) before it locked, and now it’s running peachy. So this is obviously the cause of the problem.

I searched the web for linux drivers, thinking that the ones that came with Unbuntu were the issue. Didn’t really come across anything usefull. NVIDIA’s Site has a page for my card here: ttp://www.nvidia.com/page/geforce4mx.html . No mention of a driver. Their driver download page only has GeForce 8-6 Series, what good does that do me? I tried to download the Linux version anyway, and it gives me this program to install: NVIDIA-Linux-x86-100.14.19-pkg1.run . When I click to open the program, Ubuntu says it can’t run it.

So, what now? Anyone have any ideas? I can keep using the system as is, but then I don’t have any 3D support, and I do want to play games on it. I hate to turn the system back to Windows, but at least the drivers worked then. Any help would be much appreciated.

~ James

---

### Post by FuturePilot on 2007-09-29
The easiest way to install the driver if you don't want the one from the repos, is with [Envy]("http://albertomilone.com/nvidia_scripts1.html")
Don't try to install that driver that you downloaded because it doesn't support your card. You'll just end up with a broken X.
But I have a feeling this is more than just a driver issue. I was also getting these random freezes. Try this immediately after logging in
```
sudo /etc/init.d/powernowd stop
``` 
This stops the powernow daemon which controls CPU scaling. From what I have gathered the Nvidia driver doesn't always agree well with CPU scaling especially with lower end cards. If you have anything in your BIOS for CPU scaling you might want to disable that also. See if that stops the freezing.

---

### Post by samurijim on 2007-10-01
Thanks for the advice. I'll give that a try and post the results.

---

