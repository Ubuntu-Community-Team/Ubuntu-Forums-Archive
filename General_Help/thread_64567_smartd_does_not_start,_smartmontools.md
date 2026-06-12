---
title: "smartd does not start, smartmontools"
date: 2005-09-11
forum: General Help
---

### Post by gny on 2005-09-11
Hello,

I have installed smartmontools. A great tool for monitoring harddrives.
My problem is that smartd does not start when i issue 

/etc/init.d/smartmontools start.

if I do 

ps aux | grep smartd

I get nothing, the service is not runing. But if i start it by typing smartd at the promt, everything works.

Any ideas?  :-?

---

### Post by gny on 2005-09-12
Found it.
In 
/etc/default/smartmontools

# uncomment to start smartd on system startup
start_smartd=yes

---

