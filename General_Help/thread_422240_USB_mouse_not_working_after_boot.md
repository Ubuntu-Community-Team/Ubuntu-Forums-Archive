---
title: "USB mouse not working after boot"
date: 2007-04-25
forum: General Help
---

### Post by 303 on 2007-04-25
Using Edgy -
When I boot up my PC and up to the login, the mouse pointer stays put until I unplug it then plug it back in
It's a Creative HD Laser Mouse... it has power to it, just not working until the re-plug-in

Also,
If there is no option to turn off USB after poweroff in the BIOS (only enable/disable USB) in BIOS, is there a way to turn off the mouse besides unplugging the machine or the mouse? 

here is the output of
dmesg | grep usb

[   11.932000] usbcore: registered new interface driver usbfs
[   11.932000] usbcore: registered new interface driver hub
[   11.932000] usbcore: registered new device driver usb
[   11.940000] usb usb1: configuration #1 chosen from 1 choice
[   12.284000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   12.444000] usb 1-1: configuration #1 chosen from 1 choice
[   31.328000] usbcore: registered new interface driver hiddev
[   31.420000] input: USB HID v1.10 Mouse [Creative Technology Ltd. Creative Mouse Gamer HD7600L] on usb-0000:00:1f.2-1
[   31.420000] usbcore: registered new interface driver usbhid
[   31.420000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   78.228000] usb 1-1: USB disconnect, address 2
[   83.140000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   83.300000] usb 1-1: configuration #1 chosen from 1 choice
[   83.308000] input: USB HID v1.10 Mouse [Creative Technology Ltd. Creative Mouse Gamer HD7600L] on usb-0000:00:1f.2-1
[   85.684000] drivers/usb/input/hid-core.c: event field not found
[   85.684000] drivers/usb/input/hid-core.c: event field not found
[   85.684000] drivers/usb/input/hid-core.c: event field not found
[ 1568.948000] drivers/usb/input/hid-core.c: event field not found
[ 2903.332000] drivers/usb/input/hid-core.c: event field not found


*Edit: I found this script and added it to /sbin/hotplug ... worked once but now same problem, again...

#!/bin/sh
if [ "$1" = "usb" ]; then
    if [ "$INTERFACE" = "3/1/2" ]; then
        if [ "$ACTION" = "add" ]; then
            modprobe usbmouse
        else
            rmmod usbmouse
        fi
    fi
fi



*Edit: here is lsmod output:

Module                  Size  Used by
binfmt_misc            11208  1 
capability              4840  0 
commoncap               7200  1 capability
video                  15396  0 
dock                    9112  0 
container               4288  0 
ac                      5028  0 
button                  7664  0 
af_packet              20648  2 
parport_pc             34628  0 
lp                     11524  0 
parport                35144  2 parport_pc,lp
tsdev                   7744  0 
3c59x                  44328  0 
mii                     5568  1 3c59x
psmouse                37800  0 
usbhid                 24352  0 
serio_raw               6692  0 
evdev                  10048  1 
intel_agp              23836  1 
agpgart                32080  2 intel_agp
snd_intel8x0           32604  1 
snd_ac97_codec         93856  1 snd_intel8x0
ac97_bus                2208  1 snd_ac97_codec
snd_pcm_oss            43200  0 
snd_mixer_oss          16576  1 snd_pcm_oss
snd_pcm                75560  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21476  1 snd_pcm
rng_core                5028  0 
snd                    50916  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               7456  1 snd
snd_page_alloc          9928  2 snd_intel8x0,snd_pcm
i2c_i810                5060  0 
i2c_algo_bit            7752  1 i2c_i810
shpchp                 33492  0 
pci_hotplug            31480  1 shpchp
pcspkr                  2688  0 
i2c_core               21840  2 i2c_i810,i2c_algo_bit
ext3                  130440  1 
jbd                    53320  1 ext3
mbcache                 8196  1 ext3
uhci_hcd               23340  0 
usbcore               130296  3 usbhid,uhci_hcd
ide_generic             1216  0 [permanent]
ide_cd                 39360  1 
cdrom                  36704  1 ide_cd
ide_disk               16000  3 
piix                    9956  0 [permanent]
generic                 4772  0 [permanent]
thermal                13640  0 
processor              16604  1 thermal
fan                     4612  0

---

### Post by 303 on 2007-04-29
...anyone?? (I can't afford $250 for personal desktop support...)

here is cat /proc/bus/input/devices:

I: Bus=0003 Vendor=041e Product=1053 Version=0110
N: Name="Creative Technology Ltd. Creative Mouse Gamer HD7600L"
P: Phys=usb-0000:00:1f.2-1/input0
S: Sysfs=/class/input/input5
H: Handlers=mouse0 event2 ts0 
B: EV=20007
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: LED=ff00

I've been searching on how to get this working all over -  irc, google, nothing yet
please help

lastly, here is from dmesg

[   68.136000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   68.296000] usb 1-1: configuration #1 chosen from 1 choice
[   68.304000] input: Creative Technology Ltd. Creative Mouse Gamer HD7600L as /class/input/input5
[   68.304000] input: USB HID v1.10 Mouse [Creative Technology Ltd. Creative Mouse Gamer HD7600L] on usb-0000:00:1f.2-1
[   70.544000] drivers/usb/input/hid-core.c: event field not found
[   70.544000] drivers/usb/input/hid-core.c: event field not found
[   70.544000] drivers/usb/input/hid-core.c: event field not found

anyone??

---

