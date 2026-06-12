---
title: "Scheduled backups no work, need encryption password"
date: 2012-12-13
forum: General Help
---

### Post by Rocket J Squirrel on 2012-12-13
**Using Lubuntu's default Backup program** (front end for deja-dup),scheduled backups do not run but manual ("backup now") ones do. 

The scheduled backups terminate with a notification that the backup destination is unavailable. 

I think this is an inaccurate error message because when I run the program manually, it asks for the encryption password, then goes ahead and does the job. [Edit]: the scheduled backup does not request the password.

I arbitrarily decided to encrypt my backups when I last ran the program manually (it offered the choice, I figured "why not?"). 

Now I know why not: Backup does not seem to have any place to store the encryption password so when it tries to do its job unattended, it cannot. 

So. I guess I can delete the schedule and set up a new one without an encryption password -- unless someone knows how to enter it into Backup? Or maybe there's a better front-end for Deja-Dup that handles encryption passwords.

---

### Post by Rocket J Squirrel on 2012-12-20
Oh wait -- there's a "Save Password" box right in plain view. Never mind.

---

