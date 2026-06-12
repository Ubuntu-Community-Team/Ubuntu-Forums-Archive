---
title: "Has MultiSync development ceased?"
date: 2005-06-17
forum: General Help
---

### Post by john_walsh54 on 2005-06-17
MultiSync 0.8.2 was released on April 11 2004 and looking at the CVS version 0.9x has not been developed in 14 months 
I would like to use Multisync to synchronise my data between Evolution and my Nokia 9210.  Evolution uses the Evolution plugin, while my Nokia uses the SyncML plugin. Unfortunately, there is a bug (more like a showstopper to me) in the SyncML plugin for MultiSync 0.8.2 which duplicates the entries in Evolution while Nokia entries are correct after synchronisation
There is talk that this will be fixed in Multisync 0.9x but as I mentioned earlier there doesn't seem to be any development at  [http://cvs.sourceforge.net/viewcvs.py/multisync/multisync-0.90/ ](http://cvs.sourceforge.net/viewcvs.py/multisync/multisync-0.90/ ) 

If development has ceased can you recommend another application that will sync evolution with my Nokia 9210, which uses the SyncML protocol?

---

### Post by emmet on 2005-06-29
The developer forum appears to be active...

[http://sourceforge.net/mailarchive/forum.php?forum=multisync-devel](http://sourceforge.net/mailarchive/forum.php?forum=multisync-devel)

So it's not all dead (and it does work!).

Have you scanned the multisync forums? There is also a support forum as well. Sometimes you find that someone posts a patch in the forum itself.

Emmet

---

### Post by john_walsh54 on 2005-06-29
I checked the mailing list. 
At first glace it seems multisync development has ceased because there is no development activity at [multisync](http://www.multisync.org/). However, the actual development of multisync is taking place at [opensync](http://www.opensync.org/). The multisync developers decided to separate the GUI from the core application, rewrite the core application and call it the "opensync framework". The multisync 0.9x release will just be a GUI frontend to the "opensync framework". 
At the time of writing, all the multisync plugins, except the SyncML plugin (symbian based devices) had been converted to the "opensync framework". Once testing is completed, Multisync 0.9x will be released at [multisync](http://www.multisync.org/).

---

### Post by emmet on 2005-06-30
That's good news then.

I've never really got the Multisync to work correctly, but that's probably because I've never had the chance to really sit down and get stuck into the configuration.

One day (when I get down the "to do" list).

Emmet

---

