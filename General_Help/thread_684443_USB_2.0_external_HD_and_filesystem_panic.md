---
title: "USB 2.0 external HD and filesystem panic"
date: 2008-02-01
forum: General Help
---

### Post by metalseb on 2008-02-01
Hello there,

I can see browsing the forum that I might not be alone with this kind of problem. I have a brand new USB 2.0 external HD and unable to write to it. dmesg gives me some "filesystem panic" and a lot of "reset usb device..." errors. 

I might say that the data are sent too fast from the computer since things are working like there was some kind of desynchro between the two devices. For exmample, let's backup a 700Mb ISO. Transfer initiates well at very fast speed then birate soon falls beyond the ground surface and Doplhin then hangs with a "stalled" message. Disk led blinks on a 1-second basis, way to say "dude, there something's going wrong here"

Doing a  rmmod ehci_hcd helps a bit since going down to USB 1.0 makes me able to tranfer data to the disk but the bitrate is way too slow.

I never encountered any problems with USB keys. I'm with Kubuntu 7.10.

Any idea to help ?

Kind regards.

---

### Post by polmir on 2008-02-01
Remove all thing connected to usb port.
After, connect your usb disk, 
type in terminal
```
dmesg>dmesg.txt
```
and post file dmesg.txt

---

