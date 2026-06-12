---
title: "OBEX push on Ubuntu 12.10"
date: 2013-01-27
forum: General Help
---

### Post by Ryaniskira on 2013-01-27
I can send files via Bluetooth to my Android but I can't receive files from my Android nor browse its file system. My Android says my computer Does not support the OBEX push protocol. How can I fix this? Is there a package I can install to get the OBEX service running?

Dell Studio on a X86_64 Processor.

---

### Post by stepheny on 2013-01-28
I have exactly the same problem. Searching the web it seems that there are many of us with this problem.

If there is not a solution forthcoming I will send a bug report.

---

### Post by ninjaonchronic on 2013-04-10
Try using Synaptic Package Manager to download the following packages: obexpushd and ussp-push. You still wont be able to browse your device due to 12.10 bugs, but you will be able to send and recieve files after using the setup feature on blueman bluetooth device manager to connect devices and connecting through serial port and audio source. Worked for my Dell Studio 1749.

---

### Post by jcoles on 2013-04-22
I have the same problem in Xubuntu 12.10 with a Samsung cell phone. Adding obexpushd made it possible to push files from the PC to the phone. ussp-push didn't help at all. The PC doesn't show up on the list of devices to which you can send a file via Bluetooth. Fortunately, file transfer by USB cable works just fine using gMTP.

Blueman is quite unstable. Sometimes it takes several attempts to find and connect a device. After connecting and disconnecting services a few times, all further attempts to connect will fail and the only solution is to remove the device (on the PC and the phone) and start over. Very poor! 

I found my phone has settings for visibility of its folders over Bluetooth and an Authorize function for connected Bluetooth devices. After many cycles of deleting the device on both ends and re-pairing, I was finally able to connect to the serial port service and send a picture to the computer. There's no way it should be this difficult!

[Added later]One trick that has worked a few times on my phone is to browse the computer first before attempting to send it a pic. If you don't do this, the phone shows "sending" but makes no progress and times out. 

Even after all of this, Obex is still a near-total fail. Occasionally, the Browse Device function opens a file manager window listing my phone's folders, but when opened the folders appear to be empty. Most times though there is a lame error message about not receiving a reply. 

Does anyone know of an alternative (perhaps non-Ubuntu) Bluetooth package where everything actually works?

---

