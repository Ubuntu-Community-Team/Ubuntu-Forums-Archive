---
title: "how can i know the asterisk compile-time options came with ubuntu 14.04?"
date: 2016-01-15
forum: General Help
---

### Post by www-beebuu on 2016-01-15
Hi,managers:
I want to using the chan_dongle module in asterisk under ubuntu 14.04,and i compiled from source and load module under the asterisk CLI,but got warning like these:
[Jan 15 7:11:03] WARNING[17256]: loader.c:824 inspect_module: Module 'chan_dongle.so' was not compiled with the same compile-time options as this version of Asterisk.
[Jan 15 7:11:03] WARNING[17256]: loader.c:825 inspect_module: Module 'chan_dongle.so' will not be initialized as it may cause instability.
[Jan 15 7:11:03] WARNING[17256]: loader.c:915 load_resource: Module 'chan_dongle' could not be loaded.

So,how can i know the asterisk compile-time options came with ubuntu 14.04? Or anyone tell me what are that?


best bless

---

### Post by Bucky Ball on 2016-01-15
*Thread moved to **General Help**.*

Welcome. Installation and Upgrades concerns install and upgrade of Ubuntu and its flavours. There are no managers here. We're all volunteers, including staff, moderators and admin. :)

---

### Post by buzzingrobot on 2016-01-15
You might look at the source package.  There's a link at the bottom of this page: [http://packages.ubuntu.com/source/trusty/asterisk](http://packages.ubuntu.com/source/trusty/asterisk).  Maybe check the Control file, if you can decipher the Debianese.

---

### Post by www-beebuu on 2016-01-17
Thanks for volunteers & staff ,moderators and admin. Is there any suggestion else? maybe i need make a clearly question like this: what's the options in "make menuselect" must be selected to compile for mine question?

---

