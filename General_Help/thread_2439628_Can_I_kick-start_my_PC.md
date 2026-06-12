---
title: "Can I kick-start my PC?"
date: 2020-03-30
forum: General Help
---

### Post by 2CV67 on 2020-03-30
Hi!
My main PC (Acer Aspire TC-100-007) has started to occasionally not want to boot.
There seems to be no reaction at all to the ON/OFF switch.
I suppose it is a problem in that switch & that it will get worse with time...

I should really look at the switch & try to get a replacement, but I may not be able to do that in time.

So I wonder what other choices I have.

Obviously I could just leave the PC ON but I don't really want that.

I know that with some/most/all PC's, if shut-down by the switch, the PC will boot automatically next time the power is turned on.
Is there some way to get the PC to boot automatically every time the power is turned on?

Any other ideas?

Thanks!

---

### Post by CatKiller on 2020-03-30
> **2CV67 said:**
> Any other ideas?


If it is a problem with the physical switch, wake-on-LAN will work fine.

---

### Post by TheFu on 2020-03-30
1 leave my systems on 24/7/365.
Laptops go  into standby overnight after the backup finishes. The next day, 1 have to search for the "any-key", but usually find  it. 1 use **reboot** to restart after patching, seldom use shutdown, unless the laptop is going somewhere in a vehicle.  That&#8217;s a security choice because it uses whole disk encryption.  Had a few computers stolen when on a trip in 2008.  Learned my lesson.

---

### Post by QIII on 2020-03-30
That pesky "any key".  I wear trifocals and I still have a heck on a time finding it.  Usually it seems like I do by accident.

---

### Post by 2CV67 on 2020-04-02
My symptoms seem to have disappeared (for how long?) so I have more time to explore.

Wake-on-Lan sounded interesting, thank you, but I didn't manage to see how it could work without an Ethernet cable.
I only have a Wifi network so would need something to work from a smartphone via wifi.
I found references to Wake-on-Wifi-Lan but could not find a simple-enough-for-me tutorial to try it.
In any case, I got the impression it would only wake the PC from sleep state, not from fully OFF, which is what I am looking for?

I also found references to Wake-on-Keyboard &/or Mouse.
I looked in my BIOS & found both these were present & already enabled, but again they don't work from fully OFF state.

I was hoping to be able to reproduce what happens after you turn the PC OFF by the ON/OFF switch.
Then the PC boots automatically next time the power is turned on.

(Of course I never do turn off the PC on the switch - only once to check that it did in fact do that).

---

### Post by 1clue on 2020-04-02
Did you try a power flush?

Hold the power button down for at least 30 seconds, no matter what happens on the screen. I count to 45 or more, because I want to be sure it's been 30 seconds.  It's best to start with your system off but plugged in.

Then release and then try to boot normally.

---

### Post by CatKiller on 2020-04-02
> **2CV67 said:**
> Wake-on-Lan sounded interesting, thank you, but I didn't manage to see how it could work without an Ethernet cable.
I only have a Wifi network so would need something to work from a smartphone via wifi.
I found references to Wake-on-Wifi-Lan but could not find a simple-enough-for-me tutorial to try it.
In any case, I got the impression it would only wake the PC from sleep state, not from fully OFF, which is what I am looking for?

It absolutely works when the computer is off. The way it works is that when the computer is off, the network device is still on and listening for a magic packet. The device that you're using to turn it on (I generally use my phone to do it) sends a magic packet to every device on the network that contains the MAC address of the machine that you're turning on. The ones that are listening check their MAC address against the one in the magic packet and, if it matches, turn themselves on.

The two step process is 1) making sure that the device will turn on when it receives the magic packet - this is a BIOS/UEFI configuration option - and 2) that the network device is left on when the machine is shut down, which is a software configuration option if it doesn't happen automatically after you've done step 1. Whether your hardware can do step 1 is dependent on the specifics of the hardware. All of my machines can do it, including my WiFi-only laptop.

---

