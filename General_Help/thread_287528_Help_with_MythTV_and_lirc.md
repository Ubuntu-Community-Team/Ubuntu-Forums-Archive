---
title: "Help with MythTV and lirc"
date: 2006-10-28
forum: General Help
---

### Post by jacrider on 2006-10-28
I have had a fairly tough upgrade to Edgy.

I have had to do a clean install after X-org died.

I am using a Hauppage PVR-150 card.

Anyway, I have re-installed the OS and have successfully installed MythTV 0.20, with the exception that I can't get lirc installed.  I have tried to use the one in the repos and install and compile from source.

In all cases, I can't get lirc_i2c to be created.

Anyone had any success getting this setup?

Many thanks.

---

### Post by superm1 on 2006-10-30
jacrider,

Unfortunately the latest release of lirc is broken for kernel 2.6.17 and up ( Ubuntu is using 2.6.17).  You will probably have to use LIRC CVS to be able to use the lirc_i2c module (it has been fixed in CVS).

The other option is to patch the lirc package for this i2c patch.  I will probably get around to having a third party package that includes this patch out eventually (after I get my edgy repo host setup correctly).

Here is the patch if you would like to apply it yourself to lirc sources:
[http://lirc.cvs.sourceforge.net/lirc/lirc/drivers/lirc_i2c/lirc_i2c.c?r1=1.36&r2=1.38](http://lirc.cvs.sourceforge.net/lirc/lirc/drivers/lirc_i2c/lirc_i2c.c?r1=1.36&r2=1.38)

---

### Post by superm1 on 2006-10-30
Jacrider,

To follow up, I Have put together a repository including i2c & gpio patches.

See the bottom of [https://help.ubuntu.com/community/Install_Lirc_Edgy#head-61b516764f233bff0f43ac2ac97bb18db14ad2be](https://help.ubuntu.com/community/Install_Lirc_Edgy#head-61b516764f233bff0f43ac2ac97bb18db14ad2be)

For more information about how to set up my packages.

---

