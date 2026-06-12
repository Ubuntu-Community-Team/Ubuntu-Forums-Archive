---
title: "USB Woes"
date: 2006-11-08
forum: General Help
---

### Post by Tri_X_Troll on 2006-11-08
I'm basically a linux newbie having usb problems. A while back, I messed with Red Hat 9, then I messed lightly with Ubuntu 6.06 when it first came out, and now I've been using 6.10 exclusivly since it came out.

Anyway, I've been using edgy for the past week or so and it's been running great. Nothing much more than word processing and web browsing. I came home tonight and plugged in my USB Pendrive and nothing happenens.

I rebooted to my windows install that I had almost forgotten about and my drive worked ok. SO I rebooted again, in Edgy this time, and once again, no flash drive. 

I did notice that the kern.log is giving me this:

Nov  8 23:28:55 ryan-desktop kernel: [17180972.820000] usb 4-6: new high speed USB device using ehci_hcd and address 30
Nov  8 23:29:16 ryan-desktop kernel: [17180993.780000] usb 4-6: device not accepting address 30, error -110

and help would be great, as I have not the slightest idea what to do next

---

### Post by unlokia on 2006-11-09
do a:

```
 sudo lsusb 
```

:) post results

---

### Post by secundar on 2006-11-25
I'm having the same problem it seems...
```

$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
``` 

```
$ lsmod | grep usb
usbhid                 42464  0 
usbcore               130304  4 usbhid,ehci_hcd,uhci_hcd
```

I've been searching the forums but there does not seem to be a difinitive solution.

```
$ uname -r
2.6.17-10-386
```

Been running edgy, dist upgraded from dapper, and this problem seems to have recently surfaced. Any help would be appreciated.

---

### Post by secundar on 2006-11-25
More searching the forums and no answers. This is a big problem for me as none of my usb devices work under linux now. Yuk!

Can anyone offer advice?

---

### Post by syadnom on 2006-11-25
did the usb devices work on dapper? and then not work on edgy?

what chipset is your motherboard?

does a 'tail dmesg' say anything unusual when you plug the flash drive in? and does it load a module for it?

---

### Post by secundar on 2006-11-25
no problems on dapper. everything worked and i'm now considering going back to dapper...

It's an Asus Z71V laptop with Intel 82801 Mobile PCI Bridge; 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB

here's the tail end of dmesg:
```

[17182962.280000] usb 1-1: reset low speed USB device using uhci_hcd and address 18
[17182962.600000] usb 1-1: device firmware changed
[17182962.600000] usb 1-1: USB disconnect, address 18
[17182962.716000] usb 1-1: new low speed USB device using uhci_hcd and address 19
[17182962.912000] usb 1-1: configuration #1 chosen from 1 choice
[17184378.968000] usb 1-1: USB disconnect, address 19
[17184380.904000] usb 3-2: new low speed USB device using uhci_hcd and address 7
[17184381.080000] usb 3-2: device descriptor read/64, error -71
[17184381.304000] usb 3-2: device descriptor read/64, error -71
[17184381.520000] usb 3-2: new low speed USB device using uhci_hcd and address 8
[17184381.644000] usb 3-2: device descriptor read/64, error -71
[17184381.872000] usb 3-2: device descriptor read/64, error -71
[17184382.088000] usb 3-2: new low speed USB device using uhci_hcd and address 9
[17184382.164000] usb 3-2: unable to read config index 0 descriptor/all
[17184382.164000] usb 3-2: can't read configurations, error -84
[17184382.276000] usb 3-2: new low speed USB device using uhci_hcd and address 10
[17184382.684000] usb 3-2: device not accepting address 10, error -71
[17184390.800000] usb 1-1: new low speed USB device using uhci_hcd and address 20
[17184390.944000] usb 1-1: device descriptor read/all, error -71
[17184391.060000] usb 1-1: new low speed USB device using uhci_hcd and address 21
[17184391.596000] usb 1-1: device not accepting address 21, error -71
[17184391.708000] usb 1-1: new low speed USB device using uhci_hcd and address 22
[17184392.116000] usb 1-1: device not accepting address 22, error -71
[17184392.228000] usb 1-1: new low speed USB device using uhci_hcd and address 23
[17184392.644000] usb 1-1: device not accepting address 23, error -71
[17184397.032000] usb 2-1: new low speed USB device using uhci_hcd and address 22
[17184397.288000] usb 2-1: configuration #1 chosen from 1 choice
[17184397.344000] input: HID 04d9:0499 as /class/input/input8
[17184397.344000] input: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1d.1-1

```

