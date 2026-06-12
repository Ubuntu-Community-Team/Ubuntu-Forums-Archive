---
title: "Evolution Broken after trying Gutsy !!"
date: 2007-09-10
forum: General Help
---

### Post by mat_london on 2007-09-10
Hi,

I tried out Gutsy on a spare partition over the weekend using my existing /home partition.
Now when I boot back into my stable Feisty partition evolution no longer starts. From the CL I'm getting this :

:~$ evolution
CalDAV Eplugin starting up ...

(evolution-2.10:9534): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `EEvent'

(evolution-2.10:9534): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:9534): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution-2.10:9534): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(evolution-2.10:9534): e-data-server-CRITICAL **: e_source_group_peek_base_uri: assertion `E_IS_SOURCE_GROUP (group)' failed
Segmentation fault (core dumped)

Help !! 

I've got a weeks work ahead with no diary or addressbook ?

Mat

---

### Post by TabletUbuntu on 2007-09-10
I have the same problem.  Have gutsy on another partition for over a month, and suddenly today I get this error.

---

### Post by TabletUbuntu on 2007-09-10
As a follow-up, I narrowed the problem down.  I logged out, logged into a terminal, and restored the directory ~/.gconf/apps/evolution from a recent backup.  All is well.

You might try to delete this directory if you have no backup, but you'll be prompted to set up your evolution all over again.

Hope this helps!

---

### Post by mat_london on 2007-09-10
Thanks

Me too, 

Looks like the newer version of Evo in Gutsy adds something to the gconf config that the older Evo can't handle

I copied then selectively deleted various folders in ~/.gconf/apps/evolution until Evo ran again.

Mat

---

### Post by krizz on 2007-09-17
Got the same problem, when tried to Import backuped settings from a Gutsy Evolution version in the evolution version of Feisty.
> **TabletUbuntu said:**
>  logged out, logged into a terminal, and restored the directory ~/.gconf/apps/evolution from a recent backup.  
...
Hope this helps!
Really, helped. I deleted the folder and used the Import/Export plugin to Import settings taken from a Feisty Evolution version.

Thanks a lot.

---

