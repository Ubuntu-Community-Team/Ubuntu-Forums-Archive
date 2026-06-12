---
title: "Compiz Desktop &quot;Horizontal Virtual Size&quot; Stuck at 2"
date: 2008-06-20
forum: General Help
---

### Post by aidave on 2008-06-20
When I try to move the slider in Compiz settings, it always goes to 2.  Its bizarre.  It pauses a couple seconds, then resets to 2 no matter what value I choose.

This happened after I enabled "Emerald"

How do I get 4 desktops again?

---

### Post by aidave on 2008-06-20
I was able to change it using the "gconf" editor

---

### Post by fermulator on 2009-03-29
> **aidave said:**
> I was able to change it using the "gconf" editor

OK, but where?

---

### Post by fermulator on 2009-03-29
> **fermulator said:**
> OK, but where?

OH hi, found it: [https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/129152](https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/129152)

appz >> compiz >> general >> screen0 >> options
check the hsize value.

---

### Post by n4h0j on 2011-01-08
> **fermulator said:**
> OH hi, found it: [https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/129152](https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/129152)

appz >> compiz >> general >> screen0 >> options
check the hsize value.

Cheers, just solved the same problem for me in Linux Mint Debian Edition.

---

