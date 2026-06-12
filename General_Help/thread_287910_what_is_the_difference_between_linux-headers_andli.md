---
title: "what is the difference between linux-headers andlinux-headers-generic"
date: 2006-10-29
forum: General Help
---

### Post by sup on 2006-10-29
The title says it, in synaptic, there is linux-headers-2.6.17-10 and linux-headers-2.6.17-10-generic installed, about only difference is in size, one has 25MB, the other 60MB.

---

### Post by bsussman on 2006-10-29
> **sup said:**
>  about only difference is in size

I don't think so.  

I think you should turn on the package properties display in synaptic ( settings ->preferences->general->appearance) and explore the description and other tabs.

also try:

```
diff -qr /usr/src/linux-headers-2.6.17-10 /usr/src/linux-headers-2.6.17-10-generic
```(that is all 1 line)

---

### Post by PriceChild on 2006-10-29
/usr/src/linux-headers-2.6.17-10 Is the files common to -10-generic, -10-386 etc.

/usr/src/linux-headers-2.6.17-10-generic is the files specific to -generic in addition to /usr/src/linux-headers-2.6.17-10

---

### Post by sup on 2006-10-29
Oh, I see, so I definitely need both. Thanks

---

