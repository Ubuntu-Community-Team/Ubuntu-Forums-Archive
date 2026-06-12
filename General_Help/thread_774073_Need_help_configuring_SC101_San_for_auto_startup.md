---
title: "Need help configuring SC101 San for auto startup"
date: 2008-04-29
forum: General Help
---

### Post by SonicSteve on 2008-04-29
I recently bought a netgear sc101 san (network storage device). although there is no official support from Netgear there is support from an open source google project. 

[http://code.google.com/p/sc101-nbd/](http://code.google.com/p/sc101-nbd/)

My steps to make it work are as follows,
1. Initial device config done from a windows machine, partitioning etc. The setup can only be done this way. I called the raid mirror Netgear120
2. Run these commands from the Linux box after initial setup;



steve@ADbuntu:~$ [COLOR="Red"]sudo ut listall[/COLOR]
===============================================================================
VERSION  : 4.23.0                        ROOT IP ADDR : 192.168.100.117 
TOTAL(MB): 114469                        # PARTITIONS : 1
FREE (MB): 1829  
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
PARTITION                                LABEL           IP ADDR      SIZE (MB)
F026686C-153E-11DD-8902-0050047F7F82.m1  Netgear120      192.168.100.135 112640
===============================================================================
VERSION  : 4.23.0                        ROOT IP ADDR : 192.168.100.49  
TOTAL(MB): 114469                        # PARTITIONS : 1
FREE (MB): 1829  
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
PARTITION                                LABEL           IP ADDR      SIZE (MB)
F026686C-153E-11DD-8902-0050047F7F82     Netgear120      192.168.100.130 112640
===============================================================================
steve@ADbuntu:~$ [COLOR="Red"]sudo modprobe nbd[/COLOR]
steve@ADbuntu:~$ [COLOR="Red"]sudo ut attach F026686C-153E-11DD-8902-0050047F7F82 /dev/nbd0[/COLOR]
steve@ADbuntu:~$ [COLOR="Red"]sudo mount -a[/COLOR]


In order to use this device I need to run this process every startup. 

In order to automate this process I tried adding a line in FSTAB file but it seems that things like the NBD driver haven't been loaded yet and startup hangs telling me that the device doesn't exist. I can continue by pressing Control D.

So again the device is usable and working quite well, I would just like to  have it automount, I would even settle for making a custom script that I could sit on my desktop and run after bootup.

---

### Post by SonicSteve on 2008-04-29
Perhaps someone can answer this also.

If I use the sessions manager to add kernel modules when do they get loaded? Before login, after login, shortly after grub gets things going? I need to know if using Sessions to load a kernel module has any hope of working.

Thanks.

---

### Post by magicfab on 2008-06-13
To have the nbd module load at startup simply add it to the /etc/modules file.

You can edit it as root by issuing going to Applications > Accessories > Terminal and issuing this command:
gksu gedit /etc/modules

Then at the very end of the file simply add the word "nbd" on a line by itself.

If you'd like this to make it into Ubuntu, please subscribe to this bug:
[https://bugs.edge.launchpad.net/ubuntu/+bug/213744](https://bugs.edge.launchpad.net/ubuntu/+bug/213744)

Cheers,

---

### Post by SonicSteve on 2008-06-21
Thanks, 
I subscribed. It would be nice to not have to load this up every time I install, or re-boot.

---

