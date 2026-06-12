---
title: "ircd-hybrid Won't complete install"
date: 2007-08-19
forum: General Help
---

### Post by Admiral-Cyclops on 2007-08-19
I am pleading...  Someone please help, I have found no information on what could cuase this..

I have run ircd-hybrid before and with good results, I had to reinstall Ubuntu Feisty Fawn on the system and 99.99% of everything works fine except that I cannot get ircd-hybrid to configure after it unpacks and installs.

I even changed the sym link for sh to point to bash instead of dash as I know some scripts fail when you don't do this.

Here is the error...

```
Setting up ircd-hybrid (7.2.2.dfsg.1-3) ...
Starting Hybrid 7 IRC Server: ircd-hybridinvoke-rc.d: initscript ircd-hybrid, action "start" failed.
dpkg: error processing ircd-hybrid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ircd-hybrid
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Saatii on 2008-06-03
I haven't seen the changelog, but the readme.first says:

```
************ Note for those who don't bother reading docs ***************
  * - Reading INSTALL is now a must, as the old DPATH is now specified    *
  *   when configure is run.                                              *
  *   You now need to ./configure --prefix="/path/to/install/it"          *
  * - The old config format WILL NOT WORK. Please see etc/example.conf ! *
  * - The old kline, dline, xline, gline format WILL NOT WORK.
  *************************************************************************
```

cheers,
saatii

---

