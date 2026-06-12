---
title: "Both mouse buttons on touchpad work as primary button and cannot drag and drop."
date: 2018-02-21
forum: General Help
---

### Post by badbid on 2018-02-21
Migrated from Windows to linux that was my staple for years previously.
Since space was precarious, first choice was Lubuntu. Mouse problem encountered, couldn't be solved. Then tried other distros (altogether: linux light, lubuntu, ubuntu 17.10), before ending in Ubuntu 17.10. All distros had the same mouse issue. I couldn't try puppy, the download corrupted or something.

ISSUE:

1. Both physical buttons on my synaptics touchpad behave as a primary button. 
2. When I hold down left button, and try to select a text or drag an item with another finger, touchpad thinks it is double finger gesture: doesn't drag or select but scrolls through.
(the touchpad "touch area" extends above the buttons. So when i hold down the left physical button, the touchpad registers a touch over the button. so if I move the next finger up and down holding down the button, it scrolls thinking it's a two finger scroll.)
3. USB mouse works fine

Touch, gestures, two finger tap, two finger scroll works fine. Two finger zoom doesn't work, which is not a problem.

This is a Synaptics touchpad on HP stream 11, details here 


~$ cat /proc/bus/input/devices

I: Bus=0018 Vendor=06cb Product=7442 Version=0100
N: Name="Synaptics TM2976-002"
P: Phys=i2c-SYN1EDE:00
S: Sysfs=/devices/platform/80860F41:00/i2c-0/i2c-SYN1EDE:00/0018:06CB:7442.0001/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=1
B: EV=b
B: KEY=e520 30000 0 0 0 0
B: ABS=6f3800001000003

Edit: solved after borrowing bits and pieces from various threads:
1. Button issue solved by kernel update (comment 1)
2. natural scroll restored by adding "synclient VertScrollDelta=-92" to the autostart of lxsession default applications. (mine synclient -l shows its value as 92, I just changed it to negative
3. natural scroll horizontal also working opposite. added "synclient HorizScrollDelta=-92" to autostart
4. And need two finger horizontal two finger scroll. Added "synclient HorizTwoFingerScroll=1"
5. Using two finger scroll, don't need edge scroll. Add "synclient VertEdgeScroll=0" to autostart
6. Disable tapping or scrolling while typing. Add "syndaemon -i 1 -d -t -K" to autostart

I am writing also to remember these configs I reinstall OS next time :)

---

### Post by badbid on 2018-02-21
After trying many different solutions throughout the web, one post somewhere noted mouse behaviors could be kernel related. Updated kernel on Ubuntu 17.10 to 4.15.1 and the issues are gone. After so much of lost hours on this!
Hope someone else will be helped.
( I used the ukuu tool for kernel update)

Cheers on that coffee!

---

