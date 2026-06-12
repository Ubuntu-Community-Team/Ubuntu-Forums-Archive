---
title: "printing works, lpstat does not"
date: 2007-06-11
forum: General Help
---

### Post by IndigoMontoya on 2007-06-11
I am using ubuntu 7.04 and have 2 networked printers that print (reasonably well) through all native applications.  I am forced to run microsoft word (using crossover office) due to compatibility issues with colleagues and can not print from it.  The printers show up, but no printing occurs.  When I run Word from the command line and print I get this error:

```
 Status Information, attempt 1 of 3:
sending job 'spruce@localhost+834' to Optra-S-1855@localhost
 connecting to 'localhost', attempt 1
 cannot open connection to localhost - Connection refused
Make sure the remote host supports the LPD protocol
and accepts connections from this host and from non-privileged (>1023) ports
Waiting 10 seconds before retry

```


running 'sudo lpstat -a' I get:

```

Printer 'Color-LaserJet-2600n@localhost' - cannot open connection - Connection refused
Make sure the remote host supports the LPD protocol
Printer 'Optra-S-1855@localhost' - cannot open connection - Connection refused
Make sure the remote host supports the LPD protocol
Printer 'Optra-S-1855NEW@localhost' - cannot open connection - Connection refused
Make sure the remote host supports the LPD protocol
Printer 'all@localhost' - cannot open connection - Connection refused
Make sure the remote host supports the LPD protocol

```

again, printing from other native programs (openoffice, evince, evolution) works, but not lpstat.  any thoughts?  The printers show up as socket://"their_ip":9100 when I go to my local cups webpage.

Thanks!

---

