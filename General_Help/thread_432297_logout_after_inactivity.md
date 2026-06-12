---
title: "logout after inactivity"
date: 2007-05-03
forum: General Help
---

### Post by ph0neman on 2007-05-03
I am using Feisty Fawn 7.04.  I have the settings in power management set to NEVER to start turning things off and putting them to sleep.  Nonetheless Ubuntu logs me out after approximately 5 minutes of inactivity.  Any one know how I can stop this... its very annoying... its closes all my windows and totally kicks me out. 

thanks for any help.

here is a little info from the system log:  is there something i can set in gconf?

May  3 19:41:40 mobilenix kernel: [79124.832000] [fglrx] total      TIM  = 0
May  3 19:44:52 mobilenix gconfd (ph0neman-29255): GConf server is not in use, shutting down.
May  3 19:44:52 mobilenix gconfd (ph0neman-29255): Exiting
May  3 19:54:38 mobilenix gconfd (ph0neman-31389): starting (version 2.18.0.1), pid 31389 user 'ph0neman'
May  3 19:54:38 mobilenix gconfd (ph0neman-31389): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  3 19:54:38 mobilenix gconfd (ph0neman-31389): Resolved address "xml:readwrite:/home/ph0neman/.gconf" to a writable configuration source at position 1
May  3 19:54:38 mobilenix gconfd (ph0neman-31389): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  3 19:54:38 mobilenix gconfd (ph0neman-31389): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May  3 19:54:38 mobilenix gconfd (ph0neman-31389): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May  3 19:54:41 mobilenix gconfd (ph0neman-31389): Resolved address "xml:readwrite:/home/ph0neman/.gconf" to a writable configuration source at position 0
May  3 20:10:31 mobilenix kernel: [80855.684000] [fglrx] PCIe has already been initialized. Reinitializing ...
May  3 20:10:31 mobilenix kernel: [80855.700000] [fglrx] total      GART = 130023424
May  3 20:10:31 mobilenix kernel: [80855.700000] [fglrx] free       GART = 114032640
May  3 20:10:31 mobilenix kernel: [80855.700000] [fglrx] max single GART = 114032640
May  3 20:10:31 mobilenix kernel: [80855.700000] [fglrx] total      LFB  = 66977792
May  3 20:10:31 mobilenix kernel: [80855.700000] [fglrx] free       LFB  = 52588544
May  3 20:10:31 mobilenix kernel: [80855.700000] [fglrx] max single LFB  = 52588544
May  3 20:10:31 mobilenix kernel: [80855.700000] [fglrx] total      Inv  = 0
May  3 20:10:31 mobilenix kernel: [80855.700000] [fglrx] free       Inv  = 0
May  3 20:10:31 mobilenix kernel: [80855.700000] [fglrx] max single Inv  = 0
May  3 20:10:31 mobilenix kernel: [80855.700000] [fglrx] total      TIM  = 0
May  3 20:23:29 mobilenix -- MARK --
May  3 20:27:20 mobilenix kernel: [81864.804000] [fglrx] total      GART = 130023424
May  3 20:27:20 mobilenix kernel: [81864.804000] [fglrx] free       GART = 114032640
May  3 20:27:20 mobilenix kernel: [81864.804000] [fglrx] max single GART = 114032640
May  3 20:27:20 mobilenix kernel: [81864.804000] [fglrx] total      LFB  = 66977792
May  3 20:27:20 mobilenix kernel: [81864.804000] [fglrx] free       LFB  = 52588544
May  3 20:27:20 mobilenix kernel: [81864.804000] [fglrx] max single LFB  = 52588544
May  3 20:27:20 mobilenix kernel: [81864.804000] [fglrx] total      Inv  = 0
May  3 20:27:20 mobilenix kernel: [81864.804000] [fglrx] free       Inv  = 0
May  3 20:27:20 mobilenix kernel: [81864.804000] [fglrx] max single Inv  = 0
May  3 20:27:20 mobilenix kernel: [81864.804000] [fglrx] total      TIM  = 0

---

