---
title: "CloneCD Clone?"
date: 2007-04-05
forum: General Help
---

### Post by kaffemonster on 2007-04-05
I have just purchased a Blaupunkt car stereo with GPS. It's nice and all, but requires the map cd to navigate. I never keep original cds in my car, only copies, and I really don't like the idea of keeping the original navi-cd in the car, as a new one costs over 200$ here in Denmark. So the first thing I did, was to fire up gnomebaker, to make a copy. Didn't work. I then tried CloneCD in Windows. Didn't work. Even tried Alcohol 120% in windows, and that didn't work either :(

Is there an app for Linux/Ubuntu that will do EXACT bit-by-bit copies of a cd, no matter what copy-protection is used? I REALLY don't want to scratch 200 dollars worth of cd!

---

### Post by cmost on 2007-04-05
I don't bother with a GUI when a simple command can accomplish what you want.  Insert the CD, then open a terminal and type the following:

$dd if=/dev/cdrom of=/path/to/output/file.iso

(obviously, you will adjust the above command in accordance to where/how your own optical drive is mounted and where you want to save the disk image.)

You can add lots of options to the dd command, which is quite versatile.  Check here for more information.  Good luck!

[http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

---

### Post by kaffemonster on 2007-04-06
Well, I think I'm doing something wrong...

```
ssn@ssn-laptop:~$ sudo dd if=/media/cdrom0 of=/home/ssn/scandinavia.iso
Password:
dd: læser '/media/cdrom0': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0,00132698 seconds, 0,0 kB/s
```

Any Ideas?

---

### Post by cmost on 2007-04-09
You cannot refer to your input device by its mount point.  In your case, you're referencing your optical drive as /media/cdrom0.  Look to see what device node corresponds to /media/cdrom0, and use that path in your 'dd' command.  Example:  In my case, /dev/cdrom (or /dev/hdd) refer to my optical device.  Good luck.

---

### Post by kaffemonster on 2007-04-11
Ahh, that explains it! I'll try that when I get home!

---

