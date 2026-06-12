---
title: "/dev/pilot"
date: 2007-04-21
forum: General Help
---

### Post by gila_monster on 2007-04-21
Greetings, all.

I upgraded to kubuntu feisty the other day, and thought I would give kpilot a try. (I had tried it under dapper with limited success, and heard that several problems had been fixed in feisty.) But I have a problem now with the system recognizing the handheld, which is a Palm T|X. It appears that /dev/pilot is never mounted, even if I push the hotsync button on the cradle.

IIRC, /dev/pilot was mounted under both dapper and edgy when I pressed the cradle button. (In fact, it's the only way I could get jpilot to work when I tried that as well.) Now, the device is apparently not recognized or mounted.

It appears I have an entry for it in /etc/udev/rules.d/60-symlinks.rules:

# Create /dev/pilot symlink for Palm Pilots
KERNEL=="ttyUSB*", ATTRS{product}=="Palm Handheld*|Handspring *|palmOne Handheld", \
                                        SYMLINK+="pilot"

What am I missing here? I would think that this would work. The last update to this file was 2007-04-10. I'm not sure what happened on that date -- I did not update the file manually.

Thanks.

---

### Post by gila_monster on 2007-04-21
Okay, after doing a little research, I changed my symlink rules to the following:

BUS=="usb", SYSFS{product}=="Palm Handheld*|Handspring *|palmOne Handheld", \
   KERNEL=="ttyUSB*", NAME="ttyUSB%n", SYMLINK+="pilot", GROUP="usb", MODE="0666"


This sets the /dev/pilot symlink to ttyUSB* nicely. Unfortunately, kpilot does not seem to be able to open the device. So, partial success.

Any help appreciated.

---

### Post by poekie on 2007-04-21
I have the same problem with a Palm Zire 21. It worked fine under Dapper, don't know about Edgy, I upgraded to edgy and then feisty on the same day. 
The palm used to be recognised by the autodetect settings thing in KPilot, but it doesn't anymore. /dev/pilot doesn't work either. So any clues how to fix it would be great :D
lshw recognises the palm correctly:
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: ioport:c400-c41f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: Palm Handheld
                   vendor: Palm, Inc.
                   physical id: 1
                   bus info: usb@3:1
                   version: 1.00
                   serial: PalmSN12345678
                   capabilities: usb-1.00
                   configuration: maxpower=2mA speed=12.0MB/s

---

### Post by defishguy on 2007-04-21
I had an issue with my Palm TX and the Feisty upgrade.  Turned out that the visor module wasn't loading. 

Try this:

> sudo modprobe visor

Then try setting up gpilot and trying a sync.  If it works then you have to add the visor module to the start up.  To do this :

> sudo gedit /etc/modules

Add the word **visor** to the list, save and then close.  This will load the visor module at the next startup.

I will say this, that Feisty is the only distribution that I've worked with that consistently and flawlessly syncs my TX.  KUDOS to the devs for a very high (minus the visor module thing) quality distro.


Good luck!

---

### Post by poekie on 2007-04-21
Thanks! That actually worked! I had nightmarish thoughts of staying up all night (it's 1am here) figuring out what to do and you saved me! :KS

---

### Post by seanf on 2007-04-22
Thanks - adding 'visor' to modules brought my sync back to life :)

---

### Post by hanzj on 2007-04-22
defishguy,
Thanks, that worked for me, too, even if I don't user a Visor model pda!

---

### Post by gjtoth on 2007-04-24
Just my luck... didn't work for me. :(

---

### Post by djcrash1981 on 2007-04-25
Ok, this is great, i was worry because i just did the upgrade from edgy to festy and my palm didn't worked, but i found this wonderful thread and now everything works perfect.

Tanks :guitar: :popcorn:

---

### Post by gila_monster on 2007-04-25
Well, I had partial success. I got it to where it would try to sync. Unfortunately.....

...despite the fact I had set it to "handheld overwrites PC," it tried to do a two-way sync.

...it didn't do it properly, moving some events in my datebook to the wrong day (mainly repeating events).

...kpilot crashed halfway through (which might explain the previous).


So it looks like I'm stuck with jpilot, even though I think I prefer the kdepim suite.

Thanks for all the advice, guys. It did help. Just not as well as I'd hoped.

---

### Post by Chryana on 2007-04-28
Works for me too. Kinda. My palm crashes halfway through though, and I have to reset it :(.

---

### Post by GolfHacker on 2007-05-02
I edited /etc/modules and added "visor", as mentioned previously, but kpilot still doesn't work for me.

When I run through the kpilot configuration wizard and try to auto-detect, I get the hotsync sound from my palm tungsten 2, but kpilot doesn't seem to notice. If I skip the autodetect and hardcode the parameters to my user name and /dev/pilot, the hotsync doesn't work at all.

This worked fine on Kubuntu Edgy.

Any ideas? :(

---

### Post by Bollinja on 2007-06-01
Thanks Defishguy, adding visor to the start-up modules sorted my problem with my Palm & Kpilot :)

---

### Post by Rebes on 2007-06-23
modprobe visor worked for me... ttyUSB* started showing up, and the link to /dev/pilot was created.  Sync worked in kpilot.

I then switched the setting in kpilot to net:any, and net sync is working perfectly on my Palm TX!

Thanks much, this is one of the two problems I had when switching over from gnome to kde, and it is now solved.

D!

---

### Post by printarg on 2007-07-26
Here's what lshw reports on my computer:

       *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff60-ff7f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: Palm Handheld
                   vendor: Palm, Inc.
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.00
                   serial: PalmSN12345678
                   capabilities: usb-1.10
                   configuration: driver=visor maxpower=500mA speed=12.0MB/s

However, I cannot sync the Palm device with j-pilot. What could be wrong?

---

### Post by bengar on 2007-08-26
> **defishguy said:**
> I had an issue with my Palm TX and the Feisty upgrade.  Turned out that the visor module wasn't loading. 

Try this:



Then try setting up gpilot and trying a sync.  If it works then you have to add the visor module to the start up.  To do this :



Add the word **visor** to the list, save and then close.  This will load the visor module at the next startup.

I will say this, that Feisty is the only distribution that I've worked with that consistently and flawlessly syncs my TX.  KUDOS to the devs for a very high (minus the visor module thing) quality distro.


Good luck!


Many thanks I tried > sudo modprobe visor on Gutsy and now is working without any problem, I will tried the same later with Feisty.
73
b

---

### Post by keithrennie on 2008-02-10
Thanks, defishguy.  Had spent a few frustrating days trying more complicated things to make my faithful old palm T3 sync on gutsy using kpilot.  All I needed to do to make it work was load the visor module per your advice and make it load every time.  Once I did that, turned out that everything else I had done (j-pilot, gnome-pilot, udev rules editing, device configuration, symlinks etc) turned out to be redundant because automatic. :)

---

