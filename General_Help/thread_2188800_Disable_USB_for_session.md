---
title: "Disable USB for session"
date: 2013-11-19
forum: General Help
---

### Post by MikeCyber on 2013-11-19
Hi
I want to disable my two CH devices:

michael@michael-Ubuntu:~$ sudo lsusb 
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 003: ID 174c:2074 ASMedia Technology Inc. 
Bus 003 Device 004: ID 0b05:17d0 ASUSTek Computer, Inc. 
Bus 003 Device 005: ID 068e:00ff CH Products, Inc. Flight Sim Yoke
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. 
Bus 003 Device 006: ID 068e:00f2 CH Products, Inc. Flight Sim Pedals
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
michael@michael-Ubuntu:~$ 


as it interferes with Metro Last Light. Switch them back on after playing.
Thanks

---

### Post by stinkeye on 2013-11-19
Try this.
It will disable my usb keyboard. May work for your devices.

Get your usb id.....
```
xinput
```

Then use...
```
xinput --disable [COLOR="#FF0000"]x[/COLOR]
```
...where [COLOR="#FF0000"]x[/COLOR] is your usb id.

To enable....
```
xinput --enable [COLOR="#FF0000"]x[/COLOR]
```

---

### Post by stinkeye on 2013-11-20
Been playing around with this and came up with a toggle on/off script.
The script will toggle my "Nostromo SpeedPad2" gaming keyboard on/off.
Could adapt it for your device.

eg this is my xinput...
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **xinput --list**
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; DEXIN Tt eSPORTS BLACK Gaming mouse     	id=11	[slave  pointer  (2)]
&#9116;   &#8627; DEXIN Tt eSPORTS BLACK Gaming mouse     	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Honey Bee  Nostromo SpeedPad2           	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Logitech Logitech USB Headset           	id=10	[slave  keyboard (3)]
    &#8627; Ideazon Zboard                          	id=14	[slave  keyboard (3)]
    &#8627; Ideazon Zboard                          	id=13	[slave  keyboard (3)]
    [COLOR="#FF0000"]&#8627; Honey Bee  Nostromo SpeedPad2           	id=8	[slave  keyboard (3)][/COLOR]
```

....and from that output derived this toggle script...
```
#!/bin/bash

# Script to toggle a usb device on/off
# This works to disable my Nostromo SpeedPad2 that I only use for gaming.
# Need to adapt deviceid variable to use your device from the output of "xinput --list"

deviceid=$(xinput --list | awk '/Virtual core keyboard/{y=1;next}y' | grep -m1 "Nostromo" | awk '{print $6}' | tr -d 'id=')
devicestate=$(xinput --list-props $deviceid | awk '/Device Enabled/ {print $4}') # 0=disabled 1=enabled
devicename=$(xinput --list --name-only $deviceid)

if [ $devicestate = 0 ]; then
	xinput --enable $deviceid
	notify-send -i keyboard "Enabled" "$devicename"
else
	xinput --disable $deviceid
	notify-send -i keyboard "Disabled" "$devicename"
fi
```

If you need help to make the script work for your device
post the results from...
```
xinput --list
```

---

### Post by MikeCyber on 2013-11-21
michael@michael-Ubuntu:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=8    [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                          id=10    [slave  keyboard (3)]
michael@michael-Ubuntu:~$ 


Hmm I don't see my 2 CH devices here. Thanks

---

### Post by stinkeye on 2013-11-21
> **MikeCyber said:**
> michael@michael-Ubuntu:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=8    [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                          id=10    [slave  keyboard (3)]
michael@michael-Ubuntu:~$ 


Hmm I don't see my 2 CH devices here. Thanks
Oh well, I thought they would show in xinput,
and the script works so nicely with my gaming pad. :cry:

---

