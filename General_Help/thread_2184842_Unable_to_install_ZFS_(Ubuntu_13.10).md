---
title: "Unable to install ZFS (Ubuntu 13.10)"
date: 2013-10-30
forum: General Help
---

### Post by oli.washbrook on 2013-10-30
[COLOR=#333333][FONT=UbuntuRegular]I'm fairly new to Ubuntu and wanted to setup a server running ZFS/XBMC - Te XBMC install went fine, however I ran into trouble getting ZFS working.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Configuration : Ubuntu 13.10 (GNU/Linux 3.12.0-rc7+ x86_64)
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I attempted to install ZFS native using :[/FONT][/COLOR]

[LIST]
[*]sudo add-apt-repository ppa:zfs-native/stable
[*]sudo apt-get update
[*]sudo apt-get install ubuntu-zfs
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]This failed to install due to "Module build for the currently running kernel was skipped since the kernel source for this kernel does not seem to be installed."
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Trying sudo modprobe zfs - shows FATAL error : module not found.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Looking at [ZFS package (zfs-ubuntu) does not create zfs module?]("http://askubuntu.com/questions/201896/zfs-package-zfs-ubuntu-does-not-create-zfs-module") - they mentioned it was to do with lacking build dependences- I followed the answer which was to "apt-get remove --purge ubuntu-zfs zfs-dkms zfsutils spl spl-dkms libzfs1 dkms Then, REBOOT. Then, do: apt-get install linux-headers-generic build-essential Then, do: apt-get install ubuntu-zfs "
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]This leaves me in the same situation with "Building only for 3.12.0-rc7+ Module build for the currently running kernel was skipped since the kernel source for this kernel does not seem to be installed." when trying to install ubuntu-zfs.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Trying apt-get install --reinstall zfs-dkms also does not work.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I'm sure I am missing something obvious - but if anyone could give me any help I would greatly appreciate it ![/FONT][/COLOR]

---

### Post by DuckHook on 2013-10-30
*linux-headers-generic* may not be sufficient. To get your exact kernel, do:```
uname -a
```This will return something like```
Linux MyComputer 3.5.0-42-generic #65~precise1-Ubuntu SMP Wed Oct 30 20:57:18 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```It's the part after "3.5.0" that you need. In my case, this is "3.5.0-42". In your case it will be "3.12.0-xx" where "xx" is a number. Then do:```
sudo apt-get install linux-headers-3.12.0-xx-generic
```...replacing "xx" with your specific version. Then try re-installing ZFS.

---

### Post by oli.washbrook on 2013-10-31
[FONT=arial]Thanks for getting back to me DuckHook - I appreciate it!

uname -a get's me :

[/FONT]```
[FONT=arial]Linux MicroServer 3.12.0-rc7+ #1 SMP Mon Oct 28 08:31:59 CET 2013 x86_64 x86_64 x86_64 GNU/Linux[/FONT]
```[FONT=arial]

Then putting in : ( As adding generic to the end of the line doesn't find any packages)
[/FONT]```
[FONT=arial]sudo apt-get install linux-headers-3.12.0-rc7+[/FONT]
```[FONT=arial]

Gets me : 
[/FONT]```
[FONT=arial]0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.[/FONT]
```[FONT=arial]

Trying to reinstall ZFS gives me the same problem - I tried to force a reinstall of the headers with 
[/FONT]```
[FONT=arial]sudo apt-get install --reinstall linux-headers-3.12.0-rc7+[/FONT]
```[FONT=arial]

However that gave me no joy either ,  as it just listed 20 not upgraded as well. It seems that the headers are not installed but listed in the system as being installed. I was told to attempt to purge the headers using
 ```