Earlier I had lost all usb activity. Now it's just unrelable. I can plug in the mouse into one of the five ports and eventually it will work.       Then, after some time it will stop working. Same with the CF card reader i was using. It would mount, but after a few minutes it would disappear and the desktop would scold me for removing it abruptly.

---

### Post by secundar on 2006-11-26
bump!

---

### Post by secundar on 2006-11-27
nevermind. i ended up reading a bit about another bug causing intermittent keyboard failure... [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315)

As soon as I killed gnome-power-manager and reinserted my mouse it came back to life... and stayed that way. Strange.

---

### Post by secundar on 2006-11-27
I spoke too soon! Seems that killing gnome-power-manager wasn't the solution afterall.

---

### Post by secundar on 2006-11-28
now I'm back to Dapper and mice still do not work...

```

[17180864.568000] usb 1-1: device descriptor read/64, error -71
[17180864.884000] usb 1-1: new low speed USB device using uhci_hcd and address 64

``` (last lines of dmesg)

---

### Post by secundar on 2006-11-29
does not work with a powered usb hub either. There for a moment, then gone...
```

[17179582.356000] usbcore: registered new driver usbfs
[17179582.356000] usbcore: registered new driver hub
[17230795.200000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17230796.316000] usb 2-1.2: new low speed USB device using uhci_hcd and address 3
[17230796.440000] usb 2-1.2: config 1 has an invalid interface number: 1 but max is 0
[17230796.440000] usb 2-1.2: config 1 has no interface number 0
[17230796.532000] usbcore: registered new driver hiddev
[17230796.552000] input: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.1-1.2
[17230796.552000] usbcore: registered new driver usbhid
[17230796.552000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17230859.956000] usb 2-1: USB disconnect, address 2
[17230859.956000] usb 2-1.2: USB disconnect, address 3
[17230887.932000] usb 1-1: new low speed USB device using uhci_hcd and address 2[17230888.580000] usb 1-1: device descriptor read/64, error -71
[17230889.160000] usb 1-1: device descriptor read/64, error -71
[17231731.228000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[17231731.352000] usb 3-2: device descriptor read/64, error -71
[17231731.580000] usb 3-2: device descriptor read/64, error -71
[17231732.464000] usb 3-2: new full speed USB device using uhci_hcd and address 3
[17231732.588000] usb 3-2: device descriptor read/64, error -71
[17231732.816000] usb 3-2: device descriptor read/64, error -71
[17231733.032000] usb 3-2: new full speed USB device using uhci_hcd and address 4
[17231733.448000] usb 3-2: device not accepting address 4, error -71
[17231733.564000] usb 3-2: new full speed USB device using uhci_hcd and address 5
[17231733.988000] usb 3-2: device not accepting address 5, error -71
[17231843.832000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[17231843.968000] usb 2-2: device descriptor read/64, error -71
[17231844.196000] usb 2-2: device descriptor read/64, error -71
[17231844.428000] usb 2-2: new full speed USB device using uhci_hcd and address 5
[17231844.736000] usb 2-2: device descriptor read/64, error -71
[17231845.404000] usb 2-2: device descriptor read/64, error -71
[17231845.936000] usb 2-2: new full speed USB device using uhci_hcd and address 6
[17231846.440000] usb 2-2: device not accepting address 6, error -71
[17231846.992000] usb 2-2: new full speed USB device using uhci_hcd and address 7
[17231847.528000] usb 2-2: device not accepting address 7, error -71
[17232289.396000] usb 2-2: new full speed USB device using uhci_hcd and address 8
[17232289.832000] usb 2-2: device descriptor read/64, error -71
[17232290.484000] usb 2-2: device descriptor read/64, error -71
[17232291.112000] usb 2-2: new full speed USB device using uhci_hcd and address 9
[17232291.264000] usb 2-2: device descriptor read/64, error -71
[17232291.568000] usb 2-2: device descriptor read/64, error -71
[17232292.180000] usb 2-2: new full speed USB device using uhci_hcd and address 10
[17232292.864000] usb 2-2: device not accepting address 10, error -71
[17232293.316000] usb 2-2: new full speed USB device using uhci_hcd and address 11
[17232294.024000] usb 2-2: device not accepting address 11, error -71
[17232611.348000] usb 2-2: new full speed USB device using uhci_hcd and address 12
[17232611.704000] usb 2-2: device descriptor read/64, error -71
[17232612.588000] usb 2-2: device descriptor read/64, error -71
[17232613.276000] usb 2-2: new full speed USB device using uhci_hcd and address 13
[17232613.856000] usb 2-2: device descriptor read/64, error -71
[17232614.760000] usb 2-2: device descriptor read/64, error -71
[17232615.248000] usb 2-2: new full speed USB device using uhci_hcd and address 14
[17232615.864000] usb 2-2: device not accepting address 14, error -71
[17232616.316000] usb 2-2: new full speed USB device using uhci_hcd and address 15
[17232616.996000] usb 2-2: device not accepting address 15, error -71
[17232773.104000] usb 2-2: new full speed USB device using uhci_hcd and address 16
[17232773.516000] usb 2-2: device descriptor read/64, error -71
[17232773.744000] usb 2-2: device descriptor read/64, error -71
[17232773.960000] usb 2-2: new full speed USB device using uhci_hcd and address 17
[17232774.084000] usb 2-2: device descriptor read/64, error -71
[17232774.312000] usb 2-2: device descriptor read/64, error -71
[17232774.620000] usb 2-2: new full speed USB device using uhci_hcd and address 18
[17232775.112000] usb 2-2: device not accepting address 18, error -71
[17232775.460000] usb 2-2: new full speed USB device using uhci_hcd and address 19
[17232776.048000] usb 2-2: device not accepting address 19, error -71
[17232783.332000] usb 2-2: new full speed USB device using uhci_hcd and address 20
[17232784.916000] usb 2-2: new full speed USB device using uhci_hcd and address 21
[17232785.136000] usb 2-2: device descriptor read/64, error -71
[17232785.536000] usb 2-2: device descriptor read/64, error -71
[17232785.956000] usb 2-2: new full speed USB device using uhci_hcd and address 22
[17232786.188000] usb 2-2: device descriptor read/64, error -71
[17232786.708000] usb 2-2: device descriptor read/64, error -71
[17232786.924000] usb 2-2: new full speed USB device using uhci_hcd and address 23
[17232787.340000] usb 2-2: device not accepting address 23, error -71
[17232787.452000] usb 2-2: new full speed USB device using uhci_hcd and address 24
[17232787.928000] usb 2-2: device not accepting address 24, error -71
[17232796.012000] usb 2-2: new full speed USB device using uhci_hcd and address 25
[17232801.168000] usb 2-2: new full speed USB device using uhci_hcd and address 26
[17232801.488000] usb 2-2: device descriptor read/64, error -71
[17232801.840000] usb 2-2: device descriptor read/64, error -71
[17232802.240000] usb 2-2: new full speed USB device using uhci_hcd and address 27
[17232802.396000] usb 2-2: device descriptor read/64, error -71
[17232803.076000] usb 2-2: device descriptor read/64, error -71
[17232803.448000] usb 2-2: new full speed USB device using uhci_hcd and address 28
[17232804.084000] usb 2-2: device not accepting address 28, error -71
[17232804.228000] usb 2-2: new full speed USB device using uhci_hcd and address 29
[17232804.760000] usb 2-2: device not accepting address 29, error -71
[17232812.588000] usb 2-2: new full speed USB device using uhci_hcd and address 30
[17232813.852000] usb 2-2: device not accepting address 30, error -71
[17232818.548000] usb 2-2: new full speed USB device using uhci_hcd and address 32
[17232818.792000] usb 2-2: device descriptor read/64, error -71
[17232819.200000] usb 2-2: device descriptor read/64, error -71
[17232819.580000] usb 2-2: new full speed USB device using uhci_hcd and address 33
[17232819.892000] usb 2-2: device descriptor read/64, error -71
[17232820.460000] usb 2-2: device descriptor read/64, error -71
[17232821.096000] usb 2-2: new full speed USB device using uhci_hcd and address 34
[17232821.588000] usb 2-2: device not accepting address 34, error -71
[17232821.792000] usb 2-2: new full speed USB device using uhci_hcd and address 35
[17232822.548000] usb 2-2: device not accepting address 35, error -71
[17232967.880000] usb 2-2: new full speed USB device using uhci_hcd and address 36
[17232968.368000] usb 2-2: device descriptor read/64, error -71
[17232968.972000] usb 2-2: device descriptor read/64, error -71
[17232973.948000] usb 2-2: new full speed USB device using uhci_hcd and address 38
[17232974.316000] usb 2-2: device descriptor read/64, error -71
[17232975.096000] usb 2-2: device descriptor read/64, error -71
[17232976.012000] usb 2-2: new full speed USB device using uhci_hcd and address 39
[17232976.508000] usb 2-2: device descriptor read/64, error -71
[17232977.128000] usb 2-2: device descriptor read/64, error -71
[17232977.888000] usb 2-2: new full speed USB device using uhci_hcd and address 40
[17232978.520000] usb 2-2: device not accepting address 40, error -71
[17232978.968000] usb 2-2: new full speed USB device using uhci_hcd and address 41
[17232979.748000] usb 2-2: device not accepting address 41, error -71
[17232981.292000] usb 2-2: new full speed USB device using uhci_hcd and address 42
[17232981.628000] usb 2-2: device descriptor read/64, error -71
[17232982.236000] usb 2-2: device descriptor read/64, error -71
[17232983.184000] usb 2-2: new full speed USB device using uhci_hcd and address 43
[17232983.560000] usb 2-2: device descriptor read/64, error -84
[17232984.200000] usb 2-2: device descriptor read/64, error -71
[17232984.828000] usb 2-2: new full speed USB device using uhci_hcd and address 44
[17232985.364000] usb 2-2: device not accepting address 44, error -71
[17232985.708000] usb 2-2: new full speed USB device using uhci_hcd and address 45
[17232986.352000] usb 2-2: device not accepting address 45, error -71
[17233259.848000] usb 2-1: new full speed USB device using uhci_hcd and address 46
[17233260.520000] usb 2-1: device descriptor read/64, error -71
[17233261.360000] usb 2-1: device descriptor read/64, error -71
[17233261.976000] usb 2-1: new full speed USB device using uhci_hcd and address 47
[17233262.388000] usb 2-1: device descriptor read/64, error -71
[17233262.968000] usb 2-1: device descriptor read/64, error -71
[17233263.632000] usb 2-1: new full speed USB device using uhci_hcd and address 48
[17233264.240000] usb 2-1: device not accepting address 48, error -71
[17233264.524000] usb 2-1: new full speed USB device using uhci_hcd and address 49
[17233265.236000] usb 2-1: device not accepting address 49, error -71

```

This is a fresh Dapper install from CD with my old home folder from Edgy. To test it wasn't my user folder I created a new account. Same problems.

Current kernal used: Linux debianpad 2.6.15-26-686 #1 SMP PREEMPT Fri Sep 8 20:16:40 UTC 2006 i686 GNU/Linux

Last night I went thru a bunch of other kernels, restarting, plugging the mouse back in, etc. Same issues. Mouse laser will light up momentarily then die. USB storage works though.

---

### Post by secundar on 2006-11-29
Went thru all the Dapper kernels to no avail. Ended up buying a USB PCCard and now i can use a mouse again.

In short, I think the on-board USB is failing. Too many rides on a motorcycle i suppose.

---

### Post by bodymind on 2006-12-08
i have same problem too, the problem is that your mice needs usb2.0 compatible driver, that is "echi_hcd" kernel module.. but somehow there is a conflict with ehci_hcd and ehcu_hcd modules. 
if you do: rmmod ehcu_hcd
and then connect your mice it will work, but all your devices that needs usb1.1 support won't work anymore.. :s i think it's a hotplug problem... i'm googling... 8-)

---

