---
title: "ubuntu 14.04 LTS jabber and gtalk modules gone"
date: 2014-10-14
forum: General Help
---

### Post by blwegrzyn on 2014-10-14
What happened to jabber and gtalk modules for asterisk?
How do I get them back?

thx

---

### Post by blwegrzyn on 2014-11-10
Current Ubuntu trusty version does not come with res_jabber and chan_gtalk.

* version on Ubuntu is:

dpkg --list | grep asterisk
asterisk 1:11.7.0~dfsg-1ubuntu1 amd64 Open Source Private Branch Exchange (PBX)
asterisk-modules 1:11.7.0~dfsg-1ubuntu1 amd64 loadable modules for the Asterisk PBX

i downloaded * src via apt-get, run ./configure, make menuconfig, added above module and res, compiled and copied the res_jabber.so and chan.gtalk to asterisk modules dir.

Unfortunately this trick does not work and I get below errors:
ip-1.1.1.14*CLI>
ip-1.1.1.14*CLI> module load res_jabber.so
Unable to load module res_jabber.so
Command 'module load res_jabber.so' failed.
[Nov 10 15:25:04] WARNING[23185]: loader.c:824 inspect_module: Module 'res_jabber.so' was not compiled with the same compile-time options as this version of Asterisk.
[Nov 10 15:25:04] WARNING[23185]: loader.c:825 inspect_module: Module 'res_jabber.so' will not be initialized as it may cause instability.
[Nov 10 15:25:04] WARNING[23185]: loader.c:915 load_resource: Module 'res_jabber.so' could not be loaded.
ip-1.1.1.14*CLI>
ip-1.1.1.14*CLI> module load chan_gtalk
Unable to load module chan_gtalk
Command 'module load chan_gtalk' failed.
[Nov 10 15:25:17] WARNING[23185]: loader.c:486 load_dynamic_module: Error loading module 'chan_gtalk': /usr/lib/asterisk/modules/chan_gtalk.so: undefined symbol: ast_aji_buddy_destroy
[Nov 10 15:25:17] WARNING[23185]: loader.c:902 load_resource: Module 'chan_gtalk' could not be loaded.
ip-1.1.1.14*CLI> module load chan_gtalk.so
Unable to load module chan_gtalk.so
Command 'module load chan_gtalk.so ' failed.
[Nov 10 15:25:37] WARNING[23185]: loader.c:486 load_dynamic_module: Error loading module 'chan_gtalk.so': /usr/lib/asterisk/modules/chan_gtalk.so: undefined symbol: ast_aji_buddy_destroy
[Nov 10 15:25:37] WARNING[23185]: loader.c:902 load_resource: Module 'chan_gtalk.so' could not be loaded.
ip-1.1.1.14*CLI>

how can i get these modules to work?

thx

---

### Post by blwegrzyn on 2014-11-11
seems like the solution is simpler then i though.

I went to compile options and I found out that:

chan_gtalk replaced with chan_motif
res_jabber replaced with res_xmpp

thx

---

