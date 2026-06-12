---
title: "Can't Find Device Manager"
date: 2008-06-08
forum: General Help
---

### Post by Inc0ming on 2008-06-08
Trying to setup my wireless internet on Ubuntu, but, for troubleshooting purposes, I need to check if my wireless card is recognized by Ubuntu. So, according to Help and Support app, under System > Preferences there's suppose to be Hardware Information but my Ubuntu doesn't have it. Can someone get me some answers?

Thanks.

---

### Post by kaibob on 2008-06-08
The device manager that was present in Gutsy is gone. There is a replacement utility called gnome-device-manager. It's in the repo's. However, I do not know if it will be of help with your wireless card.

---

### Post by Inc0ming on 2008-06-08
Thanks for the fast reply.

Where is the "repo's"

I have a WMP300N wireless card.

---

### Post by kaibob on 2008-06-08
> **Inc0ming said:**
> Thanks for the fast reply.

Where is the "repo's"

Sorry--I was being lazy. You can install gnome-device-manager by way of the Synaptic Package Manager. The actual package name is gnome-device-manager.

---

### Post by Inc0ming on 2008-06-08
I don't have gnone-device-manager listed in the Synaptic Package Manager. The things that should be above and below the device manager are gnome-desktop-data and gnone-doc-utils.

---

### Post by kaibob on 2008-06-08
Load Synaptic Package Manager and click on *Settings > Repositories > Ubuntu Software*. Make sure you have a check mark next to all items except source code (do not change CD-Rom setting). Close the dialog, click on the reload button, and recheck to see if you can find gnome device manager.

---

### Post by Inc0ming on 2008-06-08
Didn't work. Am I suppose to be connected to the internet for me to get it?

---

### Post by avtolle on 2008-06-08
> **Inc0ming said:**
> Didn't work. Am I suppose to be connected to the internet for me to get it?
Yes. You seem to be connected now, as you are posting here; are you using another computer or OS to do so?

---

### Post by cariboo on 2008-06-08
I just tried the gnome-device-manager, I don't think it is going to be a whole lot of help. The easiest way (for me at least:)) is in a terminal type:

```
lspci
```

and hit enter. Terminal is located at Application-->Accessories-->Terminal. You will get a listing something like this:

```
1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```

I cut a lot of the extra just for illustration purposes. As you can see in line 2, it displays my ethernet controller. You should have something similar, accept by a different manufacturer. This will give us a starting point.

Jim

---

### Post by kaibob on 2008-06-08
Posting deleted--better advice provided by cariboo907.

---

### Post by Inc0ming on 2008-06-08
Well, I can't do a direct copy and paste since I don't have internet on my Ubuntu OS. 

None the less, my second line says "00:01:.0 PCI bridge: Intel Corp. 82G33/G31/P35/P31 Express PCI Express Root Port (rev 2)"

And yes, I'm using a different computer to be posting on here.

---

