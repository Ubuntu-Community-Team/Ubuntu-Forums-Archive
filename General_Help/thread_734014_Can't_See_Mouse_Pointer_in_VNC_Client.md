---
title: "Can't See Mouse Pointer in VNC Client"
date: 2008-03-24
forum: General Help
---

### Post by andrewk8 on 2008-03-24
I've got a clean install of Ubuntu 7.10.  I enabled Remote Desktop using the default VNC server (System, Preferences, Remote Desktop).  I'm using UltraVNC client on Windows XP to control the desktop.  I can't see the Ubuntu mouse pointer in the VNC client.  All I see is the "dot" in the client representing the mouse position.

How can I see the Ubuntu mouse pointers through a VNC client?

---

### Post by artesian_spring on 2008-03-25
It's been a while since I've used VNC, so I could be wrong about this, but I think what you're experiencing is normal. As far as I recall, the dot is all that's shown to indicate the pointer location in a VNC client. Maybe there are settings you could edit to show the pointer, but that is beyond my knowledge.

---

### Post by jamesrfla on 2008-03-25
I would reboot the Ubuntu computer then try the VNC again. I had that same problem when I remoted into my Ubuntu computer.

---

### Post by daflame on 2008-03-25
I would highly recommend using FreeNX for security reasons.  VNC passwords can be hacked in transit.

---

### Post by andrewk8 on 2008-03-26
Rebooting didn't help.

I use UltraVNC server / client on a Windows XP machine frequently (client also on XP).  I always see the remote mouse pointer on the Windows XP server.  Whenever it changes to an hour glass, I-beam, etc., I see that, too.  The remote pointer obvioiusly lags behind the local dot due to network latency, etc., but at least I see them.  Ubuntu remote desktop w/ Windows XP UltraVNC client I only see the client's dot.

Out-of-the-box 7.10 install.  If I understand what Synaptic is telling me, System, Preferences, Remote Desktop is using the Vino VNC server.  Is that correct?

If so, is there a configuration setting in Vino to show the remote pointer?

---

### Post by andrewk8 on 2008-03-26
Quick read about FreeNX - sounds interesting.  Haven't absorbed all of the details.

I'm not terribly concerned about VNC security since I use it on a private network and don't have those ports opened on the router.  Would FreeNX allow secure remote access through ports that are opened (e.g. 80, etc.)

Is there a Windows FreeNX client?

Does FreeNX use a repeater between the host and client?  Can you configure it to NOT use a repeater on a LAN, but DO use a repeater on a WAN?

---

### Post by andrewk8 on 2008-04-16
> **andrewk8 said:**
> Rebooting didn't help.

I use UltraVNC server / client on a Windows XP machine frequently (client also on XP).  I always see the remote mouse pointer on the Windows XP server.  Whenever it changes to an hour glass, I-beam, etc., I see that, too.  The remote pointer obvioiusly lags behind the local dot due to network latency, etc., but at least I see them.  Ubuntu remote desktop w/ Windows XP UltraVNC client I only see the client's dot.

Out-of-the-box 7.10 install.  If I understand what Synaptic is telling me, System, Preferences, Remote Desktop is using the Vino VNC server.  Is that correct?

If so, is there a configuration setting in Vino to show the remote pointer?

Follow-up:  I've done a bit of poking around.  Vino functionality is exactly what I want, but it is quite slow (even over a LAN) and lacks capabilities of its more refined siblings, such as the ability to display the remote mouse pointer.  I was wanting to improve the performance of the VNC server plus add the bells-and whistles, but apparently Vino is the only vncserver that provides the functionality "vncserver :0".

This is very disappointing.

Does ANYONE have recommendations for a high-performance Vino substitute that provides seamless use of the primary desktop both locally and remotely?  The client has to run on Windows.

---

