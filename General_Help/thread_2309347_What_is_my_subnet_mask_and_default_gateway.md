---
title: "What is my subnet mask and default gateway"
date: 2016-01-09
forum: General Help
---

### Post by carmen2012 on 2016-01-09
I did a ifconfig in a terminal session and had the below output.

 inet addr:10.1.1.8  Bcast:10.1.1.255  Mask:255.255.255.0

Could someone confirm the following two points for me:

1.  Is mask the same as subnet mask?
2.  Would that mean that Bcast is then my default gateway?

Thank you

---

### Post by matt_symes on 2016-01-09
Hi

> **carmen2012 said:**
> I did a ifconfig in a terminal session and had the below output.

 inet addr:10.1.1.8  Bcast:10.1.1.255  Mask:255.255.255.0

Could someone confirm the following two points for me:

1.  Is mask the same as subnet mask?

Yes. Your subnet mask is 255.255.255.0.

This means your subnet is 10.1.1.0/24

> 2.  Would that mean that Bcast is then my default gateway?

No. To see your default gateway, open a terminal and type

```
route -n
```

Look for the line that has a capital 'G' in the flags section. That is your 'G'ateway.

Kind regards

---

