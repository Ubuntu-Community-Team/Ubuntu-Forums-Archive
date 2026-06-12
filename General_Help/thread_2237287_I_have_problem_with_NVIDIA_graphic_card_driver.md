---
title: "I have problem with NVIDIA graphic card driver"
date: 2014-07-31
forum: General Help
---

### Post by AbhimanyuAryan on 2014-07-31
I am using Kali Linux on my Acer E1-571G to install Nvidia drivers 

I copied these commands to terminal: 

apt-get update
apt-get dist-upgrade
apt-get install -y linux-headers-$(uname -r)
apt-get install nvidia-kernel-dkms

Then 

sed 's/quiet/quiet nouveau.modeset=0/g' -i /etc/default/grub
update-grub
reboot

after i rebooted i typed this command:  glxinfo | grep -i "direct rendering"

but i don't get : direct rendering: Yes as output 

i get : 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

what's wrong? 

Then i typed this: aptitude install nvidia-xconfig
 
in hope that it would work then : 

nvidia-xconfig

but after i reboot i get a blackscreen error so i removed xconfig using rm in ctrl+ Alt + F1

But the issue is i still don't have nvidia graphics drivers working

---

### Post by kc1di on 2014-08-01
I think you may be making it too difficult I'm not familar with Kali - but if it uses the Ubuntu repositories you should be able to simply 
type the following command and install nvidia driver you need.
```
sudo apt-get install nvidia-<driver # you need for your card>
```

Drivers that are available are Open source nouveau-firmware, (some have problems with this driver) bumblebee and bumblebee-nvidia, nividia-173, nvidia-304 and nvidia-331.

it would be helpful if we knew what nvidia card your machine is using. 
you can get that information from the command ```
lspci | grep VGA
``` and posting the results here.

---

### Post by SeijiSensei on 2014-08-01
Use "sudo apt-get install nvidia-current" and let the installer figure out the correct version.

---

### Post by nuts2 on 2014-08-01
I just open the additional drivers app that comes with Ubuntu and do it through there. That is the easiest way I have found to install drivers.

---

### Post by AbhimanyuAryan on 2014-08-01
root@HackerInside:~# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1140 (rev a1)
root@HackerInside:~#

---

### Post by AbhimanyuAryan on 2014-08-01
do i need to delete then current version i have installed on my kali Linux. Also have removed nouveau what should i do to revert to what i have done in above commands(mentioned in question). Also i am using Kali would that create problem in giving ubuntu commands

---

### Post by SeijiSensei on 2014-08-01
> **nuts2 said:**
> I just open the additional drivers app that comes with Ubuntu and do it through there. That is the easiest way I have found to install drivers.

I use that method as well, but functionally it is identical to running "sudo apt-get install nvidia-current" from the command prompt.

---

### Post by Yellow Pasque on 2014-08-01
It looks like you have Optimus/hybrid graphics. You cannot simply install the nvidia driver then, and you should ignore the previous suggestions. If you were running Ubuntu 14.04, you would either install bumblebee or nvidia-prime package.

I have no idea how old Kali Linux is (probably older than Ubuntu 14.04 since it does not know the PCI ID of the Geforce 610M). At any rate, Kali is not supported on this forum (use Kali's forums).

---

### Post by hoodbrothers2 on 2014-08-01
Try this link.  It's a tutorial on how to install NVIDIA drivers.  His voice is REALLY weird but this is how I installed mine on ubuntu.  Hopefully it works on your distro too.  Just replace the driver version with the one you want.  Basically you just need a repository.

[https://m.youtube.com/?#/watch?v=1oKn8DHvOrk](https://m.youtube.com/?#/watch?v=1oKn8DHvOrk)

---

### Post by s-l-425434 on 2014-08-01
[http://www.notebookcheck.net/Acer-Aspire-E1-571G-3114G50Mnks.87290.0.html](http://www.notebookcheck.net/Acer-Aspire-E1-571G-3114G50Mnks.87290.0.html) 
Does your graphic card match that spec? If so, assuming kali works as ubuntu 12.10 or later add this ppa:
```
  **sudo apt-add-repository ppa:xorg-edgers/ppa**
```

if it works like 10.04 - 12.04 add this ppa:

```
 **sudo apt-add-repository ppa:ubuntu-x-swat/x-updates** 
```

then:

```
 **sudo apt-get update** 
```

last 

```
 **sudo apt-get install nvidia-current nvidia-settings** 
```

To be sure, could you post specifically what NVIDIA card you´ve got?

---

### Post by kc1di on 2014-08-01
you will need the bumblebee driver for you optimus GPU.  But I'm not sure it's available for Kali. you may want to inquire on their [forum here.]("https://forums.kali.org/forumdisplay.php?1-Kali-Linux-Forums")

---

### Post by AbhimanyuAryan on 2014-08-03
i was able to install the Nvidia latest drivers by pressing ctrl+alt+f1 and then shuting down gdm3 and then typing sh Nvidia Driver then its started installation but an error occured saying: Recieved signal SIGTERM; aborting...whats wrong?

---

### Post by Yellow Pasque on 2014-08-03
> **AbhimanyuAryan said:**
> whats wrong?

You're doing it wrong. You cannot install the nvidia driver that way on an Optimus system.

---

### Post by 5mZKCMUmw1Le on 2014-08-03
Do you have integrated graphics in your CPU?

I had to manually disable that in BIOS for my AMD card to work with AMD drivers. Ubuntu/x.org incorrectly chose the wrong card to use with the drivers.

---

### Post by AbhimanyuAryan on 2014-08-04
you mean intel 400 something yaa had them but then i messed up something and now its showing fall back mode on graphic section

---

