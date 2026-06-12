---
title: "net surveillance web"
date: 2022-03-03
forum: General Help
---

### Post by m0nam3 on 2022-03-03
Hello
I recently switched to ubuntu operating system.
I'm still learning, but I come today to ask for your help with the following:
I have a surveillance system that when accessing via the WEB, it is necessary to have a plugin called "net surveillance web" but I am not able to find it for this operating system.
How can I resolve this?
Thank you for your attention.
Antonio Rosa / Azores

---

### Post by TheFu on 2022-03-03
Contact the vendor and ask for the plugin for Linux.

If you exclusively use Ubuntu, you'll want to be careful purchasing any external devices. My best advice is to stay with devices that support standard protocols and avoid devices with proprietary software.  

Even that doesn't always work, so checking each device for Ubuntu / Linux support before purchase is still necessary. Look for 2+ yrs of plug-n-play support, since nobody likes the hassle of looking for special drivers or special programs.

I bought a very cheap webcam to place in the attic. It has night vision and was supposed to work over the internet.  I didn't check and discovered later that the device was sending all the video to the vendor and the vendor only make an Android app for access. 

No web page. 
No direct stream.  
Basically, only a specific android device, **not** a tablet, can access the videos, unless I go into the attic and physically swap the microSD card every few days.  That's a major hassle. I figure I got $22 worth from the device.  Next time, I know to get a full IP-cam that either streams video to a connected target server on my LAN or has a built-in webpage to control access from my LAN.

On the MicroSD, the videos are stored in 5 min video chunks a h.264 in mp4 containers. That's fairly standard, so I'm happy. Here's a screen capture of what I discovered last year:

---

### Post by Holger_Gehrke on 2022-03-03
As far as my limited research shows "net surveillance web" is not a plugin, it's an ActiveX control. That means it will only work with Microsoft Internet Explorer (not Microsoft Edge, not Chrome, not Firefox; none of those support ActiveX which is an old and close to abandoned completely proprietary Microsoft technology). IE is not available for Linux and running it through Wine (a tool for running Windows Programs on Linux) does not work well.

Holger

---

### Post by mIk3_08 on 2022-03-03
> **m0nam3 said:**
> Hello
I recently switched to ubuntu operating system.
I'm still learning, but I come today to ask for your help with the following:
I have a surveillance system that when accessing via the WEB, it is necessary to have a plugin called "net surveillance web" but I am not able to find it for this operating system.
How can I resolve this?
Thank you for your attention.
Antonio Rosa / Azores
 I don't really know about this but firefox has a "My IPCam for IP Camera"


> **Holger_Gehrke said:**
> As far as my limited research shows "net  surveillance web" is not a plugin, it's an ActiveX control. That means  it will only work with Microsoft Internet Explorer (not Microsoft Edge,  not Chrome, not Firefox; none of those support ActiveX which is an old  and close to abandoned completely proprietary Microsoft technology). IE  is not available for Linux and running it through Wine (a tool for  running Windows Programs on Linux) does not work well.
Holger
I think firefox has already have this one. The "net  surveillance web" it so happen that, its a commercial for some features to be enabled.

---

