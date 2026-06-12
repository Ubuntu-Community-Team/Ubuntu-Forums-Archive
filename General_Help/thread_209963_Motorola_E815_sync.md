---
title: "Motorola E815 sync"
date: 2006-07-05
forum: General Help
---

### Post by TomPreuss on 2006-07-05
Hello all.

Has anyone gotten a Motorola E815 to sync with Dapper?

I just got one earlier today and I can't seem to get it to interface.  I'm using a USB cable.

I know it is connecting at /dev/ttyACM0 from a ```
$ dmesg | tail
``` after I plug it in, but other than that, I haven't had any success.  I've tried/messed around with KMobileTools, Multisync, and moto4lin.

Thanks in advance.

---

### Post by kodiak on 2006-07-12
[Access Motorola phones through USB on Hoary using Moto4Lin - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=56253").
Someone says [ this method works with Dapper also]("http://www.ubuntuforums.org/showpost.php?p=892204&postcount=4").
E815 is said to be [suported by moto4lin]("http://moto4lin.sourceforge.net/wiki/Category:Models").

---

### Post by TomPreuss on 2006-07-13
> **kodiak said:**
> [Access Motorola phones through USB on Hoary using Moto4Lin - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=56253").
I found out moto4lin [doesn't work for my phone](http://moto4lin.sourceforge.net/wiki/E815).

> **kodiak said:**
> Someone says [ this method works with Dapper also]("http://www.ubuntuforums.org/showpost.php?p=892204&postcount=4").
Yeah, moto4lin again.

> **kodiak said:**
> E815 is said to be [suported by moto4lin]("http://moto4lin.sourceforge.net/wiki/Category:Models").
Yeah, the [E815 wiki page](http://moto4lin.sourceforge.net/wiki/E815) is only included in that category because it can be switched into PTK mode, but that's it.

I'm going to try getting the Bluetooth to work instead of the USB cable.  I've made a little headway with that, I think I just need to hack the phone to get around Verizon's restrictions.

Thanks.

---

