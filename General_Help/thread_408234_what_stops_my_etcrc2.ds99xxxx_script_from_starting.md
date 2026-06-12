---
title: "what stops my /etc/rc2.d/s99xxxx script from starting?"
date: 2007-04-13
forum: General Help
---

### Post by surxain on 2007-04-13
There is a mongrel_cluster script inside /etc/init.d/ dir.
I can start the script by running  /etc/init.d/mongrel_cluster start

then I created a link to /etc/rc2.d/S99mongrel_cluster for the script. but the mongrel_cluster doesn't start when the system boots up. 

what may be wrong?

---

### Post by mac.ryan on 2007-04-13
> **surxain said:**
> ...then I created a link **to** /etc/rc2.d/S99mongrel_cluster for the script...

I am far from being an expert, but my understanding is that you should create a link **from** the rc2.d directory, as that is the one in which the boot for runlevel2 will look into.

---

### Post by surxain on 2007-04-13
> **mac.ryan said:**
> you should create a link **from** the rc2.d directory

yes, now the link is inside the rc2.d directory, pointing to the /etc/init.d/mongrel_cluster script.

---

### Post by mac.ryan on 2007-04-13
I don't know if this will change in any way the behaviour of your system.... but have you tried, instead of doing a link, to do a real script, just inserting the commandline that proved to work when manually launched?

---

