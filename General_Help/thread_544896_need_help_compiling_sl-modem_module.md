---
title: "need help compiling sl-modem module"
date: 2007-09-06
forum: General Help
---

### Post by mykrob on 2007-09-06
Hey-

Trying to get the sl-modem module built for a Best Data USB smart link modem..

here is the output of my module assistant log:

[http://pastebin.ca/684927](http://pastebin.ca/684927)

Please advise.
thanks,
-myk

---

### Post by geraldm on 2007-09-07
UTS_RELEASE is defined in the kernel headers linux/utsrelease.h

or you could pass it on the command line with -D"..."

Gerald

---

### Post by mykrob on 2007-09-07
i'm sorry, i dont understand.

Can you explain more?

Thanks,
-myk

---

### Post by geraldm on 2007-09-07
When that fails, change to directory /usr/src/modules/sl-modem/drivers
It appears that the compile fails with undefined variable UTS_RELEASE.
Look in the files in the kernel and find out what that value is to be.
replace "VAL" in the next line with that value.

gcc-4.1 -I/lib/modules/2.6.20-16-386/build/include -DUTS_RELEASE="VAL" -o kernel-ver kernel-ver.c

Execute the above command in that directory.
That should allow the compile to continue.  If the compile is successful, go back to the top
directory and try make again.

Gerald

---

