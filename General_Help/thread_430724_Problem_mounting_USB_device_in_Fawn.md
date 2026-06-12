---
title: "Problem mounting USB device in Fawn"
date: 2007-05-02
forum: General Help
---

### Post by Xitron on 2007-05-02
I have a TrEO 600 phone that I connect to my computer (Dell Latitude 800 notebook) via USB.  In the past (under Edgy), when tailing /var/log/messages, I could see that when I clicked on the hotsync button the system would recognize the device, and assign it a reasonable address such as /dev/ttyUSB01.

Now, I get the following sort of message...

  May  2 09:27:23 localhost kernel: [ 5365.044000] usb 2-6.1: new full speed USB device using ehci_hcd and address 9
  May  2 09:27:24 localhost kernel: [ 5365.136000] usb 2-6.1: configuration #1 chosen from 1 choice

So I *seem* to be getting a good connection.  My problem is that in Jpilot, under File-Preferences-Settings(tab), I am asked to fill in "Serial Port (/dev/ttyS0, /dev/pilot)" into which I always inserted whichever /dev I saw in /var/log/messages, ie. /dev/ttyUSB0, etc.  I've no idea what address is to be inserted based on "new full speed USB device using ehci_hcd and address 9" or "configuration #1 chosen from 1 choice".

I'm also a wee bit frustrated that the device changes /dev locations constantly, necessitating a frequent change of the pointer in Jpilot, a job which must be done very quickly, before the USB /dev times out and quits.

Is there a way to predesignate my phone as a static /dev location where it will *always* be when I plug it in.

Your knowledge and help are appreciated.

Unca Xitron

---

### Post by lazyart on 2007-05-04
Just try setting your device connection to usb: and you might be amazed.

I use jpilot on my Edgy box, and simply gave up on USB sync with my T|X and used wifi.  However, I just installed Feisty on another machine and while I haven't yet used jpilot there I did do a sync to Evolution and usb: worked.  On the first try.  I nearly cried.

---

### Post by Xitron on 2007-05-04
Thank you very much for your reply, lazyart.  I'm wondering if you can expand on this a bit.  I'm running J-Pilot version 0.99.9.2  I see no option in the preferences that will allow me to select USB as the device connection.  I've only ever managed it by selecting /dev/ttyUSB0 or /dev/ttyUSB01 as the serial device.  Is this a version thing (installed via apt-get install) or am I missing a setting location?  I'm also using evolution, but I haven't used it to sync the TrEO for a while as I got tired of seeing my enormous contact list populating my phone contact list.  I'm game, if that's what I'm going to need to do.

Unca Xitron

---

### Post by Xitron on 2007-05-04
Never mind, lazyart.  I installed gnome-pilot and it does the whole USB thing.  Thanks so much for your help!

Unca Xitron

---

### Post by lazyart on 2007-05-13
That works too.  In jpilot however, you would just type usb: for the serial pot.

---

