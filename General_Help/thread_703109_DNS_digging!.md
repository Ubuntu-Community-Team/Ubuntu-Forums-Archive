---
title: "DNS digging!"
date: 2008-02-21
forum: General Help
---

### Post by Chimei on 2008-02-21
Hey guys,

Just a quick question. I used to get a "status: NOERROR" when i dig my nameserver, however now i get a  "Status : NXSERVER". Wonder if anybody could shed some light for me XD

Cheers

---

### Post by GuDoN on 2008-02-21
dude, i think i got this message like yesterday, and i had some problems with my network.

to resolve it i just checked in my networking preferences and made sure that ive got all my ip and gateway as well as dns settings correct. and i went into terminal:

$ sudo ifup --force eth0
$ sudo ifup --force eth1

after that, i didn't recieve any errors and everything was working shabby! :D

---

### Post by Chimei on 2008-02-21
Great!

Ill give it a go and let you know! Thanks GuDon.

Edit:
Ok i just tried the command, but i get the following

SIOCADDRT: File exists

Any ideas?

Cheers

---

