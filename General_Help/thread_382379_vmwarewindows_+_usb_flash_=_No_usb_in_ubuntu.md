---
title: "vmware/windows + usb flash = No usb in ubuntu"
date: 2007-03-12
forum: General Help
---

### Post by kpkeerthi on 2007-03-12
I have vmware running windows in edgy. But when I plug in usb flash drive, windows steals it completely and ubuntu can't see it. ubuntu can only read/write when vmware is NOT running. Any ideas? Thanks.

---

### Post by Pontiac on 2007-03-12
Within VMWare setup for that virtual machine, remove the USB support, or, ensure that you do not have it setup to automatically connect the USB devices on start up.  In other words, set the USB devices from somewhere in the pull downs to NOT "connect on startup".

---

### Post by kpkeerthi on 2007-03-12
> **Pontiac said:**
> Within VMWare setup for that virtual machine, remove the USB support, or, ensure that you do not have it setup to automatically connect the USB devices on start up.  In other words, set the USB devices from somewhere in the pull downs to NOT "connect on startup".

Thanks... but is it not possible to have access to the usb drive from both vmware/windows and ubuntu (when both are running) at the same time?

---

### Post by Pontiac on 2007-03-12
Unfortunately, no.

The issue comes down to sharing information between the client and the server.  Server being your actual machine and the client being the VM machine.  Both the server and the client would think that its got full control of the device, which can cause a lot of headaches for the device.  In a networking situation, for example, clients have to make requests for the server to do something with that file, be it read, write, or delete, etc.  The client *NEVER* has direct physical access to the file.  The server just feeds the client the information it wants.

One way you may be able to get around this fault is setup a share on the server, then have the client access the key through that share.

---

### Post by RudolfMDLT on 2007-03-12
What I have done is share the respective folders and then in windows map a network drive to these folders, the problem comes into play with Bluetooth dongles where I can't map to the device and actually need it's drivers loaded on EITHER VM-Windows or Ubuntu.

---

### Post by Pontiac on 2007-03-12
I have VMWare at work, and fortunately I also do have a USB Bluetooth Dongle I will play with to see if I can get you fixed up.

---

### Post by kpkeerthi on 2007-03-12
> **Pontiac said:**
> Unfortunately, no.

The issue comes down to sharing information between the client and the server.  Server being your actual machine and the client being the VM machine.  Both the server and the client would think that its got full control of the device, which can cause a lot of headaches for the device.  In a networking situation, for example, clients have to make requests for the server to do something with that file, be it read, write, or delete, etc.  The client *NEVER* has direct physical access to the file.  The server just feeds the client the information it wants.
Really appreciate your explanation.

> 
One way you may be able to get around this fault is setup a share on the server, then have the client access the key through that share.

Great tip. And... it worked like a charm. Thank you very much.

---

### Post by Pontiac on 2007-03-12
No problem. :)  Enjoy.

---

