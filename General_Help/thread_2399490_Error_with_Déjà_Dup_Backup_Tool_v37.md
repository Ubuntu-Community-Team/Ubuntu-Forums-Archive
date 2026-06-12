---
title: "Error with Déjà Dup Backup Tool v37"
date: 2018-08-26
forum: General Help
---

### Post by al-2 on 2018-08-26
Error message is:  Error creating directory /media/al/380E64650E641E5E: Permission denied

---

### Post by SagaciousKJB on 2018-08-26
> **al-2 said:**
> Error message is:  Error creating directory /media/al/380E64650E641E5E: Permission denied

There's not a lot of information to go off of here, but looks like a permissions problem.  Strong guess is that whatever /media/al/380E64650E641E5E is pointing to was mounted without 'rw' mount options, or into a directory which you don't have write permissions in.  If it were an issue with the media being mounted read-only, the error would probably mention that specifically.

Are you running this command as root?

---

