---
title: "[SOLVED] Could not enable desktop effects"
date: 2008-06-05
forum: General Help
---

### Post by balakrishnanunna on 2008-06-05
Hi,
I've been trying to enable my visual effects but I always get a window saying

Could not enable desktop effects

I've tried installing compiz and typing compiz into the terminal. But it just doesn't work.

I am Using Intel Desktop board 1gb ddr2 ram Intel Pentium dual core 2.8 processor

can any one can help me?

Thanks in advance 
Balakrishna.

---

### Post by Vadi on 2008-06-05
What video card do you have?

---

### Post by Forlong on 2008-06-05
Run this and post the output here: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by Vadi on 2008-06-05
I totally forgot about Compiz Check... sorry! Do what Forlong said.

---

### Post by balakrishnanunna on 2008-06-06
i did this
Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems..../compiz-check: line 402: [: 600: unary operator expected
./compiz-check: line 402: [: 800: unary operator expected
           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Detected driver is not on Compiz' whitelist. 

Would you like to know more? (Y/n) y

 Your driver is not known (most probably not able) to work with Compiz.
 See [http://wiki.compiz-fusion.org/Hardware](http://wiki.compiz-fusion.org/Hardware) for details. 

Check if there's an alternate (proprietary) driver available? (Y/n) y

---

### Post by Vadi on 2008-06-06
I don't know much, only thing I can recommend is to go to System - Administration - Hardware Drivers, and make sure that the video driver is enabled.

---

### Post by Matthew Wiebelhaus on 2008-06-06
Im pretty sure that the VESA driver dosent support 3d acceleration so I think that you arent going to have anymore luck. Install all of these packages and see what happes after reboot.

sudo apt-get install xserver-xorg-i740
sudo apt-get install xserver-xorg-i810
sudo apt-get install xserver-xorg-intel

I doubt those will fix anything but tell me what happens.

---

### Post by Forlong on 2008-06-07
balakrishnanunna, please post the output of ```
grep -v ^# /etc/X11/xorg.conf
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by balakrishnanunna on 2008-06-08
> **Forlong said:**
> balakrishnanunna, please post the output of ```
:~$ grep -v ^# /etc/X11/xorg.conf
Section "Files"
EndSection

Section "Module"
        Disable         "dbe"
        Disable         "dri"
        Disable         "glx"
        Disable         "vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth	16
		Modes   "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

``` and use the forum's [noparse]this i got[/noparse] tag please (# button)
this i got

---

### Post by Forlong on 2008-06-08
Run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart X and try again.

---

### Post by balakrishnanunna on 2008-06-08
> **Forlong said:**
> Run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart X and try again.
sudo: unable to resolve host :(

---

### Post by balakrishnanunna on 2008-06-08
> **Forlong said:**
> Run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart X and try again.

sudo: unable to resolve :(

---

### Post by Sef on 2008-06-08
> Im pretty sure that the VESA driver dosent support 3d acceleration so I think that you arent going to have anymore luck.

That is correct.

---

### Post by balakrishnanunna on 2008-06-08
sudo: unable to resolve

---

### Post by balakrishnanunna on 2008-06-08
then i am not happy with this ubuntu how can i continue with this.

---

### Post by Forlong on 2008-06-08
What's the output of ```
cat /etc/hostname
``` and ```
cat /etc/hosts
```

---

### Post by Vadi on 2008-06-08
Edit: lets sort this out before it gets confusing.

---

### Post by Forlong on 2008-06-08
People, please stop confusing balakrishnanunna!

He/she should be able to run Compiz just fine, it's just a setup issue.

---

### Post by balakrishnanunna on 2008-06-09
```
./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

balakrishna@balakrishna-madu:~$ compiz
Checking for Xgl: not present. 
FATAL: Error inserting battery (/lib/modules/2.6.24-16-generic/kernel/drivers/acpi/battery.ko): Operation not permitted
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

i got this while doing compiz

---

### Post by Forlong on 2008-06-09
Please provide the outputs I asked for in post [#16]("http://ubuntuforums.org/showpost.php?p=5141590&postcount=16")

---

### Post by balakrishnanunna on 2008-06-09
```
 balakrishna@balakrishna-madu:~$ cat /etc/hostname
balakrishna-madu
balakrishna@balakrishna-madu:~$ cat /etc/hosts

# The following lines are desirable for IPv6 capable hosts

balakrishna@balakrishna-madu:~$ 
 
```

i got this

---

### Post by Forlong on 2008-06-09
That's bad.

The content of /etc/hosts should look like this:
```
127.0.0.1	localhost
127.0.1.1	balakrishna-madu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
Boot into the recovery mode and put it in there.

The recovery mode (selectable in GRUB) is a text only mode.
Thus you have to use nano.
Open the file like this then:
```
nano /etc/hosts
```
Then type this in there:
```
127.0.0.1	localhost
127.0.1.1	balakrishna-madu
```
How to use nano is explained in the bottom of the program itself. The ^ stands for [Ctrl]

Hope this helps.


P.S. I'd like to point out that this is a very unusual problem...

---

### Post by balakrishnanunna on 2008-06-09
amazing it is working..... i got my display effects back and i got my screen resolution proper thanks alot :)

---

