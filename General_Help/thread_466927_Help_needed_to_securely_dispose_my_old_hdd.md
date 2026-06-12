---
title: "Help needed to securely dispose my old hdd"
date: 2007-06-07
forum: General Help
---

### Post by lamadredelsapo on 2007-06-07
I want to get rid of my old 10GB hard drive, and I would like to securely erase all it's data, before giving it away. How should I do these? Any speciall app?

---

### Post by steeleyuk on 2007-06-07
There's a package called wipe in the repos. Never used it but the description claims it securely erases disks.

> **Secure file deletion**
Recovery of supposedly erased data from magnetic media is easier than what many
people would like to believe. A technique called Magnetic Force Microscopy
(MFM) allows any moderately funded opponent to recover the last two or three
layers of data written to disk. Wipe repeatedly writes special patterns to the
files to be destroyed, using the fsync() call and/or the O_SYNC bit to force
disk access.

---

### Post by Shazaam on 2007-06-07
The only SECURE way to erase all data is to take it apart and smash the disks to powder:D
Other than that find a disk wipe program that does multiple wipes with random ones and zeros. But you can still recover data from it with the right forensic software.

---

### Post by lamadredelsapo on 2007-06-07
I'll give wipe a try, but I don't really know how to test if it has securely wiped the disk.

---

### Post by steeleyuk on 2007-06-07
[Interesting article at the BBC if you want a read.]("http://news.bbc.co.uk/2/hi/technology/6677235.stm")

---

### Post by srt4play on 2007-06-07
Where I work, we use the DoD compliant [DBAN]("http://dban.sourceforge.net/")

---

### Post by viciouslime on 2007-06-07
Unless you know of some really good use for it as a funtional HDD then I would definitely take it apart and destroy it properly :D

If you take the casing off it then connect ONLY a power lead to it so it spins up, you can hold a screwdriver against it and it makes pretty patterns :D

---

### Post by rgiskard01 on 2007-06-07
DBAN as noted earlier is what I use...Guttman wipe...before donating anything.


But with it being only a 10Gb HDD though...might as well go the hammer route.

---

### Post by bmckee on 2007-06-07
[http://www.dban.org/](http://www.dban.org/)

---

### Post by FuturePilot on 2007-06-07
When I got rid of a really old 4 GB hard drive I took a hammer to it.:twisted:

---

### Post by bmckee on 2007-06-07
I prefer a drill press :-)    One of these days I'll use an oxy-acel torch just to say I've done it :-)

But I think the poster wanted to re-use it.

---

### Post by djchandler on 2007-06-07
> **FuturePilot said:**
> When I got rid of a really old 4 GB hard drive I took a hammer to it.:twisted:

Well, the hammer route is secure, but go the DBAN route and donate the drive to someplace that re-cycles, don't put it in the trash. Precious metals can be recovered from circuit boards at least. If the drive is still usable, please consider the re-cycling alternative. 10 gb doesn't seem like a lot to us, but it's enough for a boot drive for a rebuilt and donated computer for charitable uses. Find a reputable re-cycler in your area. In the U.S., they are even subsidized with federal grants.

Just how sensitive is the data on the drive? DBAN offers options that go way beyond U. S. Department of Defense standards. Run it more than once if that makes you feel better.

Regards,
D. J. Chandler

---

### Post by lamadredelsapo on 2007-06-07
I read DBAN's README and it is just what I was looking for. Thanks for the tip

---

