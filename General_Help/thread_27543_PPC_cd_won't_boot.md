---
title: "PPC cd won't boot"
date: 2005-04-16
forum: General Help
---

### Post by alock on 2005-04-16
I downloaded the ppc iso image and burnt it using Nero on my PC (since my Mac doesn't have CDRW capabilities). This worked fine, however the disc won't boot on the Mac even when holding down the 'c' key.

Just to be clear, I did md5sum the iso (it's fine), I did verify the disc burnt correctly (it did) and I did verify that the contents of the disc can be read from OS X (they're okay too). It just won't boot.

Is there something I'm missing about bootable CDs on the Mac. Do they have to be finalized or anything like that? That's about the only thing I didn't try. I'm assuming it shouldn't matter that the iso was burnt on the PC, but does it?

Thanks in advance!

---

### Post by ssam on 2005-04-16
just a quick check,

an easy mistake to make is to put the iso as a file on the cd, rather than using it as an image for the cd.

if in mac os x, when you open the cd you see a .iso file then you have do it wrong.

---

### Post by alock on 2005-04-17
No, the contents of the CD are correct - md5sum.txt, README.diskdefines, casper/, dists/ etc.

As I say, the disk looks fine but no joy. I'm going to try burning one more time (still from the PC) but using disc at once mode (I used track at once last time) and finalizing the CD this time. If that doesn't work, I'm at a loss to explain why it won't boot.

---

### Post by ssam on 2005-04-17
that might help.

if not you might want to reset PRAM, or look up some open firmware commands.

you could alway order an official cd set from [http://shipit.ubuntulinux.org/](http://shipit.ubuntulinux.org/) (for free), or search for 'cheap linux cds' on google.

---

### Post by ubuntubrian on 2005-04-27
I haven't been following this thread but I also couldn't get a bootable CD until I downloaded FireStarter FX for CD burning in OS X. It worked great and I have a live CD! I have other use issues but the CD boots up and detects hardware and all.
Good luck. ;-)

---

