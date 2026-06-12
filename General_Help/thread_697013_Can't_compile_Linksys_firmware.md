---
title: "Can't compile Linksys firmware"
date: 2008-02-14
forum: General Help
---

### Post by giruzz on 2008-02-14
I'm trying to compile the firmware 1.0.0.65 for my Linksys Wag54g-v3 and I keep getting the same error:

```
/bin/sh: /home/me/Desktop/WAG54GV3-EU-1.00.65/src/router/mipsel-uclibc/target/../mksquashfs: not found
make: *** [lang] Error 127

```

Now, I guess that I'm missing something. Together with the source code I've downloaded from Linksys there are 4 software that should be compiled&installed if errors appears while compiling the firmware.

My only problem is that I can't even compile those 4 software because I'm getting other errors, so I've installed (I think) the very same software using  Synaptic...but...I didn't work.

Is there anyone that could help with this?

Thank you

giruz

---

### Post by sebw on 2008-03-15
I'm trying to build the same firmware right now.

I had to edit the Makefile and fix the path to mksquashfs in src/router/Makefile to get past that error

Meanwhile I had to install the package libstdc++2.10-glibc2.2 because ldd revealed a library was missing for mksquashfs to work.

I'm now getting to this point :

```
---------- add code pattern --------
input file is [de_lang.image]
output file is [de_lang.bin]
code pattern is [WAG2]

Make date==>Year:2008,Month:3,Day:15,Hour:22,Min:38,Sec:23

Firmware version =>1.00.65

1:1,0

2:00,0

3:65,65
./tichksum de_lang.bin
File doesn't contain the checksum, adding
Calculated checksum is 6A65579E
Added successfully
make[1]: quittant le répertoire « /home/sw/Bureau/WAG54GV3-EU-1.00.65/src/image »
```

I can't find any usable firmware image anywhere though, so I guess something failed

---

### Post by giruzz on 2008-03-15
> **sebw said:**
> I'm trying to build the same firmware right now.

I had to edit the Makefile and fix the path to mksquashfs in src/router/Makefile to get past that error

Meanwhile I had to install the package libstdc++2.10-glibc2.2 because ldd revealed a library was missing for mksquashfs to work.

I'm now getting to this point :

I can't find any usable firmware image anywhere though, so I guess something failed

I gave up. Btw, linksys just published a firmware 1.0.0.46 who should be better then 1.0.0.65 we are trying to compile.

The indian-outsourced helpdesk told me that they were the same and there is no difference. They also removed all the previous versions.

g.

---

