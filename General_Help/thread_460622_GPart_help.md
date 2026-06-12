---
title: "GPart help"
date: 2007-05-31
forum: General Help
---

### Post by rkd1312 on 2007-05-31
I need help trying to make a partition for Ubuntu i am running the gpart in the Ubuntu live CD and when i go to resize my old partition I get the attached error. 

Thank You

---

### Post by merlinus on 2007-05-31
If your old partition is windows and you have not already done so:

Run defrag several times

Set virtual paging to zero.  You can set it back after partitioning and installing ubuntu.

It also looks like you should run chkdsk on that partition as well.

hth...

-merlin

---

### Post by sloggerkhan on 2007-05-31
no ideas here. Maybe you could add some detail about your drive and the specific op you were going to do.

---

### Post by rkd1312 on 2007-06-01
Well it's a 20gb hdd and i was trying to resize the partition

---

### Post by merlinus on 2007-06-01
From the screenshot, it seems to me that windows is taking up too much room for you to make the new partition anything more than a few gigs

-merlin

---

### Post by rkd1312 on 2007-06-01
but only 53% is being used

---

### Post by merlinus on 2007-06-01
From what I can see, about 9.3G is being used, and you cannot shrink windows to around 10 total.  The virtual paging and such will preclude this.

So perhaps if you allocate 5G or so to ubuntu, it will work.

-merlin

---

### Post by rkd1312 on 2007-06-02
tried all your tips still the same error

---

### Post by merlinus on 2007-06-02
The only other thing I can think of is to try booting with the gparted live cd.  You can download it at:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

and burn it the same way you did the ubuntu live cd.

It is a later version of gparted.

-merlin

---

