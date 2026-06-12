---
title: "Does not boot"
date: 2007-06-01
forum: General Help
---

### Post by schnauzer93 on 2007-06-01
When I try to boot from cd, I see the ubuntu screen and select the first option. Then instead of booting, I see: 

Int 14: CR2 cf8000000 err00000000 EITc020c384 CS 00000060 flags 00010007
Stack: c00f7d50 c03f129b c0371d8c 00000002 c00f7d59 000f7d50 00000000 00000000

Any ideas?

I am new to Linux in general, so please be specific 

: )

---

### Post by jimbob on 2007-06-01
Sounds like a possible bad CD.  Did you check the md5sum after downloading?

Is this the live/install CD or the alternate?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by schnauzer93 on 2007-06-01
1. How do I check an md5 sum?

2. When I brought up the help menu, it said the system requirements were 128mb of RAM. (I have 256)

---

### Post by jimbob on 2007-06-01
Open a terminal window and type 'sudo md5sum <name of your .iso file>' without the tick marks.  (You may not need the sudo but it won't hurt).  Compare this with the md5sum listed on the site from which you downloaded the file.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

.*.. things should be done from the command line the way Nature intended ...*

---

### Post by schnauzer93 on 2007-06-01
Terminal window? I'm in Windows...

---

### Post by merlinus on 2007-06-01
This may help:

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

-merlin

---

### Post by schnauzer93 on 2007-06-01
OK. I've dragged-and-dropped the file into th winMD5Sum utility and clicked "compare". It said that the sums are different. Do I have to re-download the ISO now?

---

### Post by merlinus on 2007-06-01
Yes.  It probably got corrupted during your initial download.

-merlin

---

