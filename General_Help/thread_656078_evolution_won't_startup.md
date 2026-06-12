---
title: "evolution won't startup"
date: 2008-01-02
forum: General Help
---

### Post by chudder on 2008-01-02
I looked on one other thread and it was a different error at least that is found in the terminal.  I have tried to start evolution a few times the past week and it hasn't started up, it tries to start up but then dies.  In the processes it shows the "evolution-exchange-storage" process still running.  In the command line this is the output:

```
chud@lappy20X6:~$ evolution
CalDAV Eplugin starting up ...

(evolution-2.10:9792): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution-2.10:9792): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:9792): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution-2.10:9792): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:9792): e-data-server-CRITICAL **: e_source_group_peek_base_uri: assertion `E_IS_SOURCE_GROUP (group)' failed
Segmentation fault (core dumped)

```

I have tried to reinstall evolution and get more of the evolution files from synaptic but the same result.  I have also restarted the computer and this doesn't fix it.  

Any help would be greatly appreciated.  

Thanx 

Chudder

---

### Post by bapoumba on 2008-01-02
[http://ubuntuforums.org/showthread.php?t=539168](http://ubuntuforums.org/showthread.php?t=539168)
There may be a fix in this thread.

---

### Post by chudder on 2008-01-02
Thank you Bapoumba!  That solved it.  

Thanx

Chudder

---

### Post by bapoumba on 2008-01-04
A little late, you're welcome!

---

