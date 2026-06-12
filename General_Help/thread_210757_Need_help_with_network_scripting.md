---
title: "Need help with network scripting"
date: 2006-07-07
forum: General Help
---

### Post by finite9 on 2006-07-07
I have a dreaded Broadcom 54g wireless card (bcm43xx) and after weeks of forum trawling, I have managed to get the driver working:

6.06 LTS amd64 using in-built bcm43xx driver and wl_apsta.o firmware from bcm43xx team as recommended by wiki (not ndiswrapper).

So the thing is after installing driver etc, that I do sudo iwlist eth1 scan and get "hardware doesn't support scanning" or "no scan results".  As I have an Acer Aspire 5021WLMi, it needs another non-repo module called acer_acpi to make the wireless work.  So I install that, no problem, then modprobe bcm43xx and modprobe acer_acpi, followed by a couple of echo commands to make acer_acpi work.  I have already blacklisted ndiswrapper.

If I do this manually (the modprobing) after booting up, then I can successfully scan for APs using sudo iwlist eth1 scan.  If I put all of this into a script and use post-up in /etc/network/interfaces, then it never works and im back to "no scan results" or "hardware doesnt support scanning".

My interfaces file looks like this:

auto eth1
iface eth1 inet dhcp
post-up /etc/network/WirelessAcerAcpi

The script file, WirelessAcerAcpi is root owned with 754 permissions.  These are it's contents:

#!/bin/sh 
case "$1" in 
start|" ") 
modprobe bcm43xx 
modprobe acer_acpi 
chmod 777 /proc/acpi/acer/wireless 
echo "enabled: 1" >/proc/acpi/acer/wireless
;; 
stop) 
echo "enabled: 0" >/proc/acpi/acer/wireless
modprobe -r acer_acpi
modprobe -r bcm43xx
;; 
esac

Please can someone give me any tips as to why this doesn't work!!  I want to call the script in /etc/network/interfaces so that I can get my wireless up and running (read scanning) when restarting networking with '/etc/init.d/networking restart', and I dont want to have to type all this in manually when I boot.  I don't know if it's the script that is wrong (I got it from one of the wiki guides for broadcom wireless) or whether I'm doing something wrong with assuming that I can stick it in post-up.  I don't use pre-up because it all works manually after booting computer, but I did try pre-up with same effect.

Would really appreciate some help with this.

--finite9

---

### Post by mgor on 2006-07-07
post-up makes the script execute after it have tried bringing the network interface up.

from interfaces(5)
> post-up command
              Run  command  after  bringing the interface up.  If this command
              fails then ifup aborts, refraining from marking the interface as
              configured  (even  though it has really been configured), prints
              an error message, and exits with status 0.   This  behavior  may
              change in the future.


you might want to use pre-up, since the modules should be loaded *before* you bring the interface up.
> pre-up command
              Run command before bringing the interface up.  If  this  command
              fails then ifup aborts, refraining from marking the interface as
              configured, prints an error message, and exits  with  status  0.
              This behavior may change in the future.

---

### Post by finite9 on 2006-07-13
Thanks for the reply but I figured it out eventually.   I had a script that should be run with "<script-name> start" in init.d, but this wasn't working when used in /etc/network/interfaces with pre-up.  However, if I created a simple text document and made it executable  and root owned with the following commands:

modprobe bcm43xx
modprobe acer_acpi

then this worked perfectly with pre-up in interfaces.

---

