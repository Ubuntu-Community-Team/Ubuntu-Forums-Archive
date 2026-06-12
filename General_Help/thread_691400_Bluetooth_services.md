---
title: "Bluetooth services"
date: 2008-02-08
forum: General Help
---

### Post by lsavidge on 2008-02-08
Hi,

I have the Bluetooth applet running at startup. In the preferences I have enabled all 4 services, input, network, serial and audio services but when I scan for services from my phone it doesn't see anything at all. I don't seem to be able to send files to the computer but I can send from it. The computer and phone are paired with a trusted connection. I seem to have loads of bluetooth software on the computer and I believe everything is set up correctly.

What I am trying to do is allow bi-directional file sharing between the two devices with the minimum of fuss. Ideally I would like to use my USB headset which is a GN Netcom GN 8110 device as a headset for my mobile phone. The headset is not a bluetooth device but it is an audio device. If I have enabled the audio service on the PC over bluetooth, why can't I use my headset as a device to talk to contacts on my phone as if it were a bluetooth headset?

Thanks,

Lee

---

### Post by Keith Hedger on 2008-02-08
You need to install gnome-bluetooth its in the repos use synaptic to install or ```
apt-get install gnome-bluetooth
```
and then go to Applications->Accessories->Blue Tooth File Sharing

---

