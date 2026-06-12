---
title: "mISDN Ubuntu"
date: 2007-06-13
forum: General Help
---

### Post by dim_par on 2007-06-13
Hello everybody,

Has anybody succesfully installed misdn ([http://www.misdn.org/downloads/mISDN.tar.gz](http://www.misdn.org/downloads/mISDN.tar.gz))
on Ubuntu?
I am trying to compile it but no success.The error i get is:
make[1]: Entering directory `/usr/src/install-asterisk/mISDN-1_1_3'
echo 1_1_3 > VERSION ; \

-ne 
!!You should remove the following files:

/lib/modules/2.6.20-16-server/build/include/linux/mISDNif.h
/lib/modules/2.6.20-16-server/build/include/linux/isdn_compat.h
/usr/include/linux/mISDNif.h
/usr/include/linux/isdn_compat.h

In order to upgrade to the mqueue branch


-ne I can do that for you, just type: make force


make[1]: *** [test_old_misdn] Error 1
make[1]: Leaving directory `/usr/src/install-asterisk/mISDN-1_1_3'
make: *** [misdn] Error 2

The files mentioned above to the error message do not exist anywhere

Thanks in advance

Dimitris

---

### Post by spuncy on 2007-08-16
I think it's a /bin/dash issue - try changing /bin/sh to point to /bin/bash and see how it goes.

---

### Post by Rex Kekkonen on 2007-08-26
How do you do this alteration?

---

### Post by Rex Kekkonen on 2007-08-26
Okay I believe I solved that. Logging in as root was something I probably needed to do as well.

It seemed to compile, some errors I think but I could run mISDN commands (start, config) later although typing misdnportinfo does nothing whatsoever.

And thats where I am stuck essentially. I do not know if I need to bother with mISDNuser but it wouldn't compile, complained about types.h and errno.h which I searched for and then made links to the files in the appropriate folder, which just generated more errors anyway.

I do not even know how I am supposed to be using mISDN to connect and the misdn.org pages are cryptic and seem to assume I should know that which they are not typed. I am just "Huh? What next?"

---

