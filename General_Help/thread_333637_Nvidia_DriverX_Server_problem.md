---
title: "Nvidia Driver/X Server problem"
date: 2007-01-07
forum: General Help
---

### Post by some_bloke on 2007-01-07
After installing the appropriate Nvidia driver into Ubuntu 6.10 (64-bit version) I started X up from the shell, got an Nvidia splash screen and things seemed to be working fine

Rebooted and now X won't start


Whereis xorg.conf returns /usr/lib/xorg/ ... no xorg.conf exists in this location

The 'X is dead' error screens are reporting that it's using /etc/x11/xorg.conf ... which does exist


Anyone have any ideas how I can fix this?

---

### Post by ~LoKe on 2007-01-07
There should be an error coming up.  What is it?

Oh, and paste the output of
```
cat /etc/X11/xorg.conf
```

---

### Post by bettlebrox on 2007-01-07
I think whereis is telling you where xorg is installed and not where the xorg.conf file is. The xorg.conf file should be in /etc/X11/xorg.conf

Are you sure the nvidia module is loaded after you rebooted? To find out do this:

lsmod |grep -i nvidia

If it's not loaded you can manually load it with this command:
sudo modprobe nvidia

To ensure it reload on reboot just add it to /etc/modules

If that isn't what the problem is, look at the Xorg log file for any clues: /var/log/Xorg.0.log

---

### Post by some_bloke on 2007-01-07
I should point out I'm virtually a complete linux n00b

(The last time tried linux wasn't for long enough to learn much, and sufficient aeons ago for me to have forgotten the litle I did pick up)


As such I'm not too conversant with using the shell yet .... took me two days to find out how to get into the thing at runlevel 3 (without x running) so I could install the driver in the first place!


I'll see if bettlebrox's suggestion works and if not try and get the info ~LoKe asked for

Thanks for the replies, much appreciated :)

---

### Post by some_bloke on 2007-01-07
I've moved on a little from there now, solved a few errors

Now it's telling me I need to install xorg sdk so after some searching I found xserver-xorg-dev

But when I try installing this, I get an error message saying 'new line not expected'


Perhaps a format and reinstall might be easier :-?

---

### Post by some_bloke on 2007-01-07
Almost forgot ...

The error I'm getting when trying to boot is:

NVIDIA:  could not open the device file /dev/nvidia0 (input/output error)

The file is there

---

### Post by bettlebrox on 2007-01-08
How did you install the Nvidia driver? Did U use the installer provided by Nvidia or did you the Ubuntu packages ([http://ubuntuguide.org/wiki/Ubuntu_Edgy#Graphics_Card)?](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Graphics_Card)?)

---

### Post by desertgeek on 2007-04-12
I am receiving the same message in Xorg.log (NVIDIA: could not open device file /dev/nvidia0 (Input/output error)). I googled the error and I wasn't able to turn up much, mostly archived newsgroup posts that did not have any other details on how to resolve it.

I have an AMD64 3200+ 939 with 2GB Dual Channel DDR, an Nforce2 MB, and a GeForce 6200 AGP card with 256 MB. I'm running Edgy 32-bit. (Better software and codec support, since I'm rebuilding a MythTV system that was running Fedora 4 64-bit.)

I have installed the driver via apt, envy and downloading the binary from nvidia. no matter which install I used, I get this same message. I ran the SimplyMEPIS (ubuntu derivitive) LiveCD on this very same hardware, choosing to use the nvidia drivers and it works perfectly.

I checked dmesg and there were about a half dozen lines preceeded by NVRM, follwed by the following error:

allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.

That's all fine and good, but I'm not sure where I'm supposed to use it. I figure it's a kernel parameter that is passed at boot. Also, I don't know what the default value is, so I'm not sure what a good size would be. I would rather not pass a kernel parameter, especially since it works fine in SimplyMEPIS.

I would rather run ubuntu from the Alternate Install disc instead of going to another distribution, since the MythTV install is well documented. I want to keep the 'extras' to a minumum, which is why I'm installing from command-line.

Any ideas or hints would be greatly appriciated.

---

### Post by henriquemaia on 2008-01-17
I’m getting the same error 
```

/dev/nvidia0 (input/output error)
```I have installed Nvidia’s driver through envy (version 96.43) and cannot start it. I need to install this because the lastest drivers are really buggy on my 8600M GT.

---

