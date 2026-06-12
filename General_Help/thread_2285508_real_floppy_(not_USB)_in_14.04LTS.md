---
title: "real floppy (not USB) in 14.04LTS"
date: 2015-07-06
forum: General Help
---

### Post by skippylou on 2015-07-06
Ubuntu 14.04LTS updates current.

Tried **everything** on this page [http://askubuntu.com/questions/168597/how-do-i-use-a-floppy-drive-in-ubunt](http://askubuntu.com/questions/168597/how-do-i-use-a-floppy-drive-in-ubunt)

/dev/fd0 does not exist!  What next?

PS This is the floppy in question: [http://www.newegg.com/Product/Product.aspx?Item=N82E16821121001](http://www.newegg.com/Product/Product.aspx?Item=N82E16821121001)

---

### Post by Bucky Ball on 2015-07-06
So this command:

```
lsmod | grep -i floppy
```

... returns nothing?

You can change your thread title by editing the first post> 'Go Advanced'. There may be a time limit for how long you've got to change it, not sure where that stands now. Any problems, just PM myself or report the first post using the 'Report Post' button and ask for the title to be changed. Good luck.

---

### Post by skippylou on 2015-07-06
> **Bucky Ball said:**
> So this command:

```
lsmod | grep -i floppy
```

... returns nothing?

You can change your thread title by editing the first post> 'Go Advanced'. There may be a time limit for how long you've got to change it, not sure where that stands now. Any problems, just PM myself or report the first post using the 'Report Post' button and ask for the title to be changed. Good luck.


nothing

---

### Post by Vladlenin5000 on 2015-07-06
The first thing is to make sure the drive is working and it ISN'T disabled in BIOS...

---

### Post by SeijiSensei on 2015-07-06
Take a look at /var/log/dmesg.  Do you see the floppy being recognized by the kernel when it boots?

---

### Post by skippylou on 2015-07-06
> **SeijiSensei said:**
> Take a look at /var/log/dmesg.  Do you see the floppy being recognized by the kernel when it boots?


These are all the references to "floppy" in /var/log/dmesg:

[    1.602236] Floppy drive(s): fd0 is 1.44M

[    4.624081] floppy0: no floppy controllers found

[   16.856162] Floppy drive(s): fd0 is 1.44M

[   19.880068] floppy0: no floppy controllers found

Which means what?  Bad floppy drive? Bad motherboard?

---

### Post by skippylou on 2015-07-06
> **Vladlenin5000 said:**
> The first thing is to make sure the drive is working and it ISN'T disabled in BIOS...

1.44M floppy enabled in BIOS.

---

### Post by Vladlenin5000 on 2015-07-06
> **skippylou said:**
> Which means what?  Bad floppy drive? Bad motherboard?

Neither. It just tells you the module isn't loaded... Why that happened I don't know. It may or may not be hardware related.

You can try```
sudo modprobe -v floppy
lsmod | grep -i floppy
```

---

### Post by skippylou on 2015-07-06
Additional information:

The floppy drive I purchased had absolutely no indication of pin 1 or indexing slot.  Made my best guess.  Floppy LED was on continuously which indicates reversed connector so I corrected this.  Read somewhere that this should not have caused damage but this could be wrong.

---

### Post by skippylou on 2015-07-06
> **Vladlenin5000 said:**
> Neither. It just tells you the module isn't loaded... Why that happened I don't know. It may or may not be hardware related.

You can try```
sudo modprobe -v floppy
lsmod | grep -i floppy
```

skippy@skippy-KT690-mITX:~$ sudo modprobe -v floppy
[sudo] password for skippy: 
insmod /lib/modules/3.16.0-41-generic/kernel/drivers/block/floppy.ko 
modprobe: ERROR: could not insert 'floppy': No such device
skippy@skippy-KT690-mITX:~$ lsmod | grep -i floppy
skippy@skippy-KT690-mITX:~$

---

### Post by skippylou on 2015-07-06
additional information:  Replaced with a used but presumed good Mitsumi floppy drive.  No change.

---

### Post by skippylou on 2015-07-06
additional information: I can boot DOS from the drive so it isn't the drive or the motherboard.

---

### Post by Bill_Braskey on 2016-01-24
> **skippylou said:**
> Additional information:

The floppy drive I purchased had absolutely no indication of pin 1 or indexing slot.  Made my best guess.  Floppy LED was on continuously which indicates reversed connector so I corrected this.  Read somewhere that this should not have caused damage but this could be wrong.

Pin 1 is always on the side of the ribbon cable that has the red stripe.  On devices that use ribbon cables (e.g., floppy, IDE), pin 1 is *typically* on the side closest to the power connector, but this is by no means standard.  Ribbon cable devices are usually keyed and/or have a missing pin that must line up with a filled-in (no hole present) pin location on the cable.  Again, this is not 100% standardized.

---

### Post by Bucky Ball on 2016-01-25
*Thread closed.*

Welcome and thanks for sharing, but let's not wake the dead. ;)

---

