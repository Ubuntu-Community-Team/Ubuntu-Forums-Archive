---
title: "Decent computer specs, bad performance in Ubuntu 12.10"
date: 2012-10-29
forum: General Help
---

### Post by fatsam on 2012-10-29
Hey fellas. So I've been using 12.10 since release and have just only started testing the GPU performance with the Unigen Heaven Benchmark DX11 tool. On Windows my system chews through it comfortably with crossfire enabled but after trying it for the first time on Ubuntu 12.10 the performance was terrible, like my cards weren't even working. I was getting 1-4 fps.

Here are my specifications:

CPU: Intel i7 920 @ 3.6Ghz
GPU: Radeon 5850 CF (1 Standard edition, 1 OC edition)
RAM: 1600MHz 6GB 9-9-9-24
HDD: WD 808GB
PSU: Antec EarthWatts 750w

These are the most recent changes I have made in Ubuntu 12.10:

- Installed the latest ATI Radeon Drivers from their website with Crossfire enabled
- Running AMDOverdriveCtrl
- Running Psensor 

With AMDOverdriveCtrl I have bumped up the Overdrive of my first card to match my OC edition card which works like a charm in Windows 7.

Also, is there anyway to see the GPU usage on both cards or a way to tell if the crossfire is working?

Regards,

Fats

---

### Post by Yellow Pasque on 2012-10-29
First, try the fglrx/Catalyst from the repo. If that doesn't work, try installing manually (but you must use Catalyst 12-11 beta, as that's the only version that's going to work with Quantal).
See the instructions: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

---

### Post by fatsam on 2012-10-29
> **Temüjin said:**
> First, try the fglrx/Catalyst from the repo. If that doesn't work, try installing manually (but you must use Catalyst 12-11 beta, as that's the only version that's going to work with Quantal).
See the instructions: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

Cheers will do this now.

---

