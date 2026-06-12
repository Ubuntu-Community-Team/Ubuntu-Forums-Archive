---
title: "Virtual box problem after upgrade"
date: 2007-07-03
forum: General Help
---

### Post by mpooley on 2007-07-03
Hi all
I am trying to open a virtual machine and i am getting the error 
"VM cannot start because the DVD image '/opt/VirtualBox-1.3.8/additions/VBoxGuestAdditions.iso' is not accessible."

I have checked and the folder has changed to /opt/VirtualBox-4/additions/VBoxGuestAdditions.iso'

this has happened after an update - any ideas how to solve this please?

Mike

---

### Post by DagMan on 2007-07-03
In the GUI for virtualbox, on the right hand side in the details tab click on cd/dvd-rom and select the new location of the iso, or if you aren't going to use it then select your cd-drive or another image... or just disable it.

---

### Post by mpooley on 2007-07-03
Thanks!

That worked fine

Mike

---

