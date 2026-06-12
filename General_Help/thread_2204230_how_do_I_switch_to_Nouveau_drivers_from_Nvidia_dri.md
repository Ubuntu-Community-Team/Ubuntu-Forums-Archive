---
title: "how do I switch to Nouveau drivers from Nvidia drivers?"
date: 2014-02-07
forum: General Help
---

### Post by mawxcarroll on 2014-02-07
Here's the story:

First, this is all 13.10 with two GeForce GTX 550 Ti cards (not in SLI).

In trying to get a 3 monitor setup working, I installed the nvidia-331 driver from x-swat.  It mostly works quite well but some applications (Emacs, Mathematica) cause Ubuntu to crash to the login screen.  I thought I'd experiment a bit using a 13.10 live usb (I could try xorg-edgers and get nvidia-334 for example).

When I booted to the live-usb, to my surprise, I immediately had all three monitors working beautifully with no crashes.  I can see that the live-usb is using the nouveau driver.  I know that this might come with some performance hits, but it would be worth it to me for the three monitor setup (no gaming at all on this machine).

However, when I reboot back into my system and choose nouveau I do not get the same result as the live-usb!  I get one monitor with the wrong resolution.  I can't figure out what the difference is between the live-usb and my system.

I've tried totally eliminating all of the xorg.conf files and just going with the minimal xorg.conf file from [http://nouveau.freedesktop.org/wiki/UbuntuPackages/]("http://nouveau.freedesktop.org/wiki/UbuntuPackages/").  I get the same result.

I rather not do clean install of 13.10 if I can avoid it.  I'd be grateful for any advice!

Thanks.

Cheers,
tom

---

### Post by sudodus on 2014-02-10
Have you uninstalled the proprietary drivers? There are different 'levels of uninstalling':

```
sudo apt-get remove package
```

the standard uninstalling, and

```
sudo apt-get purge package
```

which also removes configuration files.

Read more at

```
man apt-get
```

Maybe if you reinstall nvidia-331 and then purge it, you will get similar performance as with the system booted from the USB drive.

---

### Post by jeanjd63 on 2014-02-10
Hello

Yes the command is :
**sudo  apt-get  purge "nvidia *"**

---

### Post by mawxcarroll on 2014-02-10
Hi,
  Thanks for the help!  Unfortunately, things aren't working yet.  It seems like my system is still defaulting to the vesa drivers (only one screen with low resolution).

I tried totally removing the nvidia drivers as you suggested (and as also described here: [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely]("http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely")).

That seemed to work fine so that now if I try remove/purge I get:

```

sudo apt-get remove nvidia-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-bug-report.log.gz
E: Couldn't find any package by regex 'nvidia-bug-report.log.gz'
E: Unable to locate package nvidia-bug-report.log.old.gz
E: Couldn't find any package by regex 'nvidia-bug-report.log.old.gz'

```

```

sudo apt-get purge nvidia-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-bug-report.log.gz
E: Couldn't find any package by regex 'nvidia-bug-report.log.gz'
E: Unable to locate package nvidia-bug-report.log.old.gz
E: Couldn't find any package by regex 'nvidia-bug-report.log.old.gz'

```

If I go to "additional drivers" I can still see some nvidia drivers listed as options (304 and 319).  However, if I try to remove them I get:

```

sudo apt-get remove nvidia-319
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nvidia-319' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 50 not upgraded.

```

I've also attached Xorg.0.log, which I think is showing the vesa driver eventually loading.  I'm stumped at the moment -- I know that nouveau will work beautifully from my testing with the live-usb, I just can't get it to load!

Any more help would be greatly appreciated -- thanks!

Cheers,
tom

---

### Post by mawxcarroll on 2014-02-10
UPDATE: I downloaded the nvidia drivers from nvidia's website and ran them with the "--uninstall" flag and they reported that no nvidia drivers were installed.

