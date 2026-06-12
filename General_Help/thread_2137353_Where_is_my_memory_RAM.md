---
title: "Where is my memory RAM?"
date: 2013-04-20
forum: General Help
---

### Post by ubunet on 2013-04-20
Hi,

My laptop Acer Aspire One 722 have 2GB of RAM, but the Xubuntu 12.10 x32 shows only 1.7 GB. Why?

```
free -m -h
             total       usado      livre    compart.  buffers     em cache
Mem:          1,7G       902M       840M         0B        21M       216M
-/+ buffers/cache:       664M       1,1G
Swap:         1,9G         0B       1,9G

```

Kernel
```
uname -a
Linux NETUBU 3.5.0-27-generic #46-Ubuntu SMP Mon Mar 25 20:00:05 UTC 2013 i686 athlon i686 GNU/Linux
```

---

### Post by The Cog on 2013-04-20
I believe it shows usable RAM - it deducts RAM occupied by the operating system. Confusing, but that's the way it is.

---

### Post by dabl on 2013-04-20
What shows 

```
free -b -h
```?

Also look in your BIOS for "shared video RAM" -- part of your memory is given to the video system.

---

### Post by ubunet on 2013-04-20
> **dabl said:**
> What shows 

```
free -b -h
```?

Also look in your BIOS for "shared video RAM" -- part of your memory is given to the video system.

"Shared video Memory" 256MB -- OK!

---

