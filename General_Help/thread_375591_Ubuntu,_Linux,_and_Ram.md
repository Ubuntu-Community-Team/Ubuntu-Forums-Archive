---
title: "Ubuntu, Linux, and Ram"
date: 2007-03-03
forum: General Help
---

### Post by cubanresourceful on 2007-03-03
Im just wondering, because I know Windows only supports up to 4 GB of ram unless you run 64 bit. But, is the same with Ubuntu, or Linux in general? If I buy a bi-processor, which can run in either 32 bit or 64 bit mode, is 64 bit mode much buggier in Ubuntu? Im just wondering, if in Ubuntu, more that 4 GB of ram can be utilized without having to use 64 bit mode.

---

### Post by andreas64 on 2007-03-04
Hi,

32-bit-operating-systems generally don't support more than 4GB of ram. If you want to have more ram, you have to install a 64-bit-system.

The 64-bit-Ubuntu isn't 'more buggier' as the 32-bit-version - but there are some other limitations, esp. with audio and video-codecs, Flash etc. These are only availible on 32-bit-systems.

Andreas

---

### Post by cubanresourceful on 2007-03-04
Damn, and I really want multimedia stuffs. I guess I just won't play with more than 4 GB of ram until the future needs it. :D Thanks for the help.

---

### Post by fragos on 2007-03-04
Once you have enough memory so that swap space isn't used you shouldn't see any benefits from adding more ram.  How much ram you need is effected by how many services have daemons and how how many applications are loaded at the same time.  Some applications are more memory hungry than others, multimedia for example.  To see how your system is performing open a terminal window and type free.  This will tell you how much swap space is being used.  I recently upgraded from 512KB to 1GB and haven't to my knowlege used any swap space.  I regularly run tvtime, firefox, openoffice and gimp at the same time.

---

