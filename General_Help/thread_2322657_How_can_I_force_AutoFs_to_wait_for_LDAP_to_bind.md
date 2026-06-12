---
title: "How can I force AutoFs to wait for LDAP to bind?"
date: 2016-04-29
forum: General Help
---

### Post by peek-nimbios on 2016-04-29
Hi,

I've discovered what I think is a race condition whereby, during boot, sometimes AutoFS starts before LDAP has finished binding.  When this happens, user home areas are not mounted and nobody can log in until AutoFS has been restarted.  This may be a slightly more complicated matter than simply waiting for nslcd to run, as starting nslcd may still result in a delay before user information can be resolved by the system.

---

### Post by peek-nimbios on 2016-05-02
I wrote a test script that is run by systemd upon startup.  The script waits for AutoFS to start and then tries to do an 'ls -ald' on an automounted folder.  Apparently my problem is intermittent.  Sometimes AutoFS, after an initial failure to mount the directory, will recover and mount it 60 seconds later.  At other times, AutoFS never recovers, and nothing from LDAP is mountable until AutoFS is restarted.  This may indicate a bug in AutoFS itself?

---

