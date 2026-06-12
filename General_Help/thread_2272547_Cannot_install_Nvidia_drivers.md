---
title: "Cannot install Nvidia drivers"
date: 2015-04-07
forum: General Help
---

### Post by shuri2 on 2015-04-07
When I try to install Nvidia drivers in terminal I get:

jeb@jebtop:~$ sudo apt-get install nvidia-current
[sudo] password for jeb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-generic linux-image-generic thermald
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcuda1-331 nvidia-304 nvidia-opencl-icd-331
Recommended packages:
  libcuda1-304 nvidia-opencl-icd-304
The following packages will be REMOVED:
  nvidia-331
The following NEW packages will be installed:
  nvidia-304 nvidia-current
The following packages will be upgraded:
  libcuda1-331 nvidia-opencl-icd-331
2 upgraded, 2 newly installed, 1 to remove and 255 not upgraded.
1 not fully installed or removed.
Need to get 0 B/52,1 MB of archives.
After this operation, 11,8 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 170861 files and directories currently installed.)
Removing nvidia-331 (331.113-0ubuntu0.1) ...
stop: Unknown job: nvidia-persistenced
userdel: user nvidia-persistenced is currently used by process 1517
dpkg: error processing package nvidia-331 (--remove):
 subprocess installed post-removal script returned error exit status 8
Errors were encountered while processing:
 nvidia-331
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by CantankRus on 2015-04-07
Have you used the xorg-edgers ppa?
What driver are you currently using?

For info you can install and use inxi.
```
sudo apt-get install inxi
```
```
inxi -b
```
eg```
[COLOR="#008000"]**glen@Trusty:~$[/COLOR] inxi -b**
System:    Host: Trusty Kernel: 3.16.0-33-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 1400.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.16.0 drivers: **nvidia** (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 **NVIDIA 331.113**
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1250.3GB (13.0% used)
```

---

### Post by shuri2 on 2015-04-07
It says my driver is "nouveau".
I have set up xorg-edgers ppa.

---

### Post by QDR06VV9 on 2015-04-07
It looks to me like you you had nvidia 331 installed from your OP
try this 
```
sudo apt-get remove nvidia*
```

Then run
```
dpkg -l | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

After that should be be good to install driver
```
sudo apt-get install nvidia-current
```

Reboot and let us know.
Regards

---

### Post by CantankRus on 2015-04-07
Can you post your output from inxi -b because the more info given the easier it is to help.
Can you also post the output from this command...
```
find /etc/apt/sources.list.d -name \*.list | cut -f 5 -d '/' | sort
```

Please put any output in code blocks by highlighting with left mouse and hitting the hash icon.

---

### Post by CantankRus on 2015-04-07
@runrickus
> **shuri2 said:**
> It says my driver is "nouveau".
**[COLOR="#FF0000"]I have set up xorg-edgers ppa[/COLOR]**.

---

### Post by QDR06VV9 on 2015-04-07
> **CantankRus said:**
> @runrickus
Yes I saw that but did you read this in his OP
```
([COLOR=#ff0000]Reading database ... 170861 files and directories currently installed.)
Removing nvidia-331 (331.113-0ubuntu0.1) ...
stop: Unknown job: nvidia-persistenced
userdel: user nvidia-persistenced is currently used by process 1517
dpkg: error processing package nvidia-331 (--remove):[/COLOR]
 subprocess installed post-removal script returned error exit status 8
Errors were encountered while processing:
 nvidia-331
```

---

### Post by CantankRus on 2015-04-07
> **runrickus said:**
> Yes I saw that but did you read this in his OP
```
([COLOR=#ff0000]Reading database ... 170861 files and directories currently installed.)
Removing nvidia-331 (331.113-0ubuntu0.1) ...
stop: Unknown job: nvidia-persistenced
userdel: user nvidia-persistenced is currently used by process 1517
dpkg: error processing package nvidia-331 (--remove):[/COLOR]
 subprocess installed post-removal script returned error exit status 8
Errors were encountered while processing:
 nvidia-331
```
Yes, but if you want to jump right in and start running commands while I'm getting info go ahead. :p

---

### Post by QDR06VV9 on 2015-04-07
> **CantankRus said:**
> _Yes, but if you want to jump right in and start running commands_ while I'm getting info go ahead. :p
We all just do our part to help! I'm not sure I just jumped in..
But by all means get your info):P So I will just jump out now!:p
Regards

---

### Post by ubunt72 on 2015-04-07
I agree with providing the output of '$ inxi -b' - that way, you can obtain the hardware info (i.e. video card etc.).  

Why suggest to install nvidia-current?   That is just the 304 version.   It's old and mostly for legacy cards?   The Nvidia drivers I would suggest are 340, 343 and 346.

---

### Post by efflandt on 2015-04-07
I don't think it really matters which nvidia drivers he uses for GTX 550 Ti as long as properly installed and actually being used, since that has been around for awhile (I had one before replacing it with GTX 750 Ti which is faster for most things using half the power). The output of **glxinfo | grep ^OpenGL** should show what is in use:```
efflandt@XPS-8100-1404:~$ glxinfo | grep ^OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 750 Ti/PCIe/SSE2
OpenGL core profile version string: 4.3.0 NVIDIA 349.12
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5.0 NVIDIA 349.12
OpenGL shading language version string: 4.50 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
```

---