I don't know if this is helpful, but I'm concerned that maybe at some point in the past I manually installed an nvidia driver (this computer has been upgraded multiple times, so it's entirely possible and I certainly would not remember).  So I tried to find anything with nvidia in it and got the following:

```

find / -name '*nvidia*'
/lib/modules/3.11.0-15-generic/kernel/drivers/video/nvidia
/lib/modules/3.11.0-15-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.5.0-32-generic/kernel/drivers/video/nvidia
/lib/modules/3.5.0-32-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.5.0-32-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.8.0-34-generic/kernel/drivers/video/nvidia
/lib/modules/3.8.0-34-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.8.0-34-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.8.0-33-generic/kernel/drivers/video/nvidia
/lib/modules/3.8.0-33-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.8.0-33-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.8.0-25-generic/kernel/drivers/video/nvidia
/lib/modules/3.8.0-25-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.8.0-25-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.8.0-32-generic/kernel/drivers/video/nvidia
/lib/modules/3.8.0-32-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.8.0-35-generic/kernel/drivers/video/nvidia
/lib/modules/3.8.0-35-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.8.0-35-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.8.0-30-generic/kernel/drivers/video/nvidia
/lib/modules/3.8.0-30-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.8.0-30-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.8.0-29-generic/kernel/drivers/video/nvidia
/lib/modules/3.8.0-29-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.8.0-29-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.8.0-31-generic/kernel/drivers/video/nvidia
/lib/modules/3.8.0-31-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.8.0-31-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.8.0-27-generic/kernel/drivers/video/nvidia
/lib/modules/3.8.0-27-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.8.0-27-generic/kernel/drivers/net/ethernet/nvidia
/mnt/backup
find: `/lost+found': Permission denied
/usr/lib32/nvidia-current
/usr/lib32/nvidia-current/libnvidia-opencl.so.1
/usr/lib32/nvidia-current/libnvidia-wfb.so.1
/usr/lib32/nvidia-313-updates
/usr/lib32/nvidia-313-updates/libnvidia-encode.so.1
/usr/lib32/nvidia-313-updates/libnvidia-opencl.so.1
/usr/lib32/nvidia-313-updates/libnvidia-wfb.so.1
/usr/lib/x86_64-linux-gnu/directfb-1.2-9/gfxdrivers/libdirectfb_nvidia.so
/usr/lib/python3/dist-packages/NvidiaDetector/nvidiadetector.py
/usr/lib/python3/dist-packages/NvidiaDetector/__pycache__/nvidiadetector.cpython-33.pyc
/usr/lib/nvidia-current
/usr/lib/nvidia-current/libnvidia-opencl.so.1
/usr/lib/nvidia-current/libnvidia-wfb.so.1
/usr/lib/nvidia-313-updates
/usr/lib/nvidia-313-updates/libnvidia-encode.so.1
/usr/lib/nvidia-313-updates/libnvidia-opencl.so.1
/usr/lib/nvidia-313-updates/libnvidia-wfb.so.1
/usr/lib/nvidia
/usr/src/linux-headers-3.8.0-30/drivers/video/nvidia
/usr/src/linux-headers-3.8.0-30/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.8.0-34-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.8.0-34-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.8.0-34-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.8.0-30-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.8.0-30-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.8.0-30-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.8.0-31-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.8.0-31-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.8.0-31-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.8.0-25-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.8.0-25-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.8.0-25-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.8.0-32-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.8.0-35-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.8.0-35-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.8.0-35-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.11.0-15/drivers/video/nvidia
/usr/src/linux-headers-3.11.0-15/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.8.0-33-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.8.0-33-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.8.0-33-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.8.0-35/drivers/video/nvidia
/usr/src/linux-headers-3.8.0-35/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.8.0-34/drivers/video/nvidia
/usr/src/linux-headers-3.8.0-34/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.8.0-31/drivers/video/nvidia
/usr/src/linux-headers-3.8.0-31/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.11.0-15-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.11.0-15-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.11.0-15-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.8.0-25/drivers/video/nvidia
/usr/src/linux-headers-3.8.0-25/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.8.0-33/drivers/video/nvidia
/usr/src/linux-headers-3.8.0-33/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.8.0-32/drivers/video/nvidia
/usr/src/linux-headers-3.8.0-32/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.8.0-27/drivers/video/nvidia
/usr/src/linux-headers-3.8.0-27/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.8.0-27-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.8.0-27-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.8.0-27-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.8.0-29/drivers/video/nvidia
/usr/src/linux-headers-3.8.0-29/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.8.0-29-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.8.0-29-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.8.0-29-generic/include/config/fb/nvidia
/usr/bin/nvidia-detector
/usr/bin/nvidia-settings
find: `/usr/share/doc/google-chrome-stable': Permission denied
/usr/share/app-install/desktop/nvidia-driver-185.desktop
/usr/share/app-install/desktop/nvidia-driver-96.desktop
/usr/share/app-install/desktop/nvidia-driver-173.desktop
/usr/share/apport/package-hooks/source_nvidia-graphics-drivers.py
/usr/share/apport/package-hooks/source_nvidia-graphics-drivers-96.py
/usr/share/apport/package-hooks/source_nvidia-graphics-drivers-updates.py
/usr/share/apport/package-hooks/source_nvidia-graphics-drivers-71.py
/usr/share/apport/package-hooks/source_nvidia-graphics-drivers-173.py
/usr/share/apport/package-hooks/source_nvidia-graphics-drivers-experimental-310.py
/usr/share/apport/package-hooks/source_nvidia-graphics-drivers-experimental-304.py
/usr/share/man/man1/nvidia-settings.1.gz
find: `/sys/kernel/debug': Permission denied
find: `/run/udisks2': Permission denied
find: `/run/lightdm': Permission denied
find: `/run/cups/certs': Permission denied
find: `/var/lib/udisks2': Permission denied
find: `/var/lib/sudo': Permission denied
/var/lib/dpkg/info/nvidia-settings-304.postrm
/var/lib/dpkg/info/nvidia-settings.list
/var/lib/dpkg/info/nvidia-settings-331.postrm
/var/lib/dpkg/info/nvidia-304.list
/var/lib/dpkg/info/nvidia-settings-319-updates.postrm
/var/lib/dpkg/info/nvidia-persistenced.list
/var/lib/dpkg/info/nvidia-settings-331.list
/var/lib/dpkg/info/nvidia-settings-304.list
/var/lib/dpkg/info/nvidia-319-updates.list
/var/lib/dpkg/info/nvidia-304.postrm
/var/lib/dpkg/info/nvidia-current.list
/var/lib/dpkg/info/nvidia-331.list
/var/lib/dpkg/info/nvidia-313-updates.list
/var/lib/dpkg/info/nvidia-331.postrm
/var/lib/dpkg/info/nvidia-settings.postrm
/var/lib/dpkg/info/nvidia-319-updates.postrm
/var/lib/dpkg/info/nvidia-settings-319-updates.list
/var/lib/dpkg/alternatives/nvidia_settings_conf

```

Looks like there is still some nvidia stuff hanging around...not sure if this is an issue or how I remove it.  Since the package manager doesn't seem to know about it, maybe I need some sort of manual uninstall?

Thanks!

Cheers,
tom

---

### Post by Bashing-om on 2014-02-10
mawxcarroll; Hi !

If too many hands does not spoil the soup !
Let's try this approach: As a means to insure all the old Nvidia driver files are removed; And then rebuild :
```

##stop lightdm##
sudo service lightdm stop

##preperations ##
sudo apt-get update
sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*
sudo apt-get remove --purge nvidia-*

##rebuild##
sudo apt-get install linux-headers-'uname -r' ##makes sure we have the libraries to build the Nvidia module##
sudo apt-get update
##-> above commands will also remove the nvidia-common package and the nvidia-common package has as a dependency of the ubuntu-desktop package.
##So after above command you should also give the installation command for ubuntu-desktop package:##
sudo apt-get install ubuntu-desktop
sudo apt-get install nvidia-current  
sudo nvidia-xconfig
sudo apt-get update ##once more just for good measure
sudo apt-get upgrade

##start lightdm
sudo service lightdm start

```

If there are still problems, maybe reboot for all changes to take effect .


EDIT: Once stable, we can then look to installing the open source drivers if you want.
[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by mawxcarroll on 2014-02-10
Hi Bashing-om,
  Thanks for the help.  I followed your instructions and I'm now back to using nvidia-304.  I would, of course, love to switch to nouveau for the reasons in my original post!  Any ideas you have for how to make that happen would be fantastic.

Thanks again!

Cheers,
tom

---

### Post by jeanjd63 on 2014-02-10
Only :
[B]sudo  apt-get  purge  "nvidia *"
[/B]as this

---

### Post by Bashing-om on 2014-02-10
mawxcarroll; Hey !

Sounds like a winner to me, I too prefer the nouveau drivers - peace of mind -.
As you are stable, we can proceed and do this.

OK, make sure that the nouveau drivers are not blacklisted:
```

ls -la /etc/modprobe.d/
cat  /etc/modprobe.d/blacklist.conf

```
And now to do the magic: remove and get up on open source !
```

sudo apt-get purge nvidia-current nvidia-settings
sudo apt-get install xserver-xorg-video-nouveau #just to make sure and positive that the module is installed ! - safety is no accident -
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

RE-Boot for the change to take effect.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by deadflowr on 2014-02-10
> **jeanjd63 said:**
> Only :
[B]sudo  apt-get  purge  "nvidia *"
[/B]as this

Edit: nevermind.
But you can run it without quotes, just nvidia*

---

### Post by mawxcarroll on 2014-02-10
Hi Bashing-om,
  Thanks for your help.  Unfortunately, I have to report that things aren't working.  I think that I'm not really succeeding in removing the nvidia drivers from the system.  Even after running all of the commands you suggest, when I reboot I can go into system settings->software and updates-->additional drivers and see nvidia drivers as an option!  

If I choose nouveau, then when I reboot I think it just defaults to the vesa driver and leaves me with one low resolution screen.

If I choose nvidia, everything is fine for a two monitor setup.

I'm not sure if there's some other way to really get rid of these nvidia drivers.  I'm edging closer to a reinstallation of 13.10...

Just to be clear:  I am currently using nvidia-319, selected in system settings->software and updates-->additional drivers.  But look at this output:

```

sudo apt-get purge nvidia-current nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nvidia-settings' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I'm confused!

Cheers,
tom

---

### Post by deadflowr on 2014-02-10
In obviousness, nvidia-current and nvidia-319 are different names, and for the most part probably, different drivers.
Same for nvidia-settings.
My guess you have nvidia-settings-319 or 310 or something like that.
The terminal command
```
apt-cache policy <packagenamehere>
```
Will give you an output of whether or not a package is installed(or even in the repo you are using)
For fun you could run
```
apt-cache policy nvidia*
```
Which will output all the instances of nvidia within the repo system
(installed or not installed)

---

### Post by Bashing-om on 2014-02-10
mawxcarroll;

The "Additional Drivers" utility shows what is installed, as well as what is available in the repository that might be installed.

Let's look at what is !
```

sudo apt-get --purge remove nvidia-glx-* nvidia-settings
lspci -nnk | grep -iA3 vga
sudo lshw -C display
cat /sys/module/nvidia/version
ls -ld /lib/nvidia*
sudo find /lib/modules/`uname -r`/ -name 'nvidia*' ##(those are back ticks around uname -r ``)##

```

Also, going back and forth can mess things up so sometimes make sure:
    Ubuntu nouveau uses ~/.config/monitors.xml If nvidia is enabled instead, make sure to name this .bak so it's not used.

Hopefully these will show what is going on.
Else:
[INDENT][INDENT]we will keep digging and looking !
[/INDENT][/INDENT]

---

### Post by jeanjd63 on 2014-02-11
> **jeanjd63 said:**
> Only :
[B]sudo  apt-get  purge  "nvidia *"
[/B]as this


This command works fine. You can try it.

---

### Post by mawxcarroll on 2014-02-11
Hi Bashing-om,
  Thanks.  At the moment, I have nvidia-319 selected in additional drivers just so I can keep working at my actual job :).  

Here's the output:

```

sudo apt-get --purge remove nvidia-glx-* nvidia-settings
[sudo] password for tcarroll: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-glx' for regex 'nvidia-glx-*'
Package 'nvidia-glx' is not installed, so not removed
Package 'nvidia-settings' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:1556]
	Kernel driver in use: nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation GF116 High Definition Audio Controller [10de:0bee] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:1556]
	Kernel driver in use: snd_hda_intel
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:1556]
	Kernel driver in use: nvidia
02:00.1 Audio device [0403]: NVIDIA Corporation GF116 High Definition Audio Controller [10de:0bee] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:1556]
	Kernel driver in use: snd_hda_intel
04:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE912x SATA 6Gb/s Controller [IDE mode] [1b4b:91a0] (rev 12)
	Subsystem: ASRock Incorporation Device [1849:91a0]

```

```

sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f4000000-f5ffffff memory:e0000000-e7ffffff memory:e8000000-ebffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:17 memory:f0000000-f1ffffff memory:d0000000-d7ffffff memory:d8000000-dbffffff ioport:d000(size=128) memory:f2000000-f207ffff

```

```

cat /sys/module/nvidia/version
319.60

```

```

ls -ld /lib/nvidia*
drwxr-xr-x 2 root root 4096 Feb 10 16:43 /lib/nvidia-319-updates

```

```

sudo find /lib/modules/`uname -r`/ -name 'nvidia*'
/lib/modules/3.11.0-15-generic/kernel/drivers/video/nvidia
/lib/modules/3.11.0-15-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.11.0-15-generic/updates/dkms/nvidia_319_updates.ko

```

---

### Post by mawxcarroll on 2014-02-11
Hi deadflowr,
  Thanks for the suggestion.  The output of this command is exactly what confuses me, since it seems like I have some nvidia installed that the package manager doesn't know about:

```

tcarroll@loki2:~$ apt-cache policy nvidia*
N: Unable to locate package nvidia-bug-report.log.gz
N: Couldn't find any package by regex 'nvidia-bug-report.log.gz'
N: Unable to locate package nvidia-bug-report.log.old.gz
N: Couldn't find any package by regex 'nvidia-bug-report.log.old.gz'

```

---

### Post by sherwoodinc on 2014-03-03
Don't mind the files you found in /lib/modules/... The nvidiafb.ko (framebuffer) module is part of the stock kernel and has nothing to do with the binary nvidia module.

The nvidia binary drivers will always show up in your "additional drivers" window, regardless of them being installed or not.

You should check that your nouveau driver is not blacklisted, just as a previous post recommends.

---

