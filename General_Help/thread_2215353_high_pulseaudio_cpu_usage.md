---
title: "high pulseaudio cpu usage"
date: 2014-04-06
forum: General Help
---

### Post by frohfroh on 2014-04-06
After updating to 13.10, pulseaudio started using lots of cpu(15% - 40%), even when no sound is being played at all. If I try to play any sound it works fine.
If I kill pulseaudio however, it will respawn , work nicely and with 0.0% of cpu when no sound played. 
Any idea what the problem could be?

---

### Post by tgalati4 on 2014-04-06
Check the log files in /var/log and see if *pulseaudio* is dumping error messages.  How did you update to 13.10?  Did  you perform an in-place update or a fresh installation of 13.10?

---

### Post by frohfroh on 2014-04-06
Thanks for answering.
It was a in-place update.
I could find in /home/ferraro/grepador/syslog:
Apr  6 10:32:26 *-HP-Pavilion-dv6-Notebook-PC pulseaudio[3387]: [pulseaudio] pid.c: Daemon already running.

and in /home/ferraro/grepador/udev

UDEV  [16.724724] change   /devices/pci0000:00/0000:00:1b.0/sound/card0 (sound)
ACTION=change
DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0
ID_BUS=pci
ID_FOR_SEAT=sound-pci-0000_00_1b_0
ID_MODEL_FROM_DATABASE=6 Series/C200 Series Chipset Family High Definition Audio Controller
ID_MODEL_ID=0x1c20
ID_PATH=pci-0000:00:1b.0
ID_PATH_TAG=pci-0000_00_1b_0
ID_PCI_CLASS_FROM_DATABASE=Multimedia controller
ID_PCI_SUBCLASS_FROM_DATABASE=Audio device
ID_VENDOR_FROM_DATABASE=Intel Corporation
ID_VENDOR_ID=0x8086
PULSE_PROFILE_SET=extra-hdmi.conf
SEQNUM=2118
SOUND_FORM_FACTOR=internal
SOUND_INITIALIZED=1
SUBSYSTEM=sound
TAGS=:seat:
USEC_INITIALIZED=6877

---

### Post by neil11 on 2014-05-12
I'm getting the same thing:
```

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                   
 2753 neilm      9 -11  443436   9880   7264 S   6.6  0.3   1:40.29 pulseaudio                                                                                

```

It averages between 4-7% cpu - whilst no music or sounds are being played or recorded, ie when I'm doing nothing.

Not sure it's a problem but it does seem high for process that should be idle.

Kubuntu 14.4 (LTS - upgraded from 12.4 LTS )
Dell laptop.

I've looked in /var/log/ and I see message from pulseaudio but only at startup:
I looks like pulseaudio is running system mode by default! - I'll try and disable that and see if it helps.

---

### Post by neil11 on 2014-05-12
Stopping it running in System mode solved the problem - a bit of manual editing the /etc/init.d/pulseaudio script to use the correct settings file.

---

### Post by pete24 on 2014-07-02
> **neil11 said:**
> Stopping it running in System mode solved the problem - a bit of manual editing the /etc/init.d/pulseaudio script to use the correct settings file.

Hi,

Could you please let us know exactly what changes you made to /etc/init.d/pulseaudio?

I'm experiencing this issue too - pulseaudio using 7% - 12% of CPU but apparently not doing anything. I'm currently getting around it by killing the pulseaudio process after restart. :-(

Cheers

Pete

---

### Post by frohfroh on 2014-07-05
Can anyone confirm if upgrading to 14.04 solves the issue?
I am currently not planning to upgrade, as each upgrade seems to add 2-3 annoying bugs, but if it fixes this, it might be worth it.

---

### Post by scottstensland on 2014-12-14
I see this same behaviour on 14.10

---

