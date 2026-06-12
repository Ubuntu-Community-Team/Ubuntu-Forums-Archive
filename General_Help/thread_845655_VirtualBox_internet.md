---
title: "VirtualBox internet"
date: 2008-06-30
forum: General Help
---

### Post by cowdog88 on 2008-06-30
I have a windows vista host and Ubuntu HH on my virtual box.  Is it possible to get on the internet in my virtualBox?

---

### Post by prince_niceguy on 2008-06-30
yes you should be able to do that. make sure you configure to share the network card.

---

### Post by dominiquec on 2008-06-30
I haven't had to configure anything special with my Virtualbox to enable guests to access the Internet.  They usually connect immediately via NAT (internal IP address so they can connect outside, but not vice versa.)

---

### Post by soccerboy on 2008-06-30
same here.  no config needed.  check if you use the version of virtual box from ubuntu repos or the innotek version.

---

### Post by forger on 2008-06-30
> **soccerboy said:**
> same here.  no config needed.  check if you use the version of virtual box from ubuntu repos or the innotek version.

ubuntu is the guest o/s, the host is vista, it's not virtualbox-ose ;)

---

### Post by forger on 2008-07-01
Choose your virtual machine > Settings > Network > Adapter Type: PC-net PCI II (**not III**)

try booting the virtual machine using the live cd, check if the internet is working and reinstall your virtual machine

---

### Post by cowdog88 on 2008-07-01
I went to machine, settings, network, and adapter 1 was enabled attached to NAT the MAC address was assigned and the cable connected checkbox was checked.  There were no host interfaces.  Is there anything else i need to do?

---

### Post by dje on 2008-07-01
For Vista you must install the guest additions to get the internet. Go to Devices >> Install Guest Additions in the VM window (the window Vista runs in), in the Vista guest an autorun prompt should appear asking you to run the guest additions installer. Run it and then reboot Vista when done. You will now have internet and many new features including seamless mode and mouse integration

hope that helps,
dje

---

### Post by cowdog88 on 2008-07-01
I have Ubuntu running in the virtualbox.  Do I still need to install the guest additions?

---

### Post by dje on 2008-07-01
woops i completely misread the first post :oops:, it's a Vista host and Ubuntu guest. The internet should work immediately? sorry for my useless previous post

dje

---

### Post by cowdog88 on 2008-07-01
Its cool.  I think I might have found my problem.  I am running an older version of VirtualBox (1.5.2) and I think they are on 1.6 or something now, so ill try upgrading.

---

### Post by Azurise on 2010-09-21
> **forger said:**
> Choose your virtual machine > Settings > Network > Adapter Type: PC-net PCI II (**not III**)

try booting the virtual machine using the live cd, check if the internet is working and reinstall your virtual machine

This was the key to solving it. I had internet connectivity issues as well.

I'm using Virtualbox 3.2.8 r64453, installed on windows XP 32bit. The virtual system is Ubuntu 10.04.1. When I installed the system, I had the adapter set to Bridged + wireless... however it **appeared** that packets were sent and received no matter what I switched it to - at least during installation. Unfortunately, I wasn't paying attention to that setting. Tried internet with "try before install" -- nothing. Tried the internet after install, shutting down ubuntu, and starting it up again. This time it appeared to have a signal, but nothing that Firefox could see.

So, my original config was 
Attached to: Bridged Adapter
Adapter Type: Intel PRO /1000 MT Desktop

I switched it to this, and then it connected to Google, ubuntu.com etc
Attached to: NAT
Adapter: PCnet-PCI II

[http://i55.tinypic.com/2udzxhj.png](http://i55.tinypic.com/2udzxhj.png)

**I did not reinstall Ubuntu!** 
I just shut it down, changed settings and started it back up.

---

