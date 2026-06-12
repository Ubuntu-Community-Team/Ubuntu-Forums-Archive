---
title: "polkit segfaul"
date: 2008-07-10
forum: General Help
---

### Post by epeeist01 on 2008-07-10
Great.  I can't fix my thread name typo.  Doh.  Anyway.

I can start polkit from system->administration->authorizations and I can change every entry except for "storage->mount file systems from internal drives".  If I click that entry the window closes.  If I instead do:

>sudo polkit-gnome-authorization

I get:
[WARN  9359] kit-hash.c:206:kit_hash_insert(): key != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN  9359] kit-hash.c:294:kit_hash_lookup(): key != NULL
 Not built with -rdynamic so unable to print a backtrace

 (repeated times 7)



But the window does open.  But when I click anything I get:

[WARN  9371] polkit-session.c:285:polkit_session_get_ck_objref(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN  9371] polkit-session.c:321:polkit_session_get_ck_is_local(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN  9371] polkit-session.c:303:polkit_session_get_ck_is_active(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN  9371] kit-hash.c:294:kit_hash_lookup(): key != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN  9371] kit-hash.c:206:kit_hash_insert(): key != NULL
 Not built with -rdynamic so unable to print a backtrace

And if I click on the "storage->mount file systems from internal drives" I get: 

Segmentation fault

in addition to the same lines above that I got for clicking anything.


System background is that everything was working after I upgraded to Hardy but I have some HDDs that I only like to mount if I request it and I always used "authorize for one session" but one time I accidentally clicked to make it always authorized, so I was poking around in Authorizations to try and get it back how it was.  I can't remember the last thing I poked at in authorizations before this started.  But if I change any other settings in Authorizations they work fine and they update and save properly.  It is just that one option that seg faults.  Any help?  Is there a way I can just delete the file where this data is saved and recreate it?

---

### Post by epeeist01 on 2008-07-11
bump.

---

