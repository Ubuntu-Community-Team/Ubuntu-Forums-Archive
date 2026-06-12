---
title: "Remote Desktop Connection lost after rebooting - Ubuntu 23.10"
date: 2023-11-01
forum: General Help
---

### Post by edurangel on 2023-11-01
Hello guys, 

I'm new to Linux environment and it's distributions. Recently I installed Ubuntu 23.10 on a old laptop, created an user and enabled remote access and SSH. To connect to this machine I was using Windows RDC, and it worked fine until I had to reboot my Ubuntu machine, because each time it rebooted I had to manually login in order to remotely connect to it. 

So, what I did was enabling the Autologin, on Settings, but with this option enabled, after every reboot my Remote Connection password reset to a new password. 

I don't know if is a bug or if it's a noob mistake. 

How can I setup my ubuntu machine so I can remotely connect to it whenever, even after a reboot?

Thank you all.

---

### Post by MAFoElffen on 2023-11-02
Since from Windows, I am assuming you meant RDP. If so, what where you using on the Linux side? xrdp server?

Using that protocol, you can not be logged in locally to the user that you are trying to connect with through RDP. That protocol only allows a user to be logged in once, one at a time. With machines that I run xrdp server (usually VM's), I usually get around that by creating an xrdp user, that only logs in via remote connections to that machine.

So for machines that have a GUI, that reboot on purpose or a result of a power failure, there is this gray area time period. It boots, and goes to the graphical login. Even if the users are configured for no sleep or hibernation, those setting do not get applied until someone logs in. If you leave it a login required, it tries to go to powersavers default settings, and shuts down after about 10 minutes. If you autologin to a user, if xdrp, then you cannot login as that specific user.

For my workstation and server, I have they both to not sleep or hibernate. If you have a machine with a GUI, and do not do that, if it times out while on the Graphical Login screen, it will blank/suspend the machine and not be reachable from shh. I have to do a few more things to keep my workstation alive and kicking, than my server...

The powerprofile is set to "performance".

In /etc/default/grub
```

GRUB_CMDLINE_LINUX_DEFAULT="-- video=uvesa:1920x1080-32@60,mtrr:3,ywrap,[COLOR=#ff0000]noblank consoleblank=0[/COLOR] init_on_alloc=0 intel_iommu=on iommu=pt kvm.ignore_msrs=1 vfio-pci.ids=8086:a780 igb.max_vfs=7"

```
I use LightDM as my DE. In /etc/lightdm/lightdm.conf.d/50-dpms.conf, I have:
```

[SeatDefaults]
display-setup-script=/usr/local/bin/dpms-stop

```
That call this custom user script 
```

#!/bin/sh
sudo xhost +si:localuser:lightdm # grants localuser rights to X session
sudo su lightdm -s /bin/bash <<HERE
/usr/bin/xset -dpms
/usr/bin/xset s noblank
/usr/bin/xset s off
exit
HERE

```
In my user options, then I have all user gsettings set to stay alive, never sleep or suspend, no screensaver.

---

