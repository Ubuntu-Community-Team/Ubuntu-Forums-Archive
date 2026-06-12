---
title: "quickcam messenger"
date: 2008-03-08
forum: General Help
---

### Post by francky_51 on 2008-03-08
Hi all,
I have a logitech quickcam messenger webcam (Bus 003 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger) but with the module already installed in Gutsy (quickcam_messenger) videdo has a really poor quality (very dark and blue).
I decided to install the qc-usb-messenger driver found here [http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/).
So I launched the script quickcam.sh (found in the tar.gz)as root and everything went well.
The image into camorama is really, really !!! better now.
The problem is that after a reboot even if I load the quickcam module (the one I created with the script quickcam.sh) the module used is the quickcam_messenger.
If i do : sudo rmmod quick_messenger and then a sudo modprobe quickcam the /dev/video is not created. It's the same thing if I put the quickcam_messenger module in /etc/modprobe.d/blacklist and quickcam in /etc/modules file.

How can I remove the module quickcam_messenger included in Gutsy and use the quickcam module instead (the one I have compiled) ?

Thanks
Franck

---

### Post by fragos on 2008-03-08
You can "blacklist" the module you don't want any more.  I believe you can do that in /etc/modprobe.d/.  The following process worked for me when changing WiFi drivers.

Ubuntu 7.10/Issues/ipw3945 Wireless Network Module Issues
From DellLinuxWiki

When using the ipw3945 wireless module, the network connection can drop or lockup during heavy transfer rates.
Systems Affected: Inspiron 1420n, XPS 1330n
Impact: Wireless connection drops. Data transfer stops.
Workaround: Use network module iwl3945 instead.

Create a file called /etc/modprobe.d/blacklist-ipw3945 and add:
blacklist ipw3945

Add to /etc/modules:
iwl3945

Reboot. After the system restarts, verify that the module iwl3945 (and not ipw3945) is loaded:

$ lsmod | egrep 'Module|iwl|ipw'

You should see an output that looks like:

Module                  Size  Used by
iwl3945                88168  0
iwlwifi_mac80211      175112  1 iwl3945
cfg80211                7304  1 iwlwifi_mac80211

As seen, only the iwl3945 module is loaded.

---

### Post by francky_51 on 2008-03-09
It's what i did I put quickcam_messenger module in /etc/modprobe.d/blacklist and quickcam module in /etc/modules. 

The problem is that the video device is not ceated after a reboot.

I have to relaunch the script quickcam.sh to have video.

Is there an expert of module :) ?

Thanks

---

### Post by fragos on 2008-03-09
This web page an an email for the developer.

[http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)

---

### Post by Nevon on 2008-03-09
Do you think you could post an example picture from your webcam? I think I have the same one, and I just want to see what your picture quality is like.

---

### Post by algernon83 on 2008-03-09
I had the same problem. The issue is that, after a reboot, the old quickcam.ko is being loaded from /lib/modules/<uname>/ubuntu/media/quickcam/. So I had to delete quickcam.ko from that directory and replace it with the newly compiled quickcam.ko. Now modprobe installs the new quickcam module and all is well.

If I knew more about making Debian packages (read: if I knew anything about making Debian packages) I'd make one that depends on gcc and the kernel source/headers, compiles the driver, and puts it in the modules directory. As it is, I've e-mailed the author of the driver to recommend that this issue be mentioned in the documentation.

---

### Post by francky_51 on 2008-03-10
> **algernon83 said:**
> I had the same problem. The issue is that, after a reboot, the old quickcam.ko is being loaded from /lib/modules/<uname>/ubuntu/media/quickcam/. So I had to delete quickcam.ko from that directory and replace it with the newly compiled quickcam.ko. Now modprobe installs the new quickcam module and all is well.

If I knew more about making Debian packages (read: if I knew anything about making Debian packages) I'd make one that depends on gcc and the kernel source/headers, compiles the driver, and puts it in the modules directory. As it is, I've e-mailed the author of the driver to recommend that this issue be mentioned in the documentation.

Thanks :)
It worked.

@Nevon : Yes, no problem I will do it as soon as I will be at home.

---

### Post by francky_51 on 2008-03-10
Picture of my nabaztag :)

[[IMG]http://img368.imageshack.us/img368/7552/webcam1205180191pc1.png[/IMG]](http://imageshack.us)

---

