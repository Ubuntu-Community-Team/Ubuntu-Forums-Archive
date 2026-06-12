---
title: "Partition Help"
date: 2006-11-13
forum: General Help
---

### Post by StreetSmart on 2006-11-13
Right now my drive looks like this

[Dapper Linux 71 gigs][swap 3 gigs]

I want to resize the 71 gigs so I can install edgy on the 10 gig partition and still have Dapper installed. The partition should now look like this.

[Linux Dapper 61 gigs][Linux Edgy 10 gigs][Swap 3 gigs]

I tried using gpartition in the edgy CD but I couldn't resize. How do I do this?

---

### Post by earobinson on 2006-11-13
the live cd should work, did you get an error, if so post it :)

---

### Post by StreetSmart on 2006-11-13
The following operation could not be applied to disk:

Resize /dev/sda1 from 71.48 GiB to 62.69 GiB

See the details for more information

---

### Post by earobinson on 2006-11-13
from the terminal run ```
sudo gparted
``` see if you get any more info

---

### Post by StreetSmart on 2006-11-13
Same error when staring gpart in sudo

---

### Post by earobinson on 2006-11-13
anyting in the terminal? If not you best bet is to try a diferent live cd like [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

