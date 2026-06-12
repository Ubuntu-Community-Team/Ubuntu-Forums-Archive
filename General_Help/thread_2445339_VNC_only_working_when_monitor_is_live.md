---
title: "VNC only working when monitor is live"
date: 2020-06-12
forum: General Help
---

### Post by johnwalker2 on 2020-06-12
I am running Ubuntu 20.04 and want to share its desktop to my mac. My mac has a second monitor and rather than let the Ubuntu PC have sole use of it I would rather continue with it connected to my iMac as a second screen and use desktop sharing to access the Ubuntu PC. I use a KVM switch to switch the second monitor between may mac and PC. I have managed to get the desktop sharing working, and can connect to the Ubuntu PC from my mac. But the connection only works while the monitor is actually KVM'd to the Ubuntu PC, which is pointless. When I switch the KVM so the monitor becomes the second screen for the mac, the shared Ubuntu desktop appears to freeze, it does not accept input from the mac's separate keyboard (which is not connected via the KVM). Upon switching back to being a monitor for the Ubuntu PC, the shared screen on the mac springs back to life.

I have tried starting without a monitor at all on the Ubuntu PC. There is a user auto logged-in on the PC so the desktop sharing is offered to the mac. I log in using the VNC password, and the shared desktop asks for the user password to unlock the keychain. That would be fine, but again it will not accept keyboard input. If I attach the monitor to the headless PC, it does accept input from the mac keyboard.

I would like to get this working! Thanks for any help.

---

### Post by ActionParsnip on 2020-06-12
What are you wanting to do on the Ubuntu system that you need a GUI to perform, please? There may be a sleeker solution to when you want to do.

---

### Post by johnwalker2 on 2020-06-12
I am running Virt Manager which does not wun on macOS or Windows AFAIK

---

### Post by sturmey2 on 2020-06-22
Asking why you want a GUI is not helpful. Either you know how to get it to work, or you're wasting everyone's time. If I want a remote GUI, I shouldn't have to justify why. There ar many reasons to want a remote GUI on a remote desktop. Perhaps a linux equivalent to RDP, or perhaps I'm using it for video edit and rendering and need to see what the edit looks like before suspending the session and browsing on my laptop.

---

### Post by QIII on 2020-06-22
What one wishes to accomplish is quite relative to the best answer to provide.

Now, as you are not the OP, please don't insinuate yourself into the conversation unless you have help to offer.

---

### Post by kneutron on 2020-06-22
--Try nomachine nx, it has clients for all 3 major platforms ( Mac / Linux / win ). The only problem I've run into is when I boot my ubuntu server without the monitor on, it confuses the startup graphics into too-low of a resolution.  But if you at least boot connected to a display to the point where X is asking for user/password, NX takes over and you can turn the monitor off.

[https://www.nomachine.com/download](https://www.nomachine.com/download)

---

### Post by HermanAB on 2020-06-23
Hmm, the Mac runs a FreeBSD phylum and it has an X server available called Quartz.  So, if you install and run Quartz, then you can SSH to the Ubuntu machine and run the remote program with the GUI displayed on the Mac, without the need for VNC.  This is mooch, mooch easier and secure also.

---

