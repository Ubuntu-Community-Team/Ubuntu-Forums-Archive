---
title: "fglrxinfo crashes my system - desperate"
date: 2007-10-20
forum: General Help
---

### Post by mithbuntu on 2007-10-20
I have been struggling to get my system to run properly after upgrading to 7.10. My main problems are stemming from a disfunctional setup of my ATI card that is resulting in rather strange behavior on my computer. I have a radeon x1800 card and recently re-installed my drivers using envy.

Right now it seems that any time my computer tries to access any function calls that invoke the use of my graphics card, including the harmless fglrxinfo, I crash and are brought back to the log in screen. Beryl and compiz are not working and moving windows around my screen is slow and choppy.

Any help is appreciated and I will post any necessary info to help with my issue.

---

### Post by mithbuntu on 2007-10-20
I removed, manually downloaded from ati's site, compiled and reinstalled the ati drivers, but I am still having absolutely no luck. 

Could someone at least tell me how to examine the crash log or figure out WHY fglrxinfo is crashing my system?

---

### Post by mithbuntu on 2007-10-20
Upon examinig my syslog I have found this many times:

```

Oct 20 10:36:49 mithbuntu gdm[5393]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Oct 20 10:36:50 mithbuntu kernel: [  105.079564] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Oct 20 10:36:50 mithbuntu kernel: [  105.083201] [fglrx] Maximum main memory to use for locked dma buffers: 2889 MBytes.
Oct 20 10:36:50 mithbuntu kernel: [  105.083219] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0

```


Could the Fatal X error be the problem?  If so, how would I work with it to determine a solution?

---

