---
title: "Version 20.04 - Intermittently Non-Responsive"
date: 2021-04-02
forum: General Help
---

### Post by fathamir on 2021-04-02
Howdy Folks,

I have been running a home server type system for about a year - it has various odd-jobs but mostly serves as a NAS.  While I have enjoyed the recent change to Ubuntu, I have one critical issue I can't resolve myself.  Every few days, at least once a week, the system completely stops responding.  It lives in the garage in a cabinet next to one of my routers.  My connections to it are always SSH or via Remote Desktop.  Every few days, I notice that my network drive, plex, and other services go offline, and I am unable to connect via SSH.


I've read through several log files, but I don't find anything that appears to be a critical error right before it goes unresponsive.  It is still clearly powered on, often even running system fans at max.


Where do I start to troubleshoot this issue?  What would cause the system to go unresponsive (at least on my network) every few days?

---

### Post by daniewicz on 2021-04-02
>  often even running system fans at max 

Maybe a cooling problem? Open the cabinet for more airflow?

---

### Post by fathamir on 2021-04-02
The fans running up are an occasional symptom, but temperatures are always acceptable.  Its cold in the garage still this time of year and this began only when I switched to ubuntu a few months ago.  It acts like the system bus is waiting for a task that will never complete.

After a restart, its always fine - for a few more days.

---

### Post by ActionParsnip on 2021-04-03
Test your RAM health as a good first step

---

### Post by fathamir on 2021-04-03
> **ActionParsnip said:**
> Test your RAM health as a good first step



Wow!  Thanks for bringing me back to the basics.  I ran memtester and received several error messages.


When installing ubuntu I had also replaced the hard drives.  It is likely that I bumped a stick loose.  After pulling them and re-seating, so far I have not seen the same error tests from memtester.  I'll run a more conclusive mem test if I continue to have the random loss of response.



While only time can tell, I believe this is likely solved.

---

### Post by daniewicz on 2021-04-04
Glad you got things sorted out :cool:

---

