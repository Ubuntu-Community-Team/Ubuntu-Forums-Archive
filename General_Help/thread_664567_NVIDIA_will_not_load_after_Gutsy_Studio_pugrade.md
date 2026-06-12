---
title: "NVIDIA will not load after Gutsy Studio pugrade"
date: 2008-01-11
forum: General Help
---

### Post by reja on 2008-01-11
After successfully running Gutsy and Gutsy studio without the audio packages, I decided to install the Studio audio packages. On reboot, I get:

FATAL error running install command for NVIDIA
Failed to load the NVIDIA kernel module

I tried:

sudo apt-get install linux-generic
and was told it was already installed. Then tried:

sudo apt-get install nvidia-glx
and was told that it was not found.

All I get now on booting, after going thru error messages, is the equivalent of a Windows command prompt (recent linux/ubuntu convert) -- terminal?. Am not sure how to download and install packages/ modules from this, and am definitely not sure which ones to get. 

Card is a NVIDIA Quadro 4 280 NVS with dual monitor output (only one is attached).  Monitor is 1440 x 900 resolution.  AMD 1.3g 32 bit processor.

Thanks for any help.

---

### Post by reja on 2008-01-11
At the startup boot menu, I tried:

Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)

and got:
using config file: "/etc/x11/xorg.conf"
module already built in
FATAL: Error running install command for NVIDIA
(EE) NVIDIA (0): Failed to load the NVIDIA kernel module
(EE) Screen(s) found, but none have a usable configuration
Fatal server error: no screens found

I then rebooted into
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

and was able to start Ubuntu with no problem. Regular programs run fine, but when I try to run any of the Studio audio programs, I get: "System timer resolution is too low". Obviously the audio programs won't run with the generic kernel, but the updated kernel won't work with the NVIDIA driver.

I have seen this problem on a few other forums on the net, but none of the solutions have worked (yet).

---

### Post by reja on 2008-01-24
I was able to fix this problem by reinstalling the linux-rx kernel. I am using the nvidia-glx driver. I found this solution, along with others, at:

[http://ubuntuforums.org/archive/index.php/t-589728.html](http://ubuntuforums.org/archive/index.php/t-589728.html)

The page lists a lot of possible solutions, but this is what worked for me:

"The fix to make nvidia work is to install linux-rt in synaptic or go to terminal and type in sudo apt-get install linux-rt".

After reinstalling the rt kernel, I rebooted and everything ran fine. 

Hope this helps someone!

---

