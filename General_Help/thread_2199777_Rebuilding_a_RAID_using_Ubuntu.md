---
title: "Rebuilding a RAID using Ubuntu?"
date: 2014-01-15
forum: General Help
---

### Post by MrMichaelHill on 2014-01-15
Hey guys!

On of the school sites I attended this week has had a Buffalo TeraStation (NAS Station) fail on them! The exact model is [B]*TS-XE4.0TL/R5*.

[/B]it has ***4x 1TB drives in RAID5***, Booting the station shows that an init file is missing from drive 1,2 & 3!

Now I used disky utility to check the SMART status of the drives, they are all fully readable & showing healthy.

When I connect drive 1 it gives me the option to go to array, **will this allow me to access the data? (providing I connect the other 3 drives of course) Data recovery is TOP priority! **

I have tried various things with the station itself but I have a feel the firmware is corrupt, I cannot access it via IP and the Buffalo firmware update software will find the station on the network but will not communicate with it :(

I've attached screenshots of Disk Utility with each drive, HD01 showing the go to array option!

Any help is greatly appreciated thanks! 

**_*HD01*_**
[https://dl.dropboxusercontent.com/u/2066107/sudleystation/HD01.png](https://dl.dropboxusercontent.com/u/2066107/sudleystation/HD01.png)
_***HD02***_
[https://dl.dropboxusercontent.com/u/2066107/sudleystation/HD02.png](https://dl.dropboxusercontent.com/u/2066107/sudleystation/HD02.png)
_***HD03***_
[https://dl.dropboxusercontent.com/u/2066107/sudleystation/HD03.png](https://dl.dropboxusercontent.com/u/2066107/sudleystation/HD03.png)
_***HD04***_
[https://dl.dropboxusercontent.com/u/2066107/sudleystation/HD04.png](https://dl.dropboxusercontent.com/u/2066107/sudleystation/HD04.png)

---

### Post by MrMichaelHill on 2014-01-17
Bump 

:(

---

### Post by smbventures on 2014-01-25
Hello Michael,

I have a similar question and look forward to a helpful response

I built my own NAS on a standard PC platform with three 2TB HDs and Ubuntu Server 12.04 with RAID5. The system works well so now for the RAID test. I shutdown and disconnect one of the HDs. The system will not boot upon restart. Obviously there's something I don't understand about RAID recovery. Do I need to boot using boot disc?

Many thanks.

---

