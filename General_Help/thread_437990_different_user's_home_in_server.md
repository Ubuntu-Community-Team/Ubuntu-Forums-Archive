---
title: "different user's /home in server"
date: 2007-05-09
forum: General Help
---

### Post by jmvidalvia on 2007-05-09
I am setting a home server: first step before trying it at work.
Everything is running: can access by NFS, ssh, etc.
And my question is: ¿can I copy the /home directories of all of my users in the server, export them by NFS so every user can use different machines using his own configuration, and having all data files safely stored in the server?
Is that possible?
Any special configuration futher to standard nsf?
Thank you very much!

---

### Post by IgnorantGuru on 2007-05-09
Never tried it but I don't see why that wouldn't work.  Might be a bit slow compared to having a /home on each system.  Not sure what your goal is, but might be faster to just share data folders.

---

### Post by ikonia on 2007-05-09
totally possible.

you need NFS and automount, this is old school unix. you may want to consider a centralised authentication system such as ldap too if you have enough clients.


One reason this used to work well on unix systems was because they all used to use the same desktop and version of the desktop, if you have multiple client machine with varying versions of linux and desktop this could be a problem as they are not all configured the same, eg: the .gnome dir on an ubuntu 6.06 box being mounted onto a suse box may cause problems.

---

### Post by jmvidalvia on 2007-05-10
Thanks for your answers: meanwhile I read something about NIS, but doubt about which system (nis vs ldap) is better..
Thanks!

---

### Post by ikonia on 2007-05-10
Nis is legacy, and quite insecure and was replaced by NIS+ which is much better, but also a real headache to run and manage, more so if your not used to the more older techniques. Ldap is pretty much the modern day version so I'd advise that to maintain compatability with applications in the future.

---

