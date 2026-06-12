---
title: "Need to backup data, no usb recognised"
date: 2020-03-22
forum: General Help
---

### Post by mr-zx on 2020-03-22
Any help given will be fully appreciated, 

I was having network issues since upgrading from 16 to 18.04, so when it happened yesterday I decided to give up on linux and go back to windows. So i thought let me copy the stuff I need, but plugging in my usb was not recognised. I can see the light on my usb device but no driver recognised,  same with any other device I plugged in (phones, tablet etc).

I have tried everything and now my ubuntu shows an internal error on some start-ups with error stating something like " Xwayland crashed with sigabrt in OSAbrt()".


Please does anyone have any ingenious method to get my required files without doing something that might cause boot problems ( ex: I don't want to re-install the os, just want the files then I will nuke the whole os). Being able to boot gives me hope to recover my files in my home folder

---

### Post by Impavidus on 2020-03-22
Can you boot a live disk? That should allow you to access your internal hard drive.

---

### Post by tea for one on 2020-03-22
> **mr-zx said:**
> 
I have tried everything and now my ubuntu shows an internal error on some start-ups with error stating something like " Xwayland crashed with sigabrt in OSAbrt()".

Is the PC powered off at the moment?

Remove all usb devices (other than keyboard and mouse)

Assuming that you can reach the login screen, can you see the little **gear wheel** icon?

Click on the icon and select **Ubuntu** session rather than Wayland.

Any help?

---

### Post by mr-zx on 2020-03-22
The problem is I only have access to this laptop until sometime next week. I don't have the previous cd that I used anymore, but I can get some empty cd's. Don't know how I'm going to burn the data or even download the data on the cd? Or is it already on my current installation and somehow I can trigger it from boot?

---

### Post by mr-zx on 2020-03-22
I have tried all the options with unity(default), ubuntu, and ubuntu wayland. Although I don't get the error when I'm in ubuntu or unity, my hardware still don't work. 
And 1 thing I don't understand is, is there a way to get the dialog in my picture below bigger (would like to know what is after "Hardware Aero...")?
[https://imgur.com/a/20JBeta](https://imgur.com/a/20JBeta) 


It doesn't do anything's,  aeroplane mode still is enabled no matter how many times I press

---

### Post by HermanAB on 2020-03-22
Some options:
1. Ethernet works?  Copy data to another computer with ftp or scp.
2. PCMCIA/Cardbus still works?  Get a PCMCIA/Cardbus to USB adaptor.
3. Bluetooth works? Copy data over BT Serial to another computer or smart phone/tablet.

---

