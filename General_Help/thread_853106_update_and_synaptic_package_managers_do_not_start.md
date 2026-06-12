---
title: "update and synaptic package managers do not start"
date: 2008-07-08
forum: General Help
---

### Post by rbaggio on 2008-07-08
Hi,
I am a new ubuntu user.  Recently I have not been able to install updates.  The update manager notifies about the new updates and descriptions.  However, when I click on install updates, and typed in my password, the application does not start.  I also checked that the synaptic package manager also does not start. 

I am using the latest ubuntu hardy version on an IBM T43.  

I will appreciate if anyone can help me detect and fix this problem.  

Thanks,

Hakan

---

### Post by bigken on 2008-07-08
can you see if there any broken packages in synaptic if so try and remove them

---

### Post by rbaggio on 2008-07-08
Hi, thanks for the response.  The synaptic package manager does not start either.  When I try to start in from the Systems > Administration a box in the bottom panel appears (after typing in the admin password) saying "Starting administrative application", and this box disappears in 4-5 seconds. 
Hence I cannot see if there is a broken package or not.
Is there any other way to figure out how to get a list of broken packages?

---

### Post by rbaggio on 2008-07-08
I solved the problem by removing a repository source from /etc/apt/sources.list and changing my password from the "users and groups" window.  Now everything is back to normal.  

I think the problem was caused by an old package source rather than the password.

---

### Post by bigken on 2008-07-08
pleased you got it fixed

---

