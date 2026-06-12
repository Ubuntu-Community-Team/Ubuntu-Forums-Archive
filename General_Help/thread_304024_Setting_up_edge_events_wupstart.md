---
title: "Setting up edge events w/upstart"
date: 2006-11-21
forum: General Help
---

### Post by tayloratosu on 2006-11-21
I have a linux-powered PDA (Zaurus 5500), and when I connect it to my desktop via a usb cable, the desktop loads the usbnet module automatically.

Under Dapper Drake and hotplug, I was able to have the desktop PC automatically run a script to set up networking for my Zaurus whenever this happened.  Now that I've upgraded to Edgy Eft and upstart, I can't.

Looking through the upstart docs, which seem to be both rough and fluid, I think I need to create an "edge event" under /etc/events.d, and I think the edge event needs to look something like:

on <whenever-usbnet-module-is-loaded>
   exec <my-little-network-setup-script>

I just can't figure out what to use for <whenever-usbnet-module-is-loaded>.  Can anyone give me some pointers?  Thanks.

Doug

---

### Post by keybuk on 2006-11-23
> **tayloratosu said:**
> I have a linux-powered PDA (Zaurus 5500), and when I connect it to my desktop via a usb cable, the desktop loads the usbnet module automatically.

Under Dapper Drake and hotplug, I was able to have the desktop PC automatically run a script to set up networking for my Zaurus whenever this happened.  Now that I've upgraded to Edgy Eft and upstart, I can't.

Looking through the upstart docs, which seem to be both rough and fluid, I think I need to create an "edge event" under /etc/events.d, and I think the edge event needs to look something like:

on <whenever-usbnet-module-is-loaded>
   exec <my-little-network-setup-script>

I just can't figure out what to use for <whenever-usbnet-module-is-loaded>.  Can anyone give me some pointers?  Thanks.

Doug

You'd need to use udev to send the message.  This could be done with something like:

  SUBSYSTEM=="module", ACTION=="add", RUN+="initctl trigger %k-module-loaded"

And then use "on usbnet-module-loaded" in the job definition.

---

