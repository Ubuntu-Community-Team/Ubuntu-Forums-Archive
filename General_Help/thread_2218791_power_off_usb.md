---
title: "power off usb"
date: 2014-04-22
forum: General Help
---

### Post by MikeCyber on 2014-04-22
Hi
for Metro LL I need to disable my USB CH Pedals and joystick. When I'm finished gaming I need them for X-Plane.

echo '3-3' |sudo tee /sys/bus/usb/drivers/usb/unbind

disables ok for Metro but I need to replug them for x-plane. echo '3-3' |sudo tee /sys/bus/usb/drivers/usb/bind does not work 
correctly. I'm on Ubuntu 14.04.
Any help?
Thanks

---

### Post by varunendra on 2014-04-22
Many USB devices need a full Power Cycle to reset properly. The command-line tricks can only simulate a logical disconnect-reconnect, but there is no way to do a power cycle on USB interfaces using commands. At least this is what I found some time ago after many days of intensive search on the subject (I needed to power cycle my USB modem to reset it).

So IF the trick you already tried doesn't work, there is probably no way around other than taking **_'extreme'_** measures like cutting prints and introducing an electronic switch on the circuit board that works on binary signals that you can supply using commands. Obviously, this is almost rocket-science for most computer users, and quite a challenge for even the professionals. :|

---

### Post by bapoumba on 2014-04-22
Hmm, after resuming from suspend yesterday, usb was down, and I search how to bring it back up. Ended up rebooting.. I have saved the dmesg and X logs in case I could use it somehow, but reading your post varun makes me think there is no real way.. Thanks :)
I'll try and see if it happens again (that would be a bug then).

---

### Post by varunendra on 2014-04-22
> **bapoumba said:**
> Hmm, after resuming from suspend yesterday, usb was down, and I search how to bring it back up. Ended up rebooting.. I have saved the dmesg and X logs in case I could use it somehow, but reading your post varun makes me think there is no real way..

In my experience (and experiments on a few different systems) so far, the internal hub resets just fine with the trick Mike used (unbind/bind the PCI ID of the hub). It were just a few external USB devices that needed a full power cycle.

I determine the PCI ID of the USB bus/hub (e.g., **00:1d.0**) with "lspci" command, determine its driver (which one of uhci_hcd, ohci_hcd, ehci_hcd, xhci_hcd etc, can also be 'pci' instead of 'hcd'..) then use the commands like -
```
echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/unbind
echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/bind
```
..keeping a gap of about 6 seconds or more between the commands (actually I have put them in a script with a 6 sec. 'sleep' in-between.

It is just like re-loading a module, only we use 'unbind/bind' instead of 'modprobe'.

---

### Post by bapoumba on 2014-04-23
Will report back here if it happens again, thanks :)

---

