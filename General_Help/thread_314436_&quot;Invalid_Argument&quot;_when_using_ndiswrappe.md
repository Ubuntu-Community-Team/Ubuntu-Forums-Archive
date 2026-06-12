---
title: "&quot;Invalid Argument&quot; when using ndiswrapper"
date: 2006-12-07
forum: General Help
---

### Post by sankarj12 on 2006-12-07
Hi. I have properly installed ndiswrapper on the final release of Edgy Eft. I added the proper driver for the NETGEAR WG111 v1 USB adapter. I did```
sudo ndiswrapper -m
```to write modprobe information. When I do```
sudo modprobe ndiswrapper
```I get an invalid argument. What am I doing wrong?](*,)

I know this is a wireless networking question, but I thought that it might me a general issue because this never happened before.  I think it's something to do with modprobe than with ndiswrapper or wireless networking.  I have posted into the wireless and networking forum with no answer.  Can something please help me?

---

### Post by wieman01 on 2006-12-07
Perhaps it's the sequence of the commands that trips you up. Please try to adhere to this guide:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by Balle-Larsen on 2006-12-16
sankarj12,

When I installed ndiswrapper with synaptic I had the same error message.
ndiswrapper-utils depends on ndiswrapper-utils-1.1
After installing ndiswrapper-utils-1.8 additionally, ndiswrapper run without the error.

---

