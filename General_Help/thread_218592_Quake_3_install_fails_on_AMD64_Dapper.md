---
title: "Quake 3 install fails on AMD64 Dapper"
date: 2006-07-18
forum: General Help
---

### Post by smith. on 2006-07-18
Hi, new to linux only installed it last weekend but my initial findings are really good.

I have seen 64bit problems with Quake3 before but wondered if they had been solved.  I have copied the .pak files into /usr/local/games/Quake3/baseq3
and downloaded the latest point release from ID.

When I run the point release I get the following message :

This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
Please contact Id software technical support at [email]bugs@idsoftware.com[/email], or [email]ttimo@idsoftware.com[/email]
The setup program seems to have failed on unknown/glibc-2.0

Has this problem been solved ? I had seen solutions setting up a 32bit chroot(?) but have no idea how to do this.

Thanks for any help.

---

### Post by zeroepoch on 2006-07-28
I had the same problem try this:

```
sudo linux32 ./linuxq3apoint-1.32b-3.x86.run
```

---

### Post by lennie2 on 2007-06-07
must linux32 be loaded via apt-get install linux32 ??
Will this run the executable in 32 bit mode but afterwards everything will still be 64 bit ?

Many thanks

---

### Post by zeroepoch on 2007-06-09
It just lets you install the 32-bit version.  There is not pure 64-bit version unfortunately.

---

### Post by Sockerdrickan on 2007-06-09
There is 64bit

[www.ioquake3.org](www.ioquake3.org) enjoy

---

### Post by lennie2 on 2007-06-14
Brilliant busy downloading the run file for Linux and will post my findings and results here.

L

---

### Post by lennie2 on 2007-06-18
> **lennie2 said:**
> Brilliant busy downloading the run file for Linux and will post my findings and results here.

L

I got Quake3 running on AMD64 without sound so far, could not get ioquake3 going most probably cause I'm a newbie and ioquake3 documentation is lacking.

I have a Gigabyte Motherboard with onboard sound (VIA Chipset High Definition )

---

### Post by brexsis on 2007-10-12
i just copyied quake3.exe, baseq3 folder in my homefolder, and run throught wine, it wroks for me :)

---

