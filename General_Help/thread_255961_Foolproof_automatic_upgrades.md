---
title: "Foolproof automatic upgrades?"
date: 2006-09-12
forum: General Help
---

### Post by The Keeper on 2006-09-12
I need advise on this matter. :)

I have this PC on which I should install Ubuntu on. The PC will be used by users not in the sudoers group, so they cannot run any admin tasks. To make sure that the system is kept up-to-date at all times, I was thinking of making following script and make it run daily.
> 
aptitude update && aptitude dist-upgrade --fix-broken -y && aptitude autoclean --purge-unused -y

Should do the job decently I think. 

However, how foolproof is this method? What are the chances that someday the system gets hosed? What if an user shuts down the PC when the script was still running and installing upgrades?

---

