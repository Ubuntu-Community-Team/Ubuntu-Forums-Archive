---
title: "Ubuntu won't boot"
date: 2007-05-02
forum: General Help
---

### Post by Pas3n7 on 2007-05-02
When I boot feisty, it hangs at the splash screen (bar almost filled, don't know if that really helps)

I enabled the boot log (edited /etc/default/bootlogd), then tried to boot, but when I checked it in the recovery console it said nothing had been logged yet.

The last thing I did was compile and install the latest cvs build of the [rt2500 driver]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads")

Is there any way I can get more information? or does anyone have any ideas at all?

---

### Post by kbuel on 2007-05-02
if you have an ipod or other usb device attached, try disconnecting them before you boot.  I have seen multiple usb devices halt a boot (on windows and linux)

---

### Post by blazercist on 2007-05-02
you are using a laptop i assume?  which laptop, whats your hardware? have you tried booting in verbose mode?  whats the last thing u see when booting before it hangs?

---

### Post by Pas3n7 on 2007-05-02
kbuel - nothing in the usb ports, thanks for the suggestion though

blazercist - 

Yes, a dell inspiron 1150 (haven't had much trouble with ubuntu in the past) it was running fine before I rebooted.

I just tried with the quiet and splash flags off, the last thing I got was:

```
* Starting System Tools Backends system-tools-backends [ok] [
   50.704000] BUG: soft lockup detected on CPU#0!
```

---

### Post by blazercist on 2007-05-02
ok, lets try some more questions... I cant find any specs with enough detail about your hardware... you say the last thing you did was compile the cvs rt2500 driver, did you install it via modprobe?  Also, what chipset is it exactly, my understanding is that the rt2500 driver supports rt2500/rt61/rt73 based cards and perhaps more.  Does the laptop have a hard on/off button for wifi?  Can you boot in recovery mode?

---

### Post by Pas3n7 on 2007-05-02
Thanks so much for your help, I really appreciate it.

I just did a make, then a make install.

It is an rt2500 chipset (a hawking HWC-54d pc card). The laptop does not have a hard on/off button for wifi, as it has no onboard wifi. And yes, I can boot in recovery mode.

Is there anything else that would be helpful to know?

---

### Post by blazercist on 2007-05-02
Ok, this is what you need to do, boot into recovery mode and do the follwoing in console:

sudo apt-get remove network-manager

If this works then enjoy, if not try removing the wifi card and booting... If you can boot without the wifi card plugged in then we've narrowed ur problem down to the wifi and we can assume its the rt2500 module.

I have a rt61 wifi card thats built in, I could not boot feisty with network-manager installed for some reason that driver and network-manager do not play well together.  maybe this is your problem

---

### Post by Pas3n7 on 2007-05-02
blazercist, you are my hero.

Took out the card and it booted just fine.

Now, is there some way I can just keep the network-manager from starting at boot, so I can just start it manually. I'd like to have it continue to manage my wired connections if that's possible.

Again, I can't thank you enough for your help.

---

### Post by Pas3n7 on 2007-05-02
actually, scratch that, I didn't realize it would freeze the system every time I inserted the card. I just removed network-manager like you said.

Once again, thanks

---

### Post by blazercist on 2007-05-02
Unfortunately, your wish cannot be granted.  I uninstalled network-manager and then thinking the same thing, I reinstalled it from a running X session, it crashed ofcourse and I couldn't boot until I removed it again.  You'll have to uninstall it completely and use a script for the wifi card.  The wired connection will still work as long as it plugged in at boot it will come up automatically, if its not plugged in at boot then you'll need to bring it up manually (assuming you have a router with dhcp or ur broadband modem acts a a dhcp server you can do this with the command: sudo dhclient eth0

The script for bringing up the wifi card is another story you can find some instructions in this forum in a thread called "RT61 Wireless Solved" good luck.

edit: If i have a chance tonight ill post my wireless script in here so you have an idea of what to do.

---

