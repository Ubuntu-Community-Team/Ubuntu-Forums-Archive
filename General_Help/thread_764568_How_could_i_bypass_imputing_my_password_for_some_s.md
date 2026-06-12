---
title: "How could i bypass imputing my password for some stuff without being root?"
date: 2008-04-24
forum: General Help
---

### Post by madjr on 2008-04-24
is there a way i could bypas imputing my password for some tasks without having to be root?

stuff like launching synaptic, etc. without typing in my pass all the time (but of course letting me install the stuff).

am the only one using this computer.

Thanks :)

btw, am using gutsy, so is it possible with policykit in hardy or following some guide?

---

### Post by p_quarles on 2008-04-24
Moved to General Help. 

Yes, it's possible, but it's not really recommended. Basically, you would need to edit the /etc/sudoers file to allow you to run some applications without authenticating. 

More information here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by madjr on 2008-04-24
> **p_quarles said:**
> Moved to General Help. 

Yes, it's possible, but it's not really recommended. Basically, you would need to edit the /etc/sudoers file to allow you to run some applications without authenticating. 

More information here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

thanks !

umm how i thank people now o0

---

