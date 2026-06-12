---
title: "Foomatic/CUPS config problem - can't delete printer!"
date: 2008-05-15
forum: General Help
---

### Post by daehenoc on 2008-05-15
Hi all,

I have a Debian installation and I can't remove a particular printer queue!  I've tried using foomatic-gui, there are two printers defined and I can't delete either of them or change which printer is the default in applications.  I can change the default printer in foomatic-gui, but it doesn't make any difference in Firefox, Firefox still brings up the wrong printer as the default.

When I click on a printer in foomatic-gui and click the delete printer button, a message appears at the bottom of foomatic-gui that tells me 'printer deleted'... yet the printer is still listed in foomatic-gui!  See the attached capture.

These queues used to be in the CUPS configuration as well, while trying to change the default queue in CUPS I removed them from the CUPS configuration and now I can't even delete the queues from the command line with foomatic-configure:
# foomatic-configure -R -n Aficio_2018D
lpadmin: Forbidden
Unable to delete queue: Aficio_2018D

I tried purging all foomatic and CUPS packages and reinstalling them and this foomatic configuration for the Aficio printer won't go away!

How do I purge any and all CPUS/foomatic/lpadmin printing configuration information so I can start again with my printer setup so I can set up the correct printer as the default?

Thanks!

---

### Post by daehenoc on 2008-05-15
More information - I can't even add a new printer via foomatic-gui - the whole 'add printer' process is done, but after you finish the process, the new printer just doesn't appear in foomatic-gui :(

And the printers that do appear in foomatic-gui don't appear in the CUPS configuration page [http://localhost:631/](http://localhost:631/)  Something is broken :(

I also can't configure either of these printers in foomatic-gui, when I click on one of them, the configure button is greyed out.  Note to self: see what 'lpstat -o' shows.

---

