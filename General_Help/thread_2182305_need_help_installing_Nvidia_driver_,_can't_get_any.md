---
title: "need help installing Nvidia driver , can't get anything but the command line"
date: 2013-10-20
forum: General Help
---

### Post by sam_baker2 on 2013-10-20
Hi,
After updating yesterday morning, every now and then, my computer would completely lock up, and the log file was showing that
the GPU had "fallen off the buss".
So I ran the "check for the latest drivers" for Nvidia and it showed that I had version 308. It also showed
a version 319 and it said that it was "recommended" . So i installed it. Now I cannot get into the desktop,
I can only can into the black screen, command line screen. When I do a "nvidia-smi -q | less"
it says this :
```
NVIDIA: API mismatch: the NVIDIA kernel module has a version 304.88,
but this NVIDIA driver componet has version 319.32. Please make
sure the kernel module and all NVIDIA driver components 
have the same version.
Failed to initialize NVML: Unknown Error
```

I have edited the grub line to this:

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"
```

and then I did a :
```
sudo update-grub
```
but when I reboot I still cannot get a desktop to where I might try to download the 308 Nvidia driver.

Any help appreciated

---

### Post by sam_baker2 on 2013-10-20
correction:
"So I ran the "check for the latest drivers" for Nvidia and it showed that I had version 308"
should read that I had version "304" , not 308

---

### Post by pqwoerituytrueiwoq on 2013-10-20
try this:
```
sudo apt-get purge nvidia-*
sudo apt-get install nvida-319-updates nvidia-settings-319-updates
```

---

### Post by pqwoerituytrueiwoq on 2013-10-20
[duplicate post]

---

### Post by sam_baker2 on 2013-10-21
pqwoerituytrueiwoq, I did this :

```
sudo apt-get --purge remove nvidia-*
```

and installed the drivers again using this:

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

and I got my desktop back.
But when I run the "Additional Drivers" , I get this (attached pic)
It only shows a 304 driver and it shows it to be "activated", but not currently in use.
Before, there was a 304 driver shown as well as a 319 driver ( with the 304 one being
the one that was activated. ) I don't know whether or not to load the 319 one has has you have
noted in your reply.

---

### Post by sam_baker2 on 2013-10-21
I will try again to upload the .pgn

---

### Post by pqwoerituytrueiwoq on 2013-10-21
if you installed via the nvidia website
```
sudo nvidia-installer --uninstall
```
you may need to delete [FONT=courier new]/etc/X11/xorg.conf
[/FONT]i always recommend the newest nvidia driver, unless your card in is ancient that is not a issue

---

