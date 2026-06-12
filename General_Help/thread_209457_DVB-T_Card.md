---
title: "DVB-T Card"
date: 2006-07-05
forum: General Help
---

### Post by JoshHendo on 2006-07-05
So, today I got a "DVB-T Mobility" (tv tuner) USB stick.

I tried it under Windows, and it seems to work fine. The only thing is I have no idea how to get it working in Ubuntu.

I isntalled TV Time and MythTV, but I can't seem to get any to work.

When I plug it in and type into the terminal dmesg, I get the following message:

```

[17190173.396000] dvb-usb: found a 'DiBcom USB2.0 DVB-T reference design (MOD3000P)' in cold state, will try to load a firmware
[17190173.416000] dvb-usb: did not find the firmware file. (dvb-usb-dibusb-6.0.0.8.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems.
[17190173.416000] dvb-usb: DiBcom USB2.0 DVB-T reference design (MOD3000P) error while loading driver (-2)
[17190173.416000] dvb_usb_dibusb_mc: probe of 5-2:1.0 failed with error -2

```

Is there a way that I would be able to set this up?

Thanks!

---

### Post by RAOF on 2006-07-05
Check out [linuxtv.org](linuxtv.org).  Although, given the error message, you might be able to just get it working in windows, then restart without unplugging it.  Maybe then it'll work in Linux ('cause Windows has already done the initial setup)

---

### Post by JoshHendo on 2006-07-05
I have managed to get the firmware working :). So now it is detected, the only problem is now that I can't get any program to work. TV time doesn't even start.

Any suggestiong on what I could do there?

Thanks!

---

### Post by JoshHendo on 2006-07-06
OK. I have TVTime running and the card detected.

This is teh output of when I run TVTime:
```

josh@c1:/etc/tvtime$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/josh/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory

```

This is the output I get when I connect the DVB-T USB drive to the computer (when running "dmesg"):
```

17217909.356000] usb 5-3: USB disconnect, address 9
[17217909.356000] dvb-usb: DiBcom USB2.0 DVB-T reference design (MOD3000P) successfully deinitialized and disconnected.
[17218442.576000] usb 5-3: new high speed USB device using ehci_hcd and address 10
[17218442.708000] dvb-usb: found a 'DiBcom USB2.0 DVB-T reference design (MOD3000P)' in cold state, will try to load a firmware
[17218443.320000] dvb-usb: downloading firmware from file 'dvb-usb-dibusb-6.0.0.8.fw' to the 'Cypress FX2'
[17218443.368000] dvb-usb: DiBcom USB2.0 DVB-T reference design (MOD3000P) successfully initialized and connected.
[17218443.596000] usb 5-3: USB disconnect, address 10
[17218443.596000] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[17218445.348000] usb 5-3: new high speed USB device using ehci_hcd and address 11
[17218445.488000] dvb-usb: found a 'DiBcom USB2.0 DVB-T reference design (MOD3000P)' in warm state.
[17218445.488000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[17218445.492000] DVB: registering new adapter (DiBcom USB2.0 DVB-T reference design (MOD3000P)).
[17218445.496000] dib3000: Found a DiBcom 3000P.
[17218445.496000] DVB: registering frontend 0 (DiBcom 3000P/M-C DVB-T)...
[17218445.496000] input: IR-receiver inside an USB DVB receiver as /class/input/input5
[17218445.496000] dvb-usb: schedule remote query interval to 150 msecs.
[17218445.496000] dvb-usb: DiBcom USB2.0 DVB-T reference design (MOD3000P) successfully initialized and connected.

```

Would there be any way that I could configure TV time to connect to the USB drive?

Thanks!

---

### Post by fdimmling on 2006-07-06
The easiest way to get DVB-T working is using kaffeine, even if you are a Gnome user as I am. When you plug in the DVB-T and after that start kaffeine you will see a DVB tab indicating that kaffeine has found a DVB device. You then select your area and make a frequency scan to identify the TV and radio stations. Kaffeine allows for recording, time-shifted tv watching and  - with lirc installed - it even can handle the remote control of my Terratec Cinergy T2. Great.

Friedrich

---

### Post by JoshHendo on 2006-07-06
OK. Thanks! I had read somewhere before I bought the stick that someone got it working well with Kaffeine, but I couldn't remember the program or find that thread again.

I will give it a try and post here how it goes :)

-Josh

---

### Post by JoshHendo on 2006-07-06
OK. Got Kaffeine up, and it detected the card. The only thing now is that it can't find any channels :/. Still, I will hopefully fix that soon :).

---

### Post by RAOF on 2006-07-07
> **JoshHendo said:**
> OK. Got Kaffeine up, and it detected the card. The only thing now is that it can't find any channels :/. Still, I will hopefully fix that soon :).

You'll probably need to manually search for those channels and create a channels.conf (or whatever it is called) using the tools from the dvb-tools stuff from linuxtv.org.  Check out the wiki, but from memory you need to first use "scan" (or something like that) passing the list of base stations from one of the files in the dvb-t subdirectory (corresponding to your location).

The "Budget DVB" section on the linuxtv.org wiki will explain it better, though :)

---

### Post by fdimmling on 2006-07-07
> **RAOF said:**
> You'll probably need to manually search for those channels and create a channels.conf (or whatever it is called) using the tools from the dvb-tools stuff from linuxtv.org.

Not with kaffeine. It does the job for you. You just have to select the area you live in. But my first Cinergy T2 was broken and also you have to take into account that signal strength inside of buildings or in some places may be too low. However you should be able to watch the scanning and see at least some transponders. You definitely do not need any other program besides kaffeine.

Friedrich

---

### Post by Frenchy on 2007-08-14
I've developed a small DVB-T application for GNOME called Me TV.  I've posted some information at [http://www.linuxtv.org/wiki/index.php/Me_TV](http://www.linuxtv.org/wiki/index.php/Me_TV) and made the Feisty installer available at [https://launchpad.net/me-tv/+download](https://launchpad.net/me-tv/+download).  Hope you like it.  If you've got the time please try it out and let me know what you think.

---

### Post by rsajnpr on 2008-03-12
Thanks Frenchy.
Works great with my no-name-usb-dvb-t-thing.

---

