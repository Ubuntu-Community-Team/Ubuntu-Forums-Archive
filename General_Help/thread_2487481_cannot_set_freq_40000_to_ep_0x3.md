---
title: "cannot set freq 40000 to ep 0x3"
date: 2023-06-06
forum: General Help
---

### Post by klundermann on 2023-06-06
After upgrading an ancient Dell Latitude E6220 from 21.10 to 22.04.02, the following error message appears during boot-up:```

[    5.258942] usb 2-1.3: 1:1: cannot set freq 48000 to ep 0x3
```

 and audio does not work.

The only possibly relevant thread I've found in the forums is [this one](https://ubuntuforums.org/showthread.php?t=2476376&highlight=set+freq+48000), but it's above my technical level and it does not include a solution.

Any ideas?

---

### Post by #&amp;thj^% on 2023-06-06
This will help us to help you, Will you please run our system-info script, **and then post back the URL it will show at the end.**
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details
```
Say yes to upload to pasrebin.

---

### Post by MAFoElffen on 2023-06-06
If you run that script as 
```

./system-info --details

```
...it will display more sound details in the report. LOL. Funny thing is, that is one of the things that 1fallen suggested that I add to that 'details mode' section.

---

### Post by #&amp;thj^% on 2023-06-06
> **MAFoElffen said:**
> If you run that script as 
```

./system-info --details

```
...it will display more sound details in the report. LOL. Funny thing is, that is one of the things that 1fallen suggested that I add to that 'details mode' section.
Guilty as Charged...:o
I'm going to edit my first post here to reflect that absent "--details"

---

### Post by klundermann on 2023-06-07
Thank you kindly, 1fallen and MAFoElffen.  Ive uploaded the output of  ./system-info --details  to [https://paste.ubuntu.com/p/kQWd93TvV5/](https://paste.ubuntu.com/p/kQWd93TvV5/) .

By the way, the error message that I am reporting here, "... cannot set freq 48000 ..." appears so briefly that to read it, I used my phone to video the boot sequence and then froze the video when the message appeared.  Is there an error log somewhere where the message is recorded?

---

### Post by #&amp;thj^% on 2023-06-07
Nothing is jumping out at me with report, I see it is a upgrade, just as you reported.
Will you now try to boot to the older kernel "5.15.0.25.27" and test sound again?
As for messages give this a look
```
sudo dmesg | grep snd_

```

---

### Post by MAFoElffen on 2023-06-07
Well... I see a few things "not" there. (That is even more curious.)

The default sound device is:
```

default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=PCH
    HDA Intel PCH, 92HD90BXX Analog
    Default Audio Device
card 0: PCH [HDA Intel PCH], device 0: 92HD90BXX Analog [92HD90BXX Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
But your error message is"
```

[    5.258942] [COLOR=#ff0000]usb 2-1.3: 1:1: cannot set freq 48000 to ep 0x3[/COLOR]

```
I don't see USB sound devices in the Sound Devices Section... 

If I go to the USB Section of the report:
```

---------- USB Information from 'lsusb -t -v':
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    /sys/bus/usb/devices/usb2  /dev/bus/usb/002/001
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
        ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
        /sys/bus/usb/devices/2-1  /dev/bus/usb/002/002
        |__ Port 8: Dev 3, If 0, Class=Application Specific Interface, Driver=, 12M
            ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
            /sys/bus/usb/devices/2-1.8  /dev/bus/usb/002/003
        |__ Port 8: Dev 3, If 1, Class=Chip/SmartCard, Driver=, 12M
            ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
            /sys/bus/usb/devices/2-1.8  /dev/bus/usb/002/003
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    /sys/bus/usb/devices/usb1  /dev/bus/usb/001/001
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
        /sys/bus/usb/devices/1-1  /dev/bus/usb/001/002

```
I don't see anything recognized at port 2-1.3: 1: 1, let alone a sound device(???)

Maybe we should look at this, to see what the system found on USB Bus 02, Port 1:
```

sudo dmesg | grep -i 'usb' | grep '2-1:'

```

---

