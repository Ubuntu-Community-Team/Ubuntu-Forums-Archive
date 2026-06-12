---
title: "Please help, stuck on boot after update."
date: 2018-07-14
forum: General Help
---

### Post by Delosari on 2018-07-14
I wonder if anyone could help me please to save my os:

I accepted an ubuntu 18.04 update on my dell inspiron 15 7000 series yesterday and now I cannot get into the login screen

The system gets stuck on boot line:

started gnome display manager dispatcher service..... tem changes.pp temp link was shut down

I have tried from the tty (using alt+f4 wihthin the frozen line (somehow I have to keep clicking this key combination since the screent becomes inactive all the time)) these bug  ticket solutions ([https://bugs.launchpad.net/ubuntu/+bug/1779827](https://bugs.launchpad.net/ubuntu/+bug/1779827)) I have tried these commands:

sudo apt-get install haveged
sudo apt-get --reinstall install ubuntu-gnome-desktop- gnome-shell gnome
sudo apt-get remove linux-image-4.15.0.24-generic linux-headers-4.15.0.24-generic

However I am still stuck in the same line. There are many posts with similar issues in the last week but either their solutions are not working for me or I do not know how to make them work... Please help, I need to relog to finish my research thesis.

[UPDATE]

I am trying to change back to the kernel 4.15.0.23 as adviced by many users but I have not been able. The command  

sudo apt-get remove linux-image-4.15.0.24-generic linux-headers-4.15.0.24-generic

is actually giving me this error:

Aborting removal of the running kernel
dpkg: error procesing the package linux-image-4.15.0-24-generic (--remove):
installed linux-image-4.15.0-24-generic package pre-removal script subprocess returned error exit status 1
errors where encoutnered while processing:
linux-image-4.15.0-24-generic
E: Sub-process /usr/bin/dpkg return an error code(1)

Which is the right procedure to remove current kernel and install an older version from tty? (This is a full linux installation no grub)

---

### Post by Xian on 2018-07-14
First verify which kernels you have installed:
```
dpkg -l | grep linux-image
```


Try to remove the broken kernel:
```
sudo apt-get purge linux-image-<version/name>
```


Be sure to remove its headers too
```
sudo apt-get purge linux-headers-<version/name>
```

---

### Post by Delosari on 2018-07-15
> **Xian said:**
> First verify which kernels you have installed:
```
dpkg -l | grep linux-image
```


Try to remove the broken kernel:
```
sudo apt-get purge linux-image-<version/name>
```


Be sure to remove its headers too
```
sudo apt-get purge linux-headers-<version/name>
```

Thank you very much Xian for your update.

After typing many commads which I did not understand ubuntu started. I have lost the sound  however and now I am afraid to turn it off. I have run the first command you gave me and I have:

```
dpkg -l | grep linux-imagerc  linux-image-4.15.0-20-generic                 4.15.0-20.21                        amd64        Signed kernel image generic
rc  linux-image-4.15.0-22-generic                 4.15.0-22.24                        amd64        Signed kernel image generic
ii  linux-image-4.15.0-23-generic                 4.15.0-23.25                        amd64        Signed kernel image generic
ii  linux-image-4.15.0-24-generic                 4.15.0-24.26                        amd64        Signed kernel image generic
ii  linux-image-generic                           4.15.0.23.25                        amd64        Generic Linux kernel image

```

If I type 
```
uname -r:4.15.0-24-generic

```

If I run the other commands to delete the 24 version how do I make the 23 version to become active or reinstall it? (Do I run those from the tty or the terminal on the lunched ubuntu session)

---

### Post by Xian on 2018-07-15
> **Delosari said:**
> 
If I run the other commands to delete the 24 version how do I make the 23 version to become active or reinstall it? (Do I run those from the tty or the terminal on the lunched ubuntu session)

You certainly don't need to reinstall V.23 ... it's already on your machine. On reboot you should boot into the previous safe version. Because you won't remove the linux-generic package itself, Ubuntu will still attempt to upgrade to a new kernel when available. You mentioned grub is not installed so I'm not able confirm with normal methods that the broken kernel is/isn't the default boot choice.

If you run commands from a launched session you'll get warnings about removing an active kernel ... which is fine so just proceed.

---

### Post by TRPrecht on 2018-07-15
I'm having the same issue and uncertain where to begin. Should I start a separate thread?

---

### Post by wildmanne39 on 2018-07-15
> **TRPrecht said:**
> I'm having the same issue and uncertain where to begin. Should I start a separate thread?

Yes please.

---

