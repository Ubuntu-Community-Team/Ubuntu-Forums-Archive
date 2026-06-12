---
title: "[SOLVED] Icky Partition Issues"
date: 2007-07-17
forum: General Help
---

### Post by hailtothethief on 2007-07-17
I currently have three partitions on my hard drive, outlined as follows

[FONT="Courier New"]
+----------------+-------+------+
| NTFS / Windows | Linux | Swap |
+----------------+-------+------+
[/FONT]

I need to expand my Linux (ext3, of course) partition at the cost of downsizing my NTFS part. I can't afford to format either because I would lose all of my data, except that I could theoretically back up my linux files (about 7 gigs) on my other machine, in which case I need to know how to set up a serial connection to my other, windows based machine.

When I try in gparted I am able to reduce the NTFS part, but am not able to resize the ext3 part, nor am I able to move it.

Please help.

---

### Post by bodhi.zazen on 2007-07-17
Newer versions of gparted will do this.

You need to do this from a live CD.

Take a peak at the gparted live CD:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by rbmorse on 2007-07-17
I will confirm the gParted LiveCD will do what you want because I just did it myself.No problems, strangeness or other issues. 

Resizing the partition will take a long time and you can't do anything else with the machine while gParted is doing it's thing.

---

### Post by hailtothethief on 2007-07-18
Ah! It worked perfectly.
Thank you very much.

---