sudo apt-get purge linux-headers-3.12.0-rc7
``` 

This removed them, however when i rebooted and ran the install again it just lists 20 not upgraded again. I'm at a bit of a loss now, any ideas?[/FONT]

---

### Post by Yellow Pasque on 2013-10-31
Where did you obtain the kernel? Mainline Kernel?

What happens when you run:
```
sudo apt-get dist-upgrade
```

---

### Post by oli.washbrook on 2013-10-31
Tried "sudo apt-get dist-upgrade " it just lists 2 not upgraded. 

The Kernel was taken from a link on the XBMC forums [http://forum.xbmc.org/showthread.php?tid=174854](http://forum.xbmc.org/showthread.php?tid=174854) -  it's the RC 7 for 3.12 - needed to support the OSS Radeon drivers to allow full vpadu support (hardware acceleration for radeon GPU's and fixes issues such as no sound over HDMI ) so HD video will work with my ATI 5450 (its moonlighting as a HTPC/File Server) 

It installs without a hitch - however when trying to install ZFS then fails.



I attempted to try this the other way round , so erased and reinstalled Ubuntu 13.10 - and using the default 3.11 kernel installed ZFS - that worked and I was able to create the data pools with ZFS - however when I subsequently installed the 3.12 kernel using ```
[COLOR=#000000][FONT=monospace]mkdir ~/kernel[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]cd ~/kernel[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]wget https://dl.dropboxusercontent.com/u/55728161/linux-headers-3.12.0-rc7%2B_0.1_amd64.deb https://dl.dropboxusercontent.com/u/55728161/linux-image-3.12.0-rc7%2B_0.1_amd64.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]sudo dpkg -i *rc7*deb[/FONT][/COLOR]
```

It failed with ```
ERROR (dkms apport): kernel package linux-headers-3.12.0-rc7+ is not supported
Error! Bad return status for module build on kernel: 3.12.0-rc7+ (x86_64)
``` 

So there appears to be an issue with 3.12 kernel and the release of ubuntu-zfs - does anyone know any way I could solve this and run ZFS on a 3.12 kernel to keep the hardware acceleration?

---

### Post by Yellow Pasque on 2013-10-31
>  it's the RC 7 for 3.12 - needed to support the OSS Radeon drivers to allow full vpadu support (hardware acceleration for radeon GPU's and fixes issues such as no sound over HDMI 
3.11 will work just fine for that, though you may need to manually enable HDMI audio: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)
Use this ppa to get vdpau and such: [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)

---

### Post by DuckHook on 2013-10-31
I should have picked up on the fact that your kernel was non-standard. In your case, of course you would not get the kernel headers--you did not install a standard repository kernel. You cannot expect the repositories to work on a customized engine because the warehouse simply doesn't stock those parts.

You can and should follow *Temujin*'s advice to enable HDMI sound using the standard kernel.

On a related note, as a fairly new user, do you really want to go installing kernels that you download from somebody's dropbox account??? What if it comes complete with a rootkit or keylogger? Your bank account could be cleaned out by now.

<Sigh> Please read [this]("http://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795") thread that was just recently posted. No point in my repeating myself.

---

### Post by oli.washbrook on 2013-10-31
Thanks for the links Temujin, I had previously tried the oibaf drivers but found a problem with video not playing and only displaying a white screen when accelerated using VDPAU - For those that are interested - I ended up with XBMC using VDPAU properly on a clean install of 13.10 (default kernel) by using the *xbmc-fernetmenta-master *build with the default drivers and the workaround for HDMI audio that Temujin kindly posted, which has also allowed me to install/use ZFS without issue (so far!) 

I appreciate the advice DuckHook, contrary to my previous actions I generally do take measure's to protect myself/my computers. The machine doesn't/won't be used either to contain or access important data and was on a separate network from my main computers. I admit however that the custom kernel wasn't the wisest choice, I had just reached a point of frustration trying to find a stable/fast implementation of VDAPU whilst using XBMC/ZFS

Nevertheless, I've read through the thread you've linked and taken measures to buff up my security where appropriate, and thank you both for your help.

---

### Post by Yellow Pasque on 2013-10-31
You're welcome. Also note that you have some sort of mental block and keep typing 'ZSH' instead of 'ZFS'. I have some sort of mental block about typing the word 'install'. It usually comes out as 'isntall', which isn't good when I'm always instructing people to apt-get install stuff. I'm determined to overcome it, though. I've been through tougher typing issues (such as capitalizing the second letter of a word and typing 'teh' instead of 'the').

---

### Post by oli.washbrook on 2013-10-31
Heh, I hadn't noticed that until now - thanks for pointing that one out!

---

### Post by carlo-maraschin on 2013-11-12
I got the same problem after install 3.12

uname -a
Linux overkill 3.12.0-031200-generic #201311071835 SMP Thu Nov 7 23:36:07 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Building initial module for 3.12.0-031200-generic
configure: error: 
    *** Please make sure the kmod spl devel <kernel> package for your
    *** distribution is installed then try again.  If that fails you
    *** can specify the location of the spl objects with the
    *** '--with-spl-obj=PATH' option.
ERROR (dkms apport): kernel package linux-headers-3.12.0-031200-generic is not supported
Error! Bad return status for module build on kernel: 3.12.0-031200-generic (x86_64)
Consult /var/lib/dkms/zfs/0.6.2/build/make.log for more information.

more /var/lib/dkms/zfs/0.6.2/build/make.log 
DKMS make.log for zfs-0.6.2 for kernel 3.12.0-031200-generic (x86_64)
Tue Nov 12 12:10:13 CET 2013
make: *** No targets specified and no makefile found. Stop.


I've downloaded and installed those packages from ubuntu kernel:
linux-headers-3.12.0-031200_3.12.0-031200.201311071835_all.deb
linux-headers-3.12.0-031200-generic_3.12.0-031200.201311071835_amd64.deb
linux-image-3.12.0-031200-generic_3.12.0-031200.201311071835_amd64.deb

It does work with 3.11.* ...

---

