---
title: "How does one format an external drive so it is not in root?"
date: 2008-03-15
forum: General Help
---

### Post by Lord Xeb on 2008-03-15
I used gparted and formated my whole drive for ext3.... Now it is in ext3 and its owner is root! How do I format it so that I can use the space however I please?

---

### Post by PurposeOfReason on 2008-03-15
> **Lord Xeb said:**
> I used gparted and formated my whole drive for ext3.... Now it is in ext3 and its owner is root! How do I format it so that I can use the space however I please?
So you want it to be for any user? You could always chmod and chown it.

```

chown -R newowner /location
chmod 755

```
The -R in chown makes it for all folders in that location. So say your mountpoint is /storage you would

chown -R shawn /storage 

if your username was shawn.

---

### Post by Lord Xeb on 2008-03-15
Thanks! I got it. Just took me a little bit because I didn't know what location the disk was.

---

