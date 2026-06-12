---
title: "Ubuntu 22.04. External nvme drive gives “No Media” message."
date: 2022-11-16
forum: General Help
---

### Post by Advait on 2022-11-16
[COLOR=#000000][FONT=Arial]Noob here. AMD MSI Bravo laptop. Not dual boot. See attached image. For the past year I&#8217;ve been using this USB C connected 2TB external nvme drive for my regular Clonezilla system drive clone backup. A few days ago it stopped working and now Disks just displays &#8220;No Media&#8221;. See attached image.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The external nvme drive is not appearing when I run fdisk -l. My two internal nvme drives successfully appear when I run fdisk -l.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Also it does not appear after I Refresh Devices in gparted.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have 2 USB C ports on my laptop and I get the same No Media message on both ports.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Also it does not appear in my Windows 10 VM running in Virtualbox.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]What's the best way to diagnose this drive? I prefer a GUI tool to diagnose but will use terminal commands if needed.
Any way I can reformat the drive?

[IMG]https://imgur.com/ZFSzJoH.png[/IMG]
[/FONT][/COLOR]

---

### Post by MAFoElffen on 2022-11-16
Since it is an external NVMe drive, I'm guessing it is a drive in an enclosure connected to your laptop with a USBC to USBC cable... Like one of mine. (I have 3.)

I would try reseating the drive first. Then if that does not work, then try a different cable. If that doesn't work, then see if it comes up in gparted.

If the drive does not show at least basic information it is not going to be able to be partitioned nor formatted.

---

### Post by Advait on 2022-11-17
*#mafoelffen wrote:*
*Since it is an external NVMe drive, I'm guessing it is a drive in an  enclosure connected to your laptop with a USBC to USBC cable.*

**Yep, mine is connected with USB C

* I would try reseating the drive first. Then if that does not work, then  try a different cable. If that doesn't work, then see if it comes up in  gparted.*

  **Tried all those, didn't work. It shows up in gparted as "unallocated". When I tried to add a partition table, gparted threw up all kinds of errors and became unresponsive.

* If the drive does not show at least basic information it is not going to be able to be partitioned nor formatted.*

  **Yep, I think the drive is dead. Unless you have any other ideas, I'll trash it. Maybe when the new SpinRite comes out, I'll see if that can see the drive and do something.

---

