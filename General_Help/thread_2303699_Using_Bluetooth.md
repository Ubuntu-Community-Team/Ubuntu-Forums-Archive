---
title: "Using Bluetooth"
date: 2015-11-20
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2015-11-20
I am using Xubuntu 14.04 w/ Linux 4.3.0-040300-generic
My laptop has a bluetooth chip on its wifi card (laptop did not ship with this chip)
[Intel Corporation Centrino Wireless-N 2230](http://ark.intel.com/products/66889/Intel-Centrino-Wireless-N-2230-Single-Band)
i have only tried to use bluetooth twice, once with a radio at work, it synced but i could not figure out how to get audio to play over it
Today i was given a PS3 controller, i hooked it upto my desktop w/ Linux 3.18 via USB and it works as expected, even detects the battery (given i have to press the logo key to get it to operate)
based on what i googled this controller has bluetooth (as a 2ft charging cable is not very useful)
i tried to search for the controller via bluetooth while the controller was doing it blinky thing, it never found it
```
Bus 004 Device 003: ID 054c:0268 Sony Corp. Batoh Device / PlayStation 3 Controller
```

is there some trick to using bluetooth? this is my 1st time having any bluetooth hardware aide from my wifi card

---

### Post by sandyd on 2015-11-20
Seems that 14.04's BlueZ version (4.101-0ubuntu13), is not new enough to pair the DualShock 3. You require BlueZ 5.12 or newer to pair with the DualShock 3.

You will have to use Sixad to use the DualShock 3

Install Sixad
```

sudo apt-get install sixad
```

Start Sixad
```

sixad --start

```

Now, you have to create the configuration - the guide is at [http://qtsixa.sourceforge.net/manual.pdf](http://qtsixa.sourceforge.net/manual.pdf)

To stop Sixad, run
```

sixad --stop
```

And then, bring back your default bluetooth...
```

sixad --restore
```

---

### Post by pqwoerituytrueiwoq on 2015-11-21
thanks
connected via usb 
[FONT=courier new]sudo sixpair[/FONT]
disconnected
[FONT=courier new]sixad -s[/FONT]
opened new terminal
ran 
[FONT=courier new]retroarch-joyconfig[/FONT]
saw random analog inputs popup
seems the controller has a gyro sensor (i don't need this)
[FONT=Courier New]echo enable_accel 0 | sudo tee -a /var/lib/sixad/profiles/default[/FONT]
disabled sensor
*sensor does not work over usb (don't know or care why)

---

